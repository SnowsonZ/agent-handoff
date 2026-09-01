# 发布状态

更新时间：2026-09-01

| 渠道 | 状态 | 地址 | 说明 |
| --- | --- | --- | --- |
| GitHub | 已发布 | <https://github.com/SnowsonZ/agent-handoff> | `main` 与 `v0.1.4` 已推送 |
| skills.sh | 已收录 | <https://www.skills.sh/snowsonz/agent-handoff/handoff-installer> | 已用公开仓库完成实际安装验证 |
| ClawHub | `0.1.3` 已发布，安全审计为 Review | <https://clawhub.ai/snowsonz/skills/agent-handoff/security-audit> | 0.1.3 包含全部 12 个文件，从 ClawHub 精确安装可成功完成且无残留 transaction，包不完整问题已修复。完整异步审计于 2026-09-01 05:28 UTC 回写后 Outcome 变为 `Review`：VirusTotal clean；SkillSpector 报 8 项，主审计已降级其中 7 项（包括 Lp3），但接受 SSD-1 为实质问题——运行时 AGENTS 块不应声称 trailer 字段可豁免更高优先级输出规则 |
| OpenAI Plugins Directory | 延期 | <https://platform.openai.com/plugins> | 用户决定暂不发布；未创建草稿、未上传 bundle、未提交审核 |

## 当前发布标识

- 公开 Plugin、GitHub 仓库和市场 slug：`agent-handoff`
- 安装 Skill：`handoff-installer`
- 安装到目标仓库后的运行时 Skill：`handoff`
- 公开版本：GitHub `0.1.4`；ClawHub `0.1.3`
- 许可证：MIT-0
