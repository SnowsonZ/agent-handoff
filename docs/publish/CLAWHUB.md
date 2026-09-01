# ClawHub 发布

**正常路径：推 tag，workflow 自动发布。** 公开仓库的
`.github/workflows/publish-clawhub.yml` 监听 `v*.*.*` tag，自动完成版本校验、dry-run、publish
和版本确认。不要再手工敲 publish。

## 发布一个新版本

```sh
V=0.1.5
```

1. 改版本号：`.agents/skills/handoff-installer/VERSION` 与
   `plugins/agent-handoff/.codex-plugin/plugin.json` 的 `.version` 都改成 `$V`，
   然后 `sh tools/package-plugin.sh` 同步生成副本。
2. 本地检查：`sh tools/verify/test-publish-readiness.sh`。它会顺带跑
   `package-plugin.sh --check`，确认生成副本与真源同步、manifest 契约完整、发布材料齐全。
   （`check-all.sh` 只测四家 CLI 能否读到 AGENTS.md，不校验 bundle，不能当发版闸门。）
3. 取得用户授权后同步公开仓库并打 tag（tag message 会成为 changelog）：

```sh
tmp=$(mktemp -d)
git clone https://github.com/SnowsonZ/agent-handoff.git "$tmp/repo"
rsync -a --delete plugins/agent-handoff/skills/handoff-installer/ "$tmp/repo/skills/handoff-installer/"
cp plugins/agent-handoff/.codex-plugin/plugin.json "$tmp/repo/.codex-plugin/plugin.json"
cp plugins/agent-handoff/assets/logo.svg "$tmp/repo/assets/logo.svg"
mkdir -p "$tmp/repo/.github/workflows"
cp plugins/agent-handoff/.github/workflows/publish-clawhub.yml "$tmp/repo/.github/workflows/"
cp docs/publish/PUBLIC_README.md "$tmp/repo/README.md"
cp docs/publish/*.md docs/publish/TEST_CASES.json "$tmp/repo/docs/publish/"
git -C "$tmp/repo" status --short          # 只应包含上述公开路径
git -C "$tmp/repo" add -A
git -C "$tmp/repo" commit -m "<英文单行总结>"
git -C "$tmp/repo" tag -a "v$V" -m "<一句话变更说明>"
git -C "$tmp/repo" push origin main "v$V"
```

> 首次把 `.github/workflows/` 推上去时，push 用的凭据需要 `workflow` 权限，否则 GitHub 会拒收。

4. 去 Actions 看结果：<https://github.com/SnowsonZ/agent-handoff/actions>

## workflow 说明了什么

绿色 = 该 tag 对应的版本已被 ClawHub 受理，且**如果**在等待窗口内转公开，则内容完整。它按顺序卡四道：

- tag、Skill `VERSION`、manifest `.version` 三者必须一致
- dry-run 必须 `status=would-publish` 且 `fileCount=12`（**这是上传数**；已发布版本 API 会多出
  ClawHub 生成的 `skill-card.md`，两个数字口径不同，别拿 12 去比对版本 API）——ClawHub 会**静默**丢掉隐藏路径和
  符号链接，文件数是包被截断的唯一信号
- publish 只跑一次，失败不自动重试
- publish 后轮询版本 API 五分钟：转公开了就逐路径核对上传的 12 个文件一个不少（少了就红）；
  没转公开则打一条 warning 但不报红——**转公开是 ClawHub 侧的异步过程，实测 0.1.6 用了 15 分钟以上、
  0.1.5 超过 50 分钟**，让 CI 干等只会每次发版都变红

**绿色不等于安全审计通过。** VirusTotal 与 SkillSpector 要一小时左右才回写，回写后主审计会重算，
结论可能翻转。终态以 [STATUS.md](STATUS.md) 记录为准。

## 事后确认版本真的公开了

```sh
curl -sS -L "https://clawhub.ai/api/v1/skills/agent-handoff/versions/$V" \
  | jq -r '.version.files[].path' | sort > /tmp/published.txt
(cd plugins/agent-handoff/skills/handoff-installer && find . -type f | sed 's|^\./||') \
  | sort > /tmp/uploaded.txt
comm -23 /tmp/uploaded.txt /tmp/published.txt   # 输出为空才算内容完整
```

比数量更可靠：ClawHub 会给已发布版本生成 `skill-card.md`，版本 API 的文件数恒比上传数多，
拿 12 去比对那个接口永远不成立。

## 出岔子

- **红色**：tag 已经在 GitHub 上，但发布未被证明完成。先看是哪一步红的，不要直接 rerun。
- **绿色但带 warning**：已受理、尚未转公开。过一阵用下面的命令自己确认，不要重发。
- **publish 成功但版本确认超时**：版本很可能已受理。查版本 API 和审计存档，**不要重发同一版本**。
- **secret 失效**：更新 `CLAWHUB_TOKEN` 后，只有确认该版本尚未被受理才能重跑。
- **修复已发布版本**：改不了，必须走新的 semver。

只有在 workflow 确实没有运行、也没有成功过的情况下，才手工发布：

```sh
npx --yes clawhub@latest skill publish ./plugins/agent-handoff/skills/handoff-installer \
  --slug agent-handoff --name 'Handoff Installer' --version "$V" \
  --changelog '<一句话变更说明>' --dry-run --json
```

确认 `status=would-publish`、`version=$V`、`fileCount=12` 之后，去掉 `--dry-run` 再跑一次。
返回 `pending-publication` 表示已受理，不要重发。
