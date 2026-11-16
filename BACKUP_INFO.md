# 备份说明 / Backup Info

> 本文件由 WorkBuddy 于 2026-11-16 自动生成，用于标注本仓库作为 **Agent2API 源码备份** 的来源、版本与差异。
> 目的：防止上游个人开发者关闭仓库、渠道或接口后无法继续取得源码。

## 1. 来源（Source）

| 项目 | 值 |
|---|---|
| 官方仓库 | https://github.com/aimod-cc/Agent2API |
| 官方最新版本下载地址 | https://github.com/aimod-cc/Agent2API/releases/latest |
| 本备份仓库 | https://github.com/34xiaoli/Agent2API （fork） |
| 开源协议 | AGPL-3.0（完整文本见 `LICENSE` 与 `licenses/`） |
| 主要语言 | Rust + Tauri 2（桌面端）；前端 TypeScript/JS |
| 官方描述 | 本地 AI 路由网关 + Agent 客户端接管：复用各家客户端登录态，一个 base_url 调用 50+ 家模型额度，统一 OpenAI / Anthropic / 生图接口 |

## 2. 版本信息（Version）

| 项目 | 版本 / 值 |
|---|---|
| 备份同步基线分支 | `main` |
| 同步基线 commit | `e8bed7397aaf9d8962489074557c2f1f1a8d4f97` |
| 基线提交时间 | 2026-11-05T07:02:52Z |
| 基线对应版本 | **v3.4.2**（最新稳定版） |
| 官方最新稳定 Release | v3.4.2，发布于 2026-11-05 |
| 官方预发布（未纳入基线） | v3.5.0-beta.1，发布于 2026-11-09 |
| 本机已安装版本 | 3.4.2（`F://Agent2API//agent2api.exe`，2026-11-05 编译） |

### 为什么备份基线选 v3.4.2 而不是 v3.5.0-beta.1

- `main` 分支当前 HEAD 就是 v3.4.2 的提交（官方把 beta 放在独立 tag/预发布通道，未合入 main）。
- v3.5.0-beta.1 是**预发布测试版**，含 WASM 插件、QuWork 接入等实验特性，并明确移除了"电脑端 Codex 对话及官方终端共享"——与本机当前用途不兼容，故不作为备份基线。
- 因此本 fork 的 `main` 与本机实际在用的 3.4.2 稳定版一致，是可直接回退复现的版本。

## 3. 与现有版本的差异（Diff）

| 对比项 | 结论 |
|---|---|
| 备份仓库 main vs 官方 main | **完全一致**（ahead_by=0, behind_by=0, status=identical） |
| 备份仓库 main vs 本机已安装 | **一致**：同为 3.4.2 稳定版源码 |
| 额外改动 | 仅新增本文件 `BACKUP_INFO.md`；未修改任何源码、配置或文档 |
| v3.5.0-beta.1 相对 v3.4.2 的主要变化（仅供参考，未纳入备份） | 新增独立 WASM 插件隔离环境、Magpie/OpenCode 插件目录、QuWork 账号接入、客户端多配置管理、图片兼容设置、临期凭证自动维护、面板自定义；优化统计报表/协议直通/云同步/内存占用；修复 TOML 配置丢失注释问题；**移除本轮 beta 的电脑端 Codex 对话及官方终端共享** |

## 4. 备份完整性（Contents）

本仓库包含官方源码的完整快照，关键内容：

- 完整后端源码（`desktop-tauri/`、`scripts/`、`src` 相关目录）
- 前端与多语言资源（`desktop-tauri/i18n/i18n-src/` 六语文案）
- 配置示例：`.env.example`、`docker-compose.yml`、`Dockerfile`
- 文档：`README.md`、`AGENTS.md`、`docs/`（安装部署、配置指南等）
- 构建与发布脚本：`.github/workflows/build.yml`、`packaging/`、`build/`
- 许可与版权：`LICENSE`、`licenses/`
- Agent 技能定义：`.agents/skills/`

## 5. 使用与恢复（Restore）

若上游仓库不可用，可直接从本仓库恢复源码：

```bash
git clone https://github.com/34xiaoli/Agent2API.git
cd Agent2API
# 构建桌面端（需 Rust >= 1.77、Tauri 2 工具链、Node >= 18.17）
npm run tauri:install
npm run tauri:build
```

或直接使用官方 Release 安装包（若 Release 页面仍可访问）：
`https://github.com/aimod-cc/Agent2API/releases/tag/v3.4.2`

## 6. 同步方法（Re-sync）

本仓库是 fork，可在上游可用时保持同步：

```bash
git remote add upstream https://github.com/aimod-cc/Agent2API.git
git fetch upstream
git checkout main
git merge upstream/main   # 或 git rebase upstream/main
git push origin main
```

快照校验（确认与上游一致）：

```bash
# 官方与本地 main 的 commit 应相同
# 2026-11-16 校验值：e8bed7397aaf9d8962489074557c2f1f1a8d4f97
git rev-parse HEAD
```

## 7. 安全与合规提示（Security）

- 本项目 AGPL-3.0 授权：使用、修改、分发（含商用）均被允许，但须保留版权与许可声明；以修改版对外提供网络服务时，需向用户提供对应源码。
- **切勿**把本机数据目录（如 `D://AI//agent2api-data`）、账号凭证、网关 Key、`*.key`、`auth.json`、`config.toml` 等敏感文件上传到任何公开仓库。本备份**仅含源码**，不含任何个人隐私或凭证数据。
- 本项目依赖各家客户端的登录态与额度，其可用性取决于上游服务条款；请自行评估合规风险。

---

*生成时间：2026-11-16 | 生成工具：WorkBuddy | 校验方式：GitHub REST API 对比官方与 fork 的 main commit*
