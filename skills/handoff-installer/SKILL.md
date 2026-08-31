---
name: handoff-installer
description: Use when the user explicitly asks to install, update, adopt, or inspect the handoff protocol in a git repository. Do not use for starting, continuing, resuming, or handing off ordinary task work.
license: MIT-0
---

# Handoff 安装器

先检查当前用户消息，再使用工具。

- 没有明确要求安装、更新、采用旧版或检查状态：立即退出，不读仓库状态，不调用脚本，不修改文件。
- 明确要求检查：运行 `scripts/install.sh status [target]`。
- 明确要求首次安装：运行 `scripts/install.sh install [target]`。
- 明确要求更新：运行 `scripts/install.sh update [target]`。
- 明确要求采用无锁旧版：运行 `scripts/install.sh adopt-existing [target]`。

每次只选择一种模式。`target` 是用户指定的 git 仓库；省略时使用当前仓库。

`status` 永不转成写操作。`install` 报告旧版时，只提示用户明确要求 `update`；不要自行升级。
任何本地修改冲突都要停止，不得覆盖。

维护安装器时读 `references/protocol.md`；排查发现或触发行为时读 `references/compatibility.md`。
