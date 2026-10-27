# dawn-game-knowledge

Dawn：黎明 — 统一游戏知识库（地图元数据、玩法配置、开发/云端提示词规范）。

- 远程：`https://github.com/sitzising/dawn-game-knowledge.git`
- 分支：`main`
- 公开 raw：`https://raw.githubusercontent.com/sitzising/dawn-game-knowledge/main/`

## 目录

| 路径 | 用途 |
|---|---|
| `manifest.json` | 版本与文件清单（含 sha256） |
| `maps/catalog.json` | 官方地图元数据（稳定 `id`） |
| `zombies/` `npcs/` `…` | 玩法配置域 |
| `prompts/local_cursor_dev.md` | **本机** Cursor / Godot 开发提示词 |
| `prompts/cloud_admin_web.md` | **云端** 网站/后台提示词 |
| `READING_SPEC.md` | 统一读取规范 |

## 重要约定

1. 地图主键是稳定 `id`（如 `hongkong_city`），不是显示名。
2. 后台列出某张地图 ≠ 客户端一定有对应 `res://` 资源。
3. 禁止提交 Token、密钥、玩家存档、`user://` 记忆。
4. 客户端游戏工程目录通常无 `.git`；本仓库是独立知识库。

详见 `READING_SPEC.md`。
