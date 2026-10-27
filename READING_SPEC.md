# Dawn 知识库读取规范（统一）

## 仓库

| 项 | 值 |
|---|---|
| 远程 | `https://github.com/sitzising/dawn-game-knowledge.git` |
| 分支 | `main` |
| 本机克隆 | `E:/图小灵科技/游戏开发/Dawn：黎明/dawn-game-knowledge-main` |
| 游戏内源 | `游戏工程/data/knowledge/**` |
| 发布镜像 | `游戏工程/data/knowledge/github_publish/**` → 同步到仓库根目录 |
| 游戏工程 Git | **无** `.git`（勿对工程目录 push） |

**禁止创建第二个知识库仓库。**

## 域（domains）

现有：`zombies` `weather` `items` `npcs` `quests` `events` `factions` `localization` `world`  
新增：`maps`（官方地图元数据）

提示词 Markdown（`prompts/*.md`）**不走** KnowledgeManager `entries` 摄取，仅供人/Agent/网站文档读取。

## 地图字段（稳定 ID）

| 字段 | 说明 |
|---|---|
| `id` | 稳定主键，如 `hongkong_city`（禁止用「HongKong City」） |
| `display_name` / `display_name_key` | 展示用 |
| `data.enabled` | 是否对玩法启用 |
| `data.status` | `ACTIVE` / `LOCKED` / … |
| `data.scene_path` | Godot 主场景 `res://…` |
| `data.model_path` | 可选静态模型 |
| `data.preview_path` | 预览图 |
| `data.resource_paths` | 审计用完整资源列表 |
| `data.resource_exists` | 本机审计布尔（scene/model/preview） |
| `data.admin_selectable` | 后台可否开官方房 |

**后台有图 ≠ 本机/客户端已有资源。**

## 读取方

| 读者 | 读什么 | 不要做什么 |
|---|---|---|
| 本机 Cursor | `prompts/local_cursor_dev.md` + 各 catalog | 勿混用云端提示词 |
| 云端网站 | raw `maps/catalog.json` + `prompts/cloud_admin_web.md` | 勿把 Token 写进前端 |
| Godot 客户端 | 打包 `data/knowledge` / 可选 raw 更新 | 勿在客户端存 PAT |

## 校验

运行：`tools/validate_knowledge_maps.ps1`（相对游戏工程根目录）。
