# 发布状态

更新时间：2026-09-02

发版步骤见 [CLAWHUB.md](CLAWHUB.md)。正常路径是往公开仓库推 `vX.Y.Z` tag，由 workflow 自动发布 ClawHub；**不要在推 tag 之后再手工执行 `clawhub skill publish`**，那会对同一版本形成第二次发布尝试。

| 渠道 | 状态 | 地址 | 说明 |
| --- | --- | --- | --- |
| GitHub | 已发布 | <https://github.com/SnowsonZ/agent-handoff-skill> | `main` 与 `v0.1.8` 已推送；tag 触发的 ClawHub 发布 workflow 已在 `v0.1.7`、`v0.1.8` 连续两次全绿。2026-09-02 仓库由 `agent-handoff` 改名为 `agent-handoff-skill`（`gh repo rename`，旧名自动重定向） |
| skills.sh | 已收录 | <https://www.skills.sh/snowsonz/agent-handoff-skill/handoff-installer> | 已用公开仓库完成实际安装验证；地址随 2026-09-02 GitHub 仓库改名一并变化 |
| ClawHub | `0.1.8` 已发布，当前主审计 `benign`（**VirusTotal 未回写，终态待定**） | <https://clawhub.ai/snowsonz/skills/agent-handoff-skill/security-audit> | 12 个上传路径经 workflow 逐路径核对齐全。0.1.8 针对 0.1.7 的意见整改后，主审计 summary 明确写为「sensitive future behavior called out and gated by user confirmation」，0.1.7 的四条 concern 全部消失（3 ok / 2 note），且无任何维度再提会话历史抢救路径；SkillSpector 4 项（2 HIGH 2 MEDIUM），HIGH 两条为长期存在的运行时作用域宽度问题，主审计历来判为已披露且与用途相符。终态须待 VirusTotal 回写、主审计在其之后重新合成才可判定——0.1.3 即曾先显示 Pass、VT 回写后翻为 Review。2026-09-02 slug 由 `agent-handoff` 改名为 `agent-handoff-skill`（`clawhub skill rename`，8 个历史版本与审计记录原样保留，旧 slug 重定向） |
| OpenAI Plugins Directory | 延期 | <https://platform.openai.com/plugins> | 用户决定暂不发布；未创建草稿、未上传 bundle、未提交审核 |

## 当前发布标识

- 公开 Plugin、GitHub 仓库和市场 slug：`agent-handoff-skill`
- 安装 Skill：`handoff-installer`
- 安装到目标仓库后的运行时 Skill：`handoff`
- 公开版本：`0.1.8`
- 许可证：MIT-0
