# WARP VPS Manager 项目背景

WARP VPS Manager 为 Linux VPS 提供 Google 精准分流及全局 WARP，支持 WireGuard 与 Socks5 两种后端，通过 `warp-vps` 管理安装、状态、检测、换 IP、规则更新与生命周期。

- 仓库：[mqfut123/warp-vps-manager](https://github.com/mqfut123/warp-vps-manager)，公开仓库，项目位于根目录。
- 迁移读取基线：`96ca60a`（2026-09-05）；最近已记录版本为 [v1.4.0](https://github.com/mqfut123/warp-vps-manager/releases/tag/v1.4.0)。
- 当前阶段：v1.4.0 本地回归、Linux CI 与 Ubuntu arm64 / WireGuard 实际验证已记录；其余实机组合见 [todo](todo.md)。
- Outline 用于公司项目介绍、架构与跨团队协作，大版本或相关重大变化时维护；入口与同步范围见[根 AGENTS](../AGENTS.md#outline项目知识接入)。日常开发资料仍在本仓库cowork及既有文档，个人隐私与偏好留在localwork。

## 结构与边界

| 路径 | 职责 |
|---|---|
| `install.sh` | 安装和已有安装入口 |
| `bin/warp-vps` | 管理命令、状态、数据面与生命周期 |
| `scripts/generate-google-rules.py` | 按 Google 官方地址集合生成规则 |
| `rules/` | 随项目提供的初始 IP 快照 |
| `tests/` | Shell 回归与 Linux 网络验证 |
| `.github/workflows/ci.yml` | 自动回归与 Linux 验证 |

规则为 Google 官方 `goog.json - cloud.json`，排除 Cloud 客户地址。v1.4.0 起 VPS 可直接更新规则，自动开关以 `warp-vps-rules-update.timer` 的 systemd 启用状态为准；程序更新保留本机规则。

WireGuard 与 Socks5 承载能力、精准/全局路由范围、现有连接保护、依赖和公开命令以 [根 README](../README.md) 及当前实现为准。仅有 UDP 探测结果不代表 WireGuard 已握手；判断需要真实隧道证据。

项目维护约定见 [rules](rules.md)，文档入口见 [docs](docs/README.md)，版本与验证层次见 [timeline](docs/timeline.md)。
