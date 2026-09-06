# baiwenhuim/ampban

- **仓库：** [https://github.com/baiwenhuim/ampban](https://github.com/baiwenhuim/ampban)
- **固定 commit：** `2ab435aa26554494efbfab866db18b3abde7a0dd`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 7

## 仓库摘要

冻结仓库是AMPBAN论文的配套资源快照，含2个FASTA数据集、2个Notebook、environment.yml和GPL-3.0许可；未见独立训练模块、推理入口或checkpoint文件。

## 可复用模块与资源

### datasets

- `data/peptipedia/positive_samples.fasta`
  - 能力：AMP positive sequence dataset
  - 用途：正类抗菌肽样本
  - 复用状态：unknown；类型：unknown
- `data/Swiss-Prot/negative_processed_samples.fasta`
  - 能力：AMP negative sequence dataset
  - 用途：负类非AMP样本
  - 复用状态：unknown；类型：unknown

### evaluation

- `5-fold-CV/ampban/ampban_cv.ipynb`
  - 能力：cross-validation evaluation notebook
  - 用途：5-fold交叉验证评估与结果汇总的候选入口
  - 复用状态：partial；类型：unknown

### reusable_assets

- `README.md`
  - 能力：documentation
  - 用途：概述项目目标、数据组织与Notebook入口
  - 复用状态：partial；类型：unknown
- `environment.yml`
  - 能力：environment specification
  - 用途：定义Python依赖环境与运行约束
  - 复用状态：partial；类型：config
- `AMPBAM_workflow.ipynb`
  - 能力：workflow notebook
  - 用途：整体数据处理与实验流程编排的候选入口
  - 复用状态：partial；类型：unknown

### training

- `5-fold-CV/ampban/ampban_cv.ipynb`
  - 能力：cross-validation training notebook
  - 用途：5-fold交叉验证训练/实验编排的候选入口
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态清单审查，未执行Notebook、未安装依赖、未运行测试。
- 训练与评估逻辑只能从文件名推断，无法确认具体实现或超参数。
- 未发现checkpoint、导出模型或独立推理脚本。
- 数据集来源与许可未单独标注，代码许可不能自动外推到数据。
- 冻结清单中没有模型架构文件，结构细节不可恢复。

## 仍未知

- AMPBAM_workflow.ipynb 是否包含预处理、训练还是仅展示流程不明。
- positive_samples.fasta 与 negative_processed_samples.fasta 的确切生成链路及是否为第三方镜像不明。
- Notebook 是否依赖外部下载的数据或隐藏大文件不明。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
