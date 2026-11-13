# WARP VPS Manager

本项目提供Google精准分流、全局WARP及WireGuard/Socks5管理。

## 运行与检查

- 安装（用户侧）和管理命令见 [README](README.md)。
- 按改动范围选择已有检查；完整发布检查为：

```bash
bash -n install.sh
bash -n bin/warp-vps
shellcheck install.sh bin/warp-vps tests/*.sh
bash tests/run.sh
python3 -m py_compile scripts/generate-google-rules.py
git diff --check
```

- 安装包初始快照用 `python3 scripts/generate-google-rules.py --output rules` 重新生成，再 `git diff -- rules` 查看；该命令获取官方数据并修改`rules/`，只在实际规则维护范围内执行。VPS日常规则更新不要求重新发布安装包。发布前核对README安装命令及实际行为。

## 核心约束

- Google规则只取官方`goog.json - cloud.json`的完整集合差，排除Cloud客户网段；不以固定数量或非官方列表代替集合核对。
- WireGuard与Socks5、精准与全局模式的协议边界以[README](README.md)为准。Socks5不承载UDP或IPv6；UDP探测不等于WireGuard已握手，不能把原生出口当作WARP结果。
- `warp-vps-rules-update.timer`的systemd启用状态是自动更新开关权威，不增加镜像字段。规则更新与程序更新职责分开，程序更新保留当前规则。
- 只管理项目拥有的路由、网卡、nftables对象和文件；共享依赖及其他项目资源不推定为本项目所有。系统路径按实际包管理器和网络能力选择。
- 解锁判断使用实际地区及正负页面特征，不复制第三方Cookie或用普通HTTP成功代替可用性；保留现有“无法确认”等正常结果。
- 维护现有Bash/ShellCheck、回归和规则生成检查，实机结论限定到实际系统、架构与模式。安装/更新只选择明确运行文件，不复制仓库根、cowork或localwork。

## 做什么读什么

| 任务 | 读 |
|---|---|
| 安装、模式、路由、命令、规则更新、卸载 | [README](README.md) |
| 安装与已有安装入口 | `install.sh` |
| 管理命令、状态、数据面、生命周期、解锁检测 | `bin/warp-vps` |
| 规则生成与初始快照 | `scripts/generate-google-rules.py`、`rules/` |
| 回归与 Linux 网络验证 | `tests/run.sh`、`.github/workflows/ci.yml` |
| 进度、决定、踩坑、实机验证记录 | `cowork/`，先读 `cowork/AGENTS.md` |

## 资料入口

- 维护者内部资料在私有仓库 `NovixLink/warp-vps-manager-internal`。有权限时在本仓库根目录执行 `gh repo clone NovixLink/warp-vps-manager-internal cowork`；`cowork/` 已被忽略，不进入公开仓库。存在 `cowork/AGENTS.md` 时先读它。
- 无权限或尚未克隆时只按本文件和 README 工作；不在公开仓库新建 cowork 或提交内部资料。
- 本仓库只提交公开源码、测试、规则和使用说明；内部链接与内部规则只写在 cowork。`localwork/` 只放个人本机备注，不进入Git或发布产物。
