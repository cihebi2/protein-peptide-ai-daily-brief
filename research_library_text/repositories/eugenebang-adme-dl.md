# eugenebang/adme-dl

- **仓库：** [https://github.com/eugenebang/adme-dl](https://github.com/eugenebang/adme-dl)
- **固定 commit：** `427e2fbf67577e38e3d1ca98434b5f633ff8f33f`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 13

## 仓库摘要

仓库提供 ADME / drug-likeness 预测的训练、推理、数据切分和 checkpoint 资源；静态上未见独立评估、CI 或可验证复现链路。

## 可复用模块与资源

### checkpoints

- `ckpts/DLP_ADME_DL.pt`
  - 能力：model_weight
  - 用途：已训练的 DLP / ADME-DL 权重文件。
  - 复用状态：partial；类型：model_weight
- `ckpts/SeqADME_ADME_DL.pt`
  - 能力：model_weight
  - 用途：已训练的 SeqADME / ADME-DL 权重文件。
  - 复用状态：partial；类型：model_weight
- `src/graphmvp/pretraining_model.pth`
  - 能力：model_weight
  - 用途：GraphMVP 预训练初始化权重。
  - 复用状态：blocked；类型：model_weight

### datasets

- `data/ADME/a_train.csv`
  - 能力：dataset
  - 用途：4 个 ADME 子任务（a/d/e/m）的 train/valid/test 划分。
  - 复用状态：partial；类型：unknown
- `data/DLP/drugmap_chembl.csv`
  - 能力：dataset
  - 用途：drugmap_chembl / drugmap_pubchem / drugmap_zinc 辅助映射数据。
  - 复用状态：partial；类型：unknown
- `data/demo/demo_molecules.smi`
  - 能力：dataset
  - 用途：推理演示输入分子集合。
  - 复用状态：ready_for_review；类型：unknown

### inference

- `score_drug_likeness.py`
  - 能力：inference_entrypoint
  - 用途：对输入分子进行 drug-likeness 打分。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/graphmvp/models/molecule_gnn_model.py`
  - 能力：model_architecture
  - 用途：分子图神经网络骨干/编码器实现，用于后续 ADME / drug-likeness 预测。
  - 复用状态：partial；类型：code_entry
- `src/graphmvp/datasets.py`
  - 能力：data_loader
  - 用途：ADME 与 SeqMTL 的样本构建、加载和多任务组织逻辑。
  - 复用状态：partial；类型：code_entry
- `src/pcgrad.py`
  - 能力：training_helper
  - 用途：PCGrad 梯度冲突处理，支持多任务训练。
  - 复用状态：partial；类型：code_entry
- `utils/utils.py`
  - 能力：utility_helper
  - 用途：任务级预处理、日志或指标工具。
  - 复用状态：ready_for_review；类型：code_entry

### training

- `train_ADME.py`
  - 能力：training_entrypoint
  - 用途：ADME 训练入口。
  - 复用状态：ready_for_review；类型：code_entry
- `train_DLP.py`
  - 能力：training_entrypoint
  - 用途：DLP 训练入口。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单，未运行代码、训练、推理或测试。
- 未见独立 evaluation 或 CI 入口，评估逻辑可能嵌入训练脚本。
- `src/graphmvp/pretraining_model.pth` 的来源、授权和可复用性未验证。
- 数据与模型资源的许可边界不清，不能仅按 GPL-3.0 处理。

## 仍未知

- `src/graphmvp/` 下的实现是否为 vendored 第三方代码或作者改写版本，静态清单无法确认。
- 4 个 ADME 子任务 a/d/e/m 的精确定义未从静态证据确认。
- `drugmap_chembl/pubchem/zinc.csv` 的生成规则与上游来源未验证。
- `score_drug_likeness.py` 的具体 CLI 参数、输出格式和依赖权重未验证。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
