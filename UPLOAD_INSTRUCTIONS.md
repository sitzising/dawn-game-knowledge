# 上传到 GitHub：`sitzising/dawn-game-knowledge`

仓库 raw 根：  
https://raw.githubusercontent.com/sitzising/dawn-game-knowledge/main/

## 必须由你上传的文件（本目录全部）

把 `data/knowledge/github_publish/` 下内容提交到仓库 **main** 根目录（覆盖现有空 `manifest.json`）：

| 本地路径 | 仓库路径 |
|----------|----------|
| `manifest.json` | `manifest.json` |
| `schema/knowledge_entry.schema.json` | `schema/knowledge_entry.schema.json` |
| `zombies/catalog.json` | `zombies/catalog.json` |
| `weather/catalog.json` | `weather/catalog.json` |
| `items/catalog.json` | `items/catalog.json` |
| `npcs/catalog.json` | `npcs/catalog.json` |
| `quests/templates.json` | `quests/templates.json` |
| `events/templates.json` | `events/templates.json` |
| `factions/catalog.json` | `factions/catalog.json` |
| `localization/term_index.json` | `localization/term_index.json` |

## 可由项目自动生成（不要手写哈希）

- 各文件 `sha256` / `bytes`（用 PowerShell `Get-FileHash -Algorithm SHA256` 或本仓库生成脚本）
- `knowledge_version` 递增
- 本目录整包：改 `res://data/knowledge/**` 后重新复制并重算 manifest

## 当前远程状态（已探测）

远程 [manifest.json](https://raw.githubusercontent.com/sitzising/dawn-game-knowledge/main/manifest.json) 现为：

- `knowledge_version: 1.0.0`
- `files: []` ← **空清单，客户端会拒绝更新并回退本地包**

请用本目录的完整 `manifest.json` 覆盖远程。

注意：远程曾设 `min_game_version: "4.0"`。发布包改为 `"0.0.0"`（或与 `application/config/version` 对齐）。客户端也会用引擎版本作兼容回退，但建议远程用游戏版本语义。

## 禁止上传

`.gd` / `.tscn` / `.exe` / `.dll` / Token / 玩家存档 / `user://` 内容
