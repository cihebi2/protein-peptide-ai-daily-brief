# zhou-jianren/bioactive-peptides

- **仓库：** [https://github.com/zhou-jianren/bioactive-peptides](https://github.com/zhou-jianren/bioactive-peptides)
- **固定 commit：** `458bf0320f5d511256d9cf03dc787e95843f3c26`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 17

## 仓库摘要

该仓库是面向 ACE/ACP 的 bioactive peptide 预测工程，包含 CNN/GRU/CapsuleGAN 三类 notebook、Vote/stack 集成 notebook、两条 predict 入口、60 个 .h5 权重，以及原始/派生数据文件；未见 LICENSE、CI 或独立训练入口，静态证据不足以证明训练与评估曾实际运行。

## 可复用模块与资源

### checkpoints

- `ACE/save_models/CNN/Independence/ESM_0.h5`
  - 能力：ACE_CNN_checkpoints
  - 用途：CNN 在 Independence 下的 10 个 .h5 权重/检查点（ESM_0.h5–ESM_9.h5）。
  - 复用状态：unknown；类型：model_weight
- `ACE/save_models/CapsuleGAN/Independence/ESM_0.h5`
  - 能力：ACE_CapsuleGAN_checkpoints
  - 用途：CapsuleGAN 在 Independence 下的 10 个 .h5 权重/检查点（ESM_0.h5–ESM_9.h5）。
  - 复用状态：unknown；类型：model_weight
- `ACE/save_models/GRU/Independence/ESM_0.h5`
  - 能力：ACE_GRU_checkpoints
  - 用途：GRU 在 Independence 下的 10 个 .h5 权重/检查点（ESM_0.h5–ESM_9.h5）。
  - 复用状态：unknown；类型：model_weight
- `ACP/save_models/CNN/Independence/ESM_0.h5`
  - 能力：ACP_CNN_checkpoints
  - 用途：CNN 在 Independence 下的 10 个 .h5 权重/检查点（ESM_0.h5–ESM_9.h5）。
  - 复用状态：unknown；类型：model_weight
- `ACP/save_models/CapsuleGAN/Independence/ESM_0.h5`
  - 能力：ACP_CapsuleGAN_checkpoints
  - 用途：CapsuleGAN 在 Independence 下的 10 个 .h5 权重/检查点（ESM_0.h5–ESM_9.h5）。
  - 复用状态：unknown；类型：model_weight
- `ACP/save_models/GRU/Independence/ESM_0.h5`
  - 能力：ACP_GRU_checkpoints
  - 用途：GRU 在 Independence 下的 10 个 .h5 权重/检查点（ESM_0.h5–ESM_9.h5）。
  - 复用状态：unknown；类型：model_weight

### datasets

- `ACE/data/ACE.tsv`
  - 能力：ACE_raw_dataset
  - 用途：ACE 任务的原始/划分数据；包含 ACE.tsv、train.tsv、test.tsv 和 data.xlsx。
  - 复用状态：unknown；类型：unknown
- `ACE/data_process/ESM.csv`
  - 能力：ACE_derived_features_and_labels
  - 用途：ACE 任务的导出特征/标签表；包含 ESM.csv 与 label.csv。
  - 复用状态：unknown；类型：unknown
- `ACP/data/train.tsv`
  - 能力：ACP_raw_dataset
  - 用途：ACP 任务的原始训练/开发划分；包含 train.tsv 与 dev.tsv。
  - 复用状态：unknown；类型：unknown
- `ACP/features_label/train.csv`
  - 能力：ACP_derived_features_and_labels
  - 用途：ACP 任务的特征与标签表；包含 train.csv、train_label.csv、test.csv、test_label.csv。
  - 复用状态：unknown；类型：unknown

### evaluation

- `ACE/Vote.ipynb`
  - 能力：ACE_ensemble_evaluation_notebooks
  - 用途：ACE 的投票/堆叠式集成汇总与评估 notebook。
  - 复用状态：blocked；类型：unknown
- `ACP/Vote.ipynb`
  - 能力：ACP_ensemble_evaluation_notebooks
  - 用途：ACP 的投票/堆叠式集成汇总与评估 notebook。
  - 复用状态：blocked；类型：unknown

### inference

- `main/predict_ACE.py`
  - 能力：ACE_inference_entry
  - 用途：ACE 预测推理入口。
  - 复用状态：blocked；类型：code_entry
- `main/predict_ACP.py`
  - 能力：ACP_inference_entry
  - 用途：ACP 预测推理入口。
  - 复用状态：blocked；类型：code_entry

### training

- `ACE/model/CNN.ipynb`
  - 能力：ACE_model_notebooks
  - 用途：CNN、GRU、CapsuleGAN 的模型结构与训练 notebook；更像实验/训练脚本而非独立训练入口。
  - 复用状态：blocked；类型：unknown
- `ACP/model/CNN.ipynb`
  - 能力：ACP_model_notebooks
  - 用途：CNN、GRU、CapsuleGAN 的模型结构与训练 notebook；更像实验/训练脚本而非独立训练入口。
  - 复用状态：blocked；类型：unknown
- `ACP/data_process/ESM and PortT5.ipynb`
  - 能力：ACP_preprocessing_notebook
  - 用途：ESM/PortT5 特征处理与数据准备 helper notebook。
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态清单审查，未执行仓库代码。
- dependencies 未安装，无法验证运行时行为。
- tests/CI 未见到，也未实际运行。
- submodules 未初始化，外部引用内容不可见。
- large blobs 可能是 promisor-only，权重文件未做内容验证。
- 静态存在不等于可复现或已训练完成。

## 仍未知

- ACE/ACP 数据是否来自外部基准集及其转发许可。
- .h5 是否为最终训练权重、最佳 checkpoint，还是占位/中间产物。
- Vote.ipynb 与 stack.ipynb 是正式评估流程还是实验汇总。
- predict_ACE.py / predict_ACP.py 的输入格式、阈值与后处理细节。
- ESM 与 PortT5 预处理 notebook 生成的特征范围与是否完全一致。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
