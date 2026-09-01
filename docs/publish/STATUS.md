# 发布状态

更新时间：2026-09-02

发版步骤见 [CLAWHUB.md](CLAWHUB.md)。正常路径是往公开仓库推 `vX.Y.Z` tag，由 workflow 自动发布 ClawHub；**不要在推 tag 之后再手工执行 `clawhub skill publish`**，那会对同一版本形成第二次发布尝试。

| 渠道 | 状态 | 地址 | 说明 |
| --- | --- | --- | --- |
| GitHub | 已发布 | <https://github.com/SnowsonZ/agent-handoff> | `main` 与 `v0.1.6` 已推送；`.github/workflows/publish-clawhub.yml` 已部署，推 `vX.Y.Z` tag 自动发布 |
| skills.sh | 已收录 | <https://www.skills.sh/snowsonz/agent-handoff/handoff-installer> | 已用公开仓库完成实际安装验证 |
| ClawHub | `0.1.6` 已发布，完整安全审计终态为 `benign` | <https://clawhub.ai/snowsonz/skills/agent-handoff/security-audit> | 上传的 12 个路径在已发布清单里一个不少（版本 API 另含 ClawHub 生成的 `skill-card.md`，共 13）。VirusTotal 63 引擎 0 恶意 0 可疑；SkillSpector 5 项能力告警；主审计 `checkedAt` 与 SkillSpector 同刻且晚于 VirusTotal，已用支持扫描重新合成，confidence high。0.1.5 受理后转公开耗时超过 50 分钟，0.1.6 超过 15 分钟——转公开是 ClawHub 侧异步过程，workflow 不等待 |
| OpenAI Plugins Directory | 延期 | <https://platform.openai.com/plugins> | 用户决定暂不发布；未创建草稿、未上传 bundle、未提交审核 |

## 当前发布标识

- 公开 Plugin、GitHub 仓库和市场 slug：`agent-handoff`
- 安装 Skill：`handoff-installer`
- 安装到目标仓库后的运行时 Skill：`handoff`
- 公开版本：`0.1.6`
- 许可证：MIT-0
