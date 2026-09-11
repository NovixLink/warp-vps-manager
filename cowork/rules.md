# WARP VPS Manager 项目规则

路径相对仓库根目录。规则从现行 README、源码与维护记录整理。

## 权威与实现

- Google 规则只使用官方 `goog.json` 与 `cloud.json` 的集合差；不能把 Google Cloud 客户网段混入 Google 服务精准分流。
- 修改规则生成器后核对完整集合与排除结果，不以固定条目数代替内容验证。
- `warp-vps-rules-update.timer` 的 systemd 启用状态是自动更新开关的唯一来源，配置不另存影子开关。规则与程序更新保持既有独立职责。
- 按系统实际包管理器、依赖和网络能力选择已支持路径；保持 README 中 WireGuard / Socks5 与精准 / 全局的公开契约。
- 网络改动只管理项目拥有的路由、网卡、nftables 对象与文件；共享依赖和外部项目资源不推定为本项目所有。
- 解锁检测依据实际地区字段及正负页面特征；不得复制第三方静态 Cookie、单字符串硬判规则或将普通 HTTP 成功视为解锁成功。

## 检查与交付

按改动范围运行既有检查，完整发布检查为：

```bash
bash -n install.sh
bash -n bin/warp-vps
shellcheck install.sh bin/warp-vps tests/*.sh
bash tests/run.sh
python3 -m py_compile scripts/generate-google-rules.py
git diff --check
```

安装包初始快照的现有更新入口：

```bash
python3 scripts/generate-google-rules.py --output rules
git diff -- rules
```

该命令会获取官方规则并修改 `rules/`，在实际规则维护范围内执行；日常 VPS 更新不要求同步发布新安装包。发布前核对根 README 的安装命令与实际行为。

## 实际系统验收

使用干净测试系统，记录系统/架构、模式、依赖初始状态、WireGuard 预检、重跑前服务状态及实际出口。按 [todo](todo.md) 补齐尚未验收的组合，不把已有回归或 Linux namespace 验证等同于所有发行版实机通过。

项目卸载命令的既有产品行为按 README 维护；运行安装、切换、卸载或网络变更须属于当前授权目标。整理协作资料不执行这些命令。
