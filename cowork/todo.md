# WARP VPS Manager 待办

| 编号 | 事项 | 状态 | 执行角色 | 下一步与完成依据 |
|---|---|---|---|---|
| WARP-ACCEPT-01 | 剩余实机矩阵 | 待授权测试环境 | 项目维护者 | 在干净 Ubuntu amd64 / Socks5、Debian amd64 / Socks5、Fedora 或 RHEL 系 / Socks5 上覆盖错误输入重跑、test、unlock-check、restart、update、uninstall，记录依赖、服务和最终出口。 |
| WARP-UNLOCK-01 | 实际检测中无法确认的请求 | 待可复现网络环境 | 项目维护者 | 保存实际响应中的地区与正负页面特征，确认是受限、传输失败还是证据不足；只有复现得到判定缺陷后再改公共检测逻辑。 |

## 已完成

- 2026-09-05：`96ca60a` / v1.4.0 的 226 项回归、Bash / Python 语法、ShellCheck、amd64 / arm64 Linux CI 与 Ubuntu 24.04 arm64 / WireGuard 实際规则更新、程序升级、定时器、菜单与卸载验证通过；范围见 [timeline](docs/timeline.md)。
- 2026-09-11：建立统一根 AGENTS / cowork，将可共享维护规则与验证结论纳入项目协作文档。

发布时更新初始快照和核对 README 属于 [rules](rules.md) 中的常规发布步骤，不重复列为长期未完成任务。
