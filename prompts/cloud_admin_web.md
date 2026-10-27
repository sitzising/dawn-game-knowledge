# Dawn：黎明 — 云服务器网站 / 管理后台系统提示词

适用范围：管理后台、HTTP API、官方房间创建、网站 CMS、服务器编排。**不是**本机 Godot 客户端改场景用的提示词。

## 知识库来源

- 仓库：`https://github.com/sitzising/dawn-game-knowledge`
- 分支：`main`
- 公开 raw（只读，无 Token）：
  - Manifest：`https://raw.githubusercontent.com/sitzising/dawn-game-knowledge/main/manifest.json`
  - 地图目录：`https://raw.githubusercontent.com/sitzising/dawn-game-knowledge/main/maps/catalog.json`

## 官方房间地图规则

1. 只使用 `maps/catalog.json` → `entries[].id` 作为房间 `map_id`。
2. 显示名称用 `display_name` / `display_name_key`，**禁止**把显示名当唯一键。
3. 后台可选条件建议：`data.enabled == true` **且** `data.admin_selectable == true`。
4. `data.resource_exists` 仅反映**某次本机审计**结果；后台列出某图 ≠ 所有客户端都已打包该资源。创建房间前应校验目标客户端/构建是否声明支持该 `map_id`。
5. 不要向浏览器或公开 API 响应中嵌入 GitHub PAT、EOS Secret、数据库密码。

## 与游戏客户端的关系

- 客户端权威地图表仍可能硬编码于 `MapRegistry`；知识库是跨端共享的元数据与规范层。
- 网站不得假设能直接加载 `res://` 路径；那些路径只对 Godot 客户端有意义。
- 联机房间应传稳定 `map_id`；客户端按本地 `MapRegistry` / 资源是否存在决定能否进入。

## 与本机提示词的边界

- Godot 场景/脚本/导出见 `local_cursor_dev.md`。
- 本文件只管网站与后台。
