# Dawn：黎明 — 本机 Cursor 开发提示词

适用范围：在开发者本机用 Cursor 修改 Godot **游戏工程**（场景、脚本、地图资源、NPC、僵尸、武器、联机客户端逻辑）。

## 环境事实

- 引擎：Godot **4.7.2-stable**（勿用未验证 API）
- 工程路径：`E:/图小灵科技/游戏开发/Dawn：黎明/游戏工程`（通常 **无 `.git`**）
- 独立知识库仓库：`https://github.com/sitzising/dawn-game-knowledge.git`  
  本地克隆：`E:/图小灵科技/游戏开发/Dawn：黎明/dawn-game-knowledge-main`（分支 `main`）
- 游戏内打包知识：`res://data/knowledge/**`；发布镜像：`res://data/knowledge/github_publish/**`

## 工作原则

1. 先读现有场景/脚本/知识 JSON，再改；优先最小改动。
2. 可配置内容写入 `data/knowledge/**`，并同步 `github_publish/**` 与独立知识库仓库。
3. 地图稳定 ID 以 `maps/catalog.json` 的 `id` 为准（如 `hongkong_city`），禁止用显示名当主键。
4. **不要**改写 `MapRegistry.MAPS` 加载路径，除非用户明确要求迁移；知识库地图元数据与客户端资源是否存在是两回事。
5. **禁止**把 GitHub Token、服务器密钥、管理员密码写入客户端工程或知识库公开文件。
6. 玩家动态记忆在 `user://`（KnowledgeManager player memory），不得推入公开知识库。
7. 知识库提交：仅在知识库仓库内显式 `git add` 文件；禁止 `git add .`；游戏工程目录勿假装有远程 Git。

## 与云端提示词的边界

- 本文件只管 **本机 Godot 游戏开发**。
- 管理后台 / API / 房间管理见同目录 `cloud_admin_web.md`，不要混成一份。
