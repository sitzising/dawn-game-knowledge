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

现有：`zombies` `weather` `items` `npcs` `quests` `events` `factions` `localization` `world` `maps`  
新增：`buildings`（建筑人体尺度标准 / 稳定 ID 注册；见 `buildings/scale_standards.json`）

提示词 Markdown（`prompts/*.md`）**不走** KnowledgeManager `entries` 摄取，仅供人/Agent/网站文档读取。

## 建筑尺度（buildings）

| 字段 / 规则 | 说明 |
|---|---|
| `type_standards.*` | 住宅 / 商业 / 工业 / 高层 / 车库 / 道路 分型米制标准 |
| `map_root_policy.hongkong_city` | **K=1**，根缩放 **1.0**（无门高/跨度自动拟合）；地图须按米制导出 |
| `repair_policy` | 禁止统一放大所有建筑；禁止整栋均匀缩放拉坏门窗/入口/底层；优先楼层模块 / 切面上部延伸 |
| `entries[].id` | 建筑稳定主键（禁止用显示名） |
| 自动检查 | Schema：`schema/buildings_scale.schema.json`；探针：`addons/tests/probe_building_scale.gd` |
| AI 新增建筑 | 未通过尺度标准与探针不得标 `live` |
| `buildings/hk_building_registry.json` | 香港城建筑审计注册表；既有 ID（`hk_garage_b2` / `hk_proto_house_01`）禁止重编号；其余 `hk_mesh_*` |
| 探针 | `addons/tests/probe_building_scale.gd`（headless）；异常快照见工程 `docs/map/hk_building_anomalies_*.json` |

详细方案：`游戏工程/docs/map/MAP_BUILDING_SCALE_REPAIR_PLAN.md`；清单摘要：`docs/map/HK_BUILDING_INVENTORY.md`。

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
