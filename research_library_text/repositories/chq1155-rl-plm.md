# chq1155/rl-plm

- **仓库：** [https://github.com/chq1155/rl-plm](https://github.com/chq1155/rl-plm)
- **固定 commit：** `c901a00040258d9fe7fd27cb3b82680574f0d638`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 0

## 仓库摘要

仓库主要实现面向蛋白序列优化的 RL 研究代码，覆盖 AMP、antibody 与 kinase 三条任务线；静态清单未见 bundled data 或 checkpoints，顶层为 MIT，但 `stable_baselines3` 目录属于 vendored third-party。

## 可复用模块与资源

- 未发现可公开描述的结构化资产。
## 使用限制

- 仅做静态清单分析，未安装依赖、未运行训练/评估、未验证结果。
- 未发现 bundled data 或 checkpoint 路径，因此无法确认是否存在仓库外数据或训练产物。
- `kinase_mutation/stable_baselines3/` 为 vendored third-party，许可证边界需要单独核查。
- `amp_design/generation.py` 存在，但静态证据不足以确认它是独立 inference entrypoint。

## 仍未知

- 外部数据集名称、下载方式与预处理协议未在冻结清单中明确。
- 仓库中未列出 checkpoint 文件，无法判断是否存在未冻结的大权重文件。
- vendored `stable_baselines3` 的上游许可证未被单独解析。
- `amp_design/generation.py` 的实际运行角色仍不确定。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
