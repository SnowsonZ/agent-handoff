# 发布状态

更新时间：2026-09-01

发版步骤见 [CLAWHUB.md](CLAWHUB.md)。正常路径是往公开仓库推 `vX.Y.Z` tag，由 workflow 自动发布 ClawHub；**不要在推 tag 之后再手工执行 `clawhub skill publish`**，那会对同一版本形成第二次发布尝试。

| 渠道 | 状态 | 地址 | 说明 |
| --- | --- | --- | --- |
| GitHub | 已发布 | <https://github.com/SnowsonZ/agent-handoff> | `main` 与 `v0.1.4` 已推送 |
| skills.sh | 已收录 | <https://www.skills.sh/snowsonz/agent-handoff/handoff-installer> | 已用公开仓库完成实际安装验证 |
| ClawHub | `0.1.4` 已发布，完整安全审计为 Pass | <https://clawhub.ai/snowsonz/skills/agent-handoff/security-audit> | 12 个文件齐全，从 ClawHub 精确安装可成功完成且无残留 transaction。完整异步审计于 2026-09-01 08:38 UTC 回写：VirusTotal 64/64 未检出，SkillSpector 原始报告列出 5 项；主审计在同一时间重新合成并把这些能力判定为已披露、目的相符，最终为 `clean/benign`，页面 Outcome 为 `Pass` |
| OpenAI Plugins Directory | 延期 | <https://platform.openai.com/plugins> | 用户决定暂不发布；未创建草稿、未上传 bundle、未提交审核 |

## 当前发布标识

- 公开 Plugin、GitHub 仓库和市场 slug：`agent-handoff`
- 安装 Skill：`handoff-installer`
- 安装到目标仓库后的运行时 Skill：`handoff`
- 公开版本：`0.1.4`
- 许可证：MIT-0
