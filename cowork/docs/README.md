# WARP VPS Manager 文档索引

| 主题 | 入口 |
|---|---|
| 安装、模式、路由、命令、规则更新与卸载 | [根 README](../../README.md) |
| 项目用途、源码结构与阶段 | [background](../background.md) |
| 维护规则、检查命令与真实验收要求 | [rules](../rules.md) |
| 规则生成契约 | [generate-google-rules.py](../../scripts/generate-google-rules.py)、[rules](../../rules/) |
| 自动化证据入口 | [tests](../../tests/)、[CI workflow](../../.github/workflows/ci.yml) |
| 状态、经验与历史 | [todo](../todo.md)、[pitfalls](pitfalls.md)、[timeline](timeline.md)、[error](../error/README.md) |

根 README 是公开使用说明，cowork 维护开发与协作资料。

## 发布边界

项目不运行网站服务。[安装器](../../install.sh) 与 [程序更新器](../../bin/warp-vps) 明确选择安装器、管理命令、规则生成器及三个规则文件，不复制仓库根目录。AGENTS 与 cowork 不进入安装路径；CI 中的临时 HTTP 服务仅返回网络测试文本，不提供文件目录。

## 维护约定

- 当前任务需要保存新的项目事实或明确要求维护文档时，才更新对应权威资料；普通查询、内容提取和单次回复草稿直接按请求交付，不为收尾新建记录或报告。
- 操作说明写当前做法；时间线只记重要变化、发布、事故和决定，关联提交与验证层次。历史更正追加说明，不改写过去发生的事件。
- 踩坑提炼可复用的触发条件、原因、处理与验证；错误跟随本项目的error索引。使用已有记录，不复制第二套现行状态。
- 移动文档时同步实际引用、构建和发布清单；包内直接消费的文件可保留原位。Outline按background中的状态和根规则处理。
