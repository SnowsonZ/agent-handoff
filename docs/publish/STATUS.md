# 发布状态

更新时间：2026-09-02

发版步骤见 [CLAWHUB.md](CLAWHUB.md)。正常路径是往公开仓库推 `vX.Y.Z` tag，由 workflow 自动发布 ClawHub；**不要在推 tag 之后再手工执行 `clawhub skill publish`**，那会对同一版本形成第二次发布尝试。

| 渠道 | 状态 | 地址 | 说明 |
| --- | --- | --- | --- |
| GitHub | 已发布 | <https://github.com/SnowsonZ/agent-handoff> | `main` 与 `v0.1.8` 已推送；tag 触发的 ClawHub 发布 workflow 已在 `v0.1.7`、`v0.1.8` 连续两次全绿 |
| skills.sh | 已收录 | <https://www.skills.sh/snowsonz/agent-handoff/handoff-installer> | 已用公开仓库完成实际安装验证 |
| ClawHub | `0.1.8` 已发布，**完整异步审计待回写** | <https://clawhub.ai/snowsonz/skills/agent-handoff/security-audit> | 上传的 12 个路径经 workflow 逐路径核对齐全。0.1.8 针对 0.1.7 审计意见做了实质整改：抢救路径需用户同意后才读会话历史、整理结果需过目后才写入。终态需等 VirusTotal 与 SkillSpector 回写、且主审计在二者之后重新合成才可判定，此前显示的任何结论均为暂定。参考：0.1.7 主审计为 `suspicious`（页面 Review），0.1.6 同内容为 `benign`，同一产物两种结论 |
| OpenAI Plugins Directory | 延期 | <https://platform.openai.com/plugins> | 用户决定暂不发布；未创建草稿、未上传 bundle、未提交审核 |

## 当前发布标识

- 公开 Plugin、GitHub 仓库和市场 slug：`agent-handoff`
- 安装 Skill：`handoff-installer`
- 安装到目标仓库后的运行时 Skill：`handoff`
- 公开版本：`0.1.8`
- 许可证：MIT-0
