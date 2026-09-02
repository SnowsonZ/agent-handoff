# 发布状态

更新时间：2026-09-02

发版步骤见 [CLAWHUB.md](CLAWHUB.md)。正常路径是往公开仓库推 `vX.Y.Z` tag，由 workflow 自动发布 ClawHub；**不要在推 tag 之后再手工执行 `clawhub skill publish`**，那会对同一版本形成第二次发布尝试。

| 渠道 | 状态 | 地址 | 说明 |
| --- | --- | --- | --- |
| GitHub | 已发布 | <https://github.com/SnowsonZ/agent-handoff-skill> | `main` 与 `v0.1.9` 已推送；tag 触发的 ClawHub 发布 workflow 已在 `v0.1.7`、`v0.1.8`、`v0.1.9` 连续三次全绿。2026-09-02 仓库由 `agent-handoff` 改名为 `agent-handoff-skill`（`gh repo rename`，旧名自动重定向） |
| skills.sh | 已收录 | <https://www.skills.sh/snowsonz/agent-handoff-skill/handoff-installer> | 已用公开仓库完成实际安装验证；地址随 2026-09-02 GitHub 仓库改名一并变化 |
| ClawHub | `0.1.9` 已发布，**完整异步审计终态为 `benign`（页面 Pass）** | <https://clawhub.ai/snowsonz/skills/agent-handoff-skill/security-audit> | 12 个上传路径经 workflow 逐路径核对齐全，5 个步骤全绿（含转公开确认，未走 warning 分支）。终态判据已满足：VirusTotal 回写（64 引擎，0 恶意 0 可疑），SkillSpector 与主审计同刻且晚于 VirusTotal，主审计已用支持扫描重新合成，`benign`/confidence high，维度 3 ok / 2 note 无 concern。主审计 `persistence_privilege` 明确记录「recovery path may read session history only after explicit user consent」，即 0.1.8 的同意门整改已被认可。需注意：SkillSpector 原始报告为 5 项全 HIGH（较 0.1.8 的 4 项 2 HIGH 更重），5 条均指向运行时协议作用域宽（元数据与正文范围不一致、指导日常仓库工作、改写任务棒、归档提交、建棒与抢救流程），主审计历来判为已披露且与用途相符。2026-09-02 slug 由 `agent-handoff` 改名为 `agent-handoff-skill`，8 个历史版本与审计记录原样保留，旧 slug 重定向 |
| OpenAI Plugins Directory | 延期 | <https://platform.openai.com/plugins> | 用户决定暂不发布；未创建草稿、未上传 bundle、未提交审核 |

## 当前发布标识

- 公开 Plugin、GitHub 仓库和市场 slug：`agent-handoff-skill`
- 安装 Skill：`handoff-installer`
- 安装到目标仓库后的运行时 Skill：`handoff`
- 公开版本：`0.1.9`
- 许可证：MIT-0
