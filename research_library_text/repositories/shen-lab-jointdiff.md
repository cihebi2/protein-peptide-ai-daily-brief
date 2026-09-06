# shen-lab/jointdiff

- **仓库：** [https://github.com/shen-lab/jointdiff](https://github.com/shen-lab/jointdiff)
- **固定 commit：** `9d53e42cdbe4fd5fdb0f44fab318da2511a26701`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 0

## 仓库摘要

这是 JointDiff 的静态仓库审查：仓库提供蛋白序列/结构联合扩散的主模型、训练/推理/评估脚本，以及 CATH 和 motif-scaffolding 相关数据；未发现 tracked checkpoints，代码许可证为 GPL-3.0，但数据许可边界未能静态确认。

## 可复用模块与资源

- 未发现可公开描述的结构化资产。
## 使用限制

- 仅做静态清点，未运行代码、未安装依赖、未执行测试。
- 路径存在不等于可复现实验；仓库中的 .pkl、.pdb、.csv 仅能证明存在，不能证明可用权重或可执行结果。
- 未发现 tracked checkpoint/model weight 文件；若存在外部分发权重，本次静态审查无法覆盖。
- 代码与数据许可边界分离，数据集与处理后样本的上游条款需要单独核查。

## 仍未知

- `src_v0/diffab` 与 `.ipynb_checkpoints` 看起来像历史实现/临时产物，但它们与当前主线的关系未能仅凭静态清单确认。
- `data/*.pkl`、`data/*.pdb`、`data/*.csv` 的上游来源、生成流程和再分发许可未能从仓库静态清单确认。
- 未见明确 checkpoint 目录或权重文件；8 个 `.pkl` 更像数据缓存而非模型权重，但未逐文件打开验证。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
