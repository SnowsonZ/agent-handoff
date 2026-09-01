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
