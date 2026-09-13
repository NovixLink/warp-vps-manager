# WARP VPS Manager 维护与验证

核心网络和规则边界见[根AGENTS](../AGENTS.md)，公开命令与运行条件见[README](../README.md)。

## 发布检查

按改动范围选择已有检查；完整发布检查为：

```bash
bash -n install.sh
bash -n bin/warp-vps
shellcheck install.sh bin/warp-vps tests/*.sh
bash tests/run.sh
python3 -m py_compile scripts/generate-google-rules.py
git diff --check
```

安装包初始快照使用现有入口：

```bash
python3 scripts/generate-google-rules.py --output rules
git diff -- rules
```

该命令获取官方数据并修改`rules/`，在实际规则维护范围内执行。发布前核对README安装命令及实际行为；VPS日常规则更新不要求重新发布安装包。

## 实际系统记录

使用干净系统，记录系统/架构、模式、依赖初始状态、WireGuard预检、重跑前服务状态与实际出口。未完成组合见[todo](todo.md)，已有验证与可复用经验见[文档索引](docs/README.md)。卸载等生命周期行为按README维护，实际运行需属于当前授权目标。
