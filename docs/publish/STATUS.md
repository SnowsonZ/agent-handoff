# 发布状态

更新时间：2026-09-01

| 渠道 | 状态 | 地址 | 说明 |
| --- | --- | --- | --- |
| GitHub | 已发布 | <https://github.com/SnowsonZ/agent-handoff> | `main` 与 `v0.1.4` 已推送 |
| skills.sh | 已收录 | <https://www.skills.sh/snowsonz/agent-handoff/handoff-installer> | 已用公开仓库完成实际安装验证 |
| ClawHub | `0.1.4` 已发布，完整异步审计待回写 | <https://clawhub.ai/snowsonz/skills/agent-handoff/security-audit> | 0.1.4 已移除 SSD-1 对应的规则豁免并增加写模式同意边界；12 个文件齐全，从 ClawHub 精确安装可成功完成且无残留 transaction。2026-09-01 08:30 UTC 初始主审计为 `clean/benign`，但 VirusTotal 与 SkillSpector 仍为空，因此当前结果只视为暂定，不记录 Pass |
| OpenAI Plugins Directory | 延期 | <https://platform.openai.com/plugins> | 用户决定暂不发布；未创建草稿、未上传 bundle、未提交审核 |

## 当前发布标识

- 公开 Plugin、GitHub 仓库和市场 slug：`agent-handoff`
- 安装 Skill：`handoff-installer`
- 安装到目标仓库后的运行时 Skill：`handoff`
- 公开版本：`0.1.4`
- 许可证：MIT-0
