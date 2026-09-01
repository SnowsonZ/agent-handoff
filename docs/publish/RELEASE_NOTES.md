# v0.1.5

Skill 内容与 v0.1.4 完全相同。本版本用于验证公开仓库新增的 tag 触发发布流程：推送 `v0.1.5`
后由 GitHub Actions 自动完成版本一致性校验、dry-run 文件数检查、发布和公开版本确认。

# v0.1.4

移除运行时 AGENTS 策略中声称 trailer 字段可豁免适用规则的文案；准确归属无法合规写入时，改为在
提交前停止并向用户说明。安装器对写模式增加当前会话同意边界：执行前披露目标仓库、文件写入、
符号链接、持久运行时策略与语言，并要求用户明确确认模式和目标；只读 `status` 不受影响。

# v0.1.3

修复 ClawHub 发布产物缺失隐藏目录载荷的问题：把 bundle 内部的运行时 Skill 与任务棒模板移到
可发布路径，同时保持目标仓库内的 `.agents/...` 安装位置不变。写模式现在会在创建 transaction 或
目录前验证全部载荷，包不完整时直接失败且不修改目标仓库。`SKILL.md` 还通过
`metadata.openclaw.requires` 声明了 `sh`、`git` 和 SHA-256 工具依赖。

# v0.1.2

在 `handoff-installer` SKILL.md 里补充了执行能力披露：明确说明四种模式都通过本地 shell 执行
`scripts/install.sh`，`status` 只读，其余三种模式在 `target` 仓库内写哪些具体文件，且不发起任何
网络请求。用于回应 ClawHub 安全审计 Lp3（MCP 最小权限，Medium）发现。

# v0.1.1 首次公开发布

Agent Handoff 将可审计的多 agent 任务接力协议安装到 git 仓库中。首次发布包含：

- 显式触发的 `handoff-installer` Skill
- `status`、`install`、`update`、`adopt-existing` 四种模式
- 安装锁、本地修改保护和中断恢复
- 仓库运行时 handoff Skill、任务棒模板和只读账本工具
- 四客户端触发与干净安装结果接棒验证

该版本不包含 MCP server、远程服务、认证、遥测或托管数据。
