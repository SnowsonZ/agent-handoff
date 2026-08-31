# v0.1.1 首次公开发布

Agent Handoff 将可审计的多 agent 任务接力协议安装到 git 仓库中。首次发布包含：

- 显式触发的 `handoff-installer` Skill
- `status`、`install`、`update`、`adopt-existing` 四种模式
- 安装锁、本地修改保护和中断恢复
- 仓库运行时 handoff Skill、任务棒模板和只读账本工具
- 四客户端触发与干净安装结果接棒验证

该版本不包含 MCP server、远程服务、认证、遥测或托管数据。
