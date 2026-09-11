# WARP VPS Manager 时间线

| 日期 | 事件与证据 |
|---|---|
| 2026-09-05 | `9ff79f1` 隔离网络探测并保留 WireGuard 默认；`bdbf18b` 更新使用说明。 |
| 2026-09-05 | `96ca60a` / [v1.4.0](https://github.com/mqfut123/warp-vps-manager/releases/tag/v1.4.0) 增加每日 Google IP 自动更新及菜单管理，程序升级保留本机规则。 |
| 2026-09-11 | 统一 AGENTS / cowork，提炼项目维护规则、验收范围、踩坑与待办。 |

## v1.4.0 验证记录（2026-09-05）

- 226 项回归、Bash / Python 语法、ShellCheck 与 diff 检查通过；[main CI](https://github.com/mqfut123/warp-vps-manager/actions/runs/33958344380) 与 [标签 CI](https://github.com/mqfut123/warp-vps-manager/actions/runs/33958706988) 含 amd64 / arm64 回归和 Linux 路由验证。
- Ubuntu 24.04 arm64 独立测试 VM / WireGuard 实际安装、握手、双栈、规则及程序更新、菜单、定时器和卸载完成验证。
- 官方快照从 IPv4 262 更新为 303，IPv6 为 98；完整集合等于 `goog.json - cloud.json`，内核路由逐项一致，WARP 配置、网卡及服务保持原运行实例。
- 缩短测试触发时间的 systemd runtime drop-in 在验证后撤回，恢复每日计划；隔离网络的获取失败保留原规则和服务。
- 从 v1.3.4 原版更新器升级后补齐生成器、service 与 timer；旧安装默认未开启定时器，之后可手动开启。新版程序更新保留本机规则与元数据。
- 实際在线 WARP 验证限于上述系统/模式，部分 unlock-check 请求无法确认；其余组合与证据收集由 [todo](../todo.md) 跟踪。

本页记录当次验证结论，本次协作迁移未重新执行安装或外部流量验收。
