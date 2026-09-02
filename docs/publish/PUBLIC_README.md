# Agent Handoff

Agent Handoff 把可审计的多 agent 任务接力协议安装到 git 仓库中。任务目标、已完成工作、下一步、决策和禁区保存在版本控制内的任务棒中，不依赖任何单一客户端的会话历史。

## 包含内容

- `handoff-installer`：显式安装、检查、更新或采用仓库级 handoff 协议
- 四模式安装状态机：`status`、`install`、`update`、`adopt-existing`
- 安装锁、本地修改保护和中断恢复
- 仓库运行时 handoff Skill、任务棒模板和只读 git 账本工具

## 安装

从支持 Agent Skills 的客户端安装：

```bash
npx skills add SnowsonZ/agent-handoff-skill --skill handoff-installer
```

安装 Skill 后显式调用：

```text
Use the $handoff-installer skill to install handoff in this git repository.
```

普通 `Continue.`、继续编码或交棒请求不会触发安装器。

## 市场页面

- [skills.sh](https://www.skills.sh/snowsonz/agent-handoff-skill/handoff-installer)
- [ClawHub](https://clawhub.ai/snowsonz/skills/agent-handoff-skill)
- [GitHub](https://github.com/SnowsonZ/agent-handoff-skill)

## 安全边界

- 只接受具体 git 仓库作为目标
- 当前版本重复安装为 no-op
- 旧版更新和无锁旧版采用必须显式请求
- 受管文件有本地修改时拒绝覆盖
- 不包含遥测、远程服务、认证或网络上报

安装前请审查 Skill 和脚本，并为重要仓库保留备份。

## 文档

- [隐私政策](docs/publish/PRIVACY.md)
- [服务条款](docs/publish/TERMS.md)
- [支持](docs/publish/SUPPORT.md)
- [审核测试用例](docs/publish/TEST_CASES.json)
- [发布状态](docs/publish/STATUS.md)

## 许可证

Skill 和公开发布包使用 MIT-0 许可证，详见 `LICENSE`。
