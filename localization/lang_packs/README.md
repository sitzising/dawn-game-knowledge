# 游戏语言包

仓库：`https://github.com/sitzising/dawn-game-knowledge` · 分支 `main`

| 文件 | 说明 |
|------|------|
| `catalog.json` | 客户端清单（`DawnLangPackRemote`） |
| `<lang_id>/pack.json` | 键值消息：`{ "id", "version", "messages": { "KEY": "…" } }` |
| `en/source_map.json` | 中文 msgid → 英文（`DawnLocale.T` 运行时映射） |

- **默认语言：`en`（English）**；繁體 `zh_TW` 为可选内建语言。
- `en` / `zh_TW` 均已随客户端发布；本目录同步镜像供远程清单与审核。
- 仅 JSON；禁止脚本/可执行文件。
- Raw 基址：`https://raw.githubusercontent.com/sitzising/dawn-game-knowledge/main/`
