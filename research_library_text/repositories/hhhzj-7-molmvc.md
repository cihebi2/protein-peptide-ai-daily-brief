# hhhzj-7/molmvc

- **仓库：** [https://github.com/hhhzj-7/molmvc](https://github.com/hhhzj-7/molmvc)
- **固定 commit：** `cbecec1c0a805c7ba26a238f181a7c1070242ca4`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 11

## 仓库摘要

该仓库实现了 MolMVC：面向药物相关任务的多视图对比学习分子表示框架，包含 GNN/SchNet 相关模块、预训练与下游微调脚本、评估代码、若干词表/加载器以及一个预训练权重；冻结清单中未见显式 LICENSE，也未包含原始训练数据。

## 可复用模块与资源

### checkpoints

- `save/model_pre20.pth`
  - 能力：pretrained model weight
  - 用途：预训练 checkpoint，可作为下游任务初始化权重。
  - 复用状态：unknown；类型：model_weight

### datasets

- `process_dataset/MPP/utils/master.csv`
  - 能力：benchmark registry / split metadata
  - 用途：列出 MPP 实验涉及的数据集/任务；不是原始样本数据。
  - 复用状态：unknown；类型：unknown

### evaluation

- `process_dataset/MPP/utils/evaluate.py`
  - 能力：metric computation
  - 用途：计算下游预测指标与评估结果。
  - 复用状态：blocked；类型：code_entry

### inference

- `get_pre_emb.py`
  - 能力：embedding extraction / feature inference
  - 用途：导出预训练表征供下游推理或特征提取使用。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `AMCLoss.py`
  - 能力：contrastive loss / multi-view objective
  - 用途：实现 MolMVC 预训练阶段的对比学习目标。
  - 复用状态：blocked；类型：code_entry
- `method/molecule_gnn_model.py`
  - 能力：molecular encoder / GNN backbone
  - 用途：核心分子表示网络，配合 `method/encoder.py` 与 `method/model_helper.py` 组织图表示学习。
  - 复用状态：blocked；类型：code_entry
- `method/schnet/schnet_oral.py`
  - 能力：3D / SchNet-style submodule
  - 用途：三维/几何特征分支，用于补充分子结构表征。
  - 复用状态：blocked；类型：code_entry
- `method/utils/geometric_computing.py`
  - 能力：geometry utilities
  - 用途：分子几何量与结构计算辅助。
  - 复用状态：blocked；类型：code_entry
- `ESPF/subword_units_map_chembl_freq_1500.csv`
  - 能力：ESPF tokenizer vocabulary
  - 用途：分子字符串子词/词表映射，配合 `ESPF/drug_codes_chembl_freq_1500.txt` 做文本式分子编码。
  - 复用状态：unknown；类型：unknown

### training

- `pretrain_MolMVC.py`
  - 能力：self-supervised pretraining entrypoint
  - 用途：MolMVC 预训练主脚本。
  - 复用状态：blocked；类型：code_entry
- `finetune_MPP.py`
  - 能力：downstream fine-tuning entrypoint
  - 用途：下游 MPP 任务的 fine-tuning 脚本。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未执行任何代码。
- 依赖未安装，训练/推理/评估均未验证。
- 未见原始数据或可复现实验数据包。
- 未见显式 LICENSE 文件，代码直接复用受限。
- checkpoint、词表与数据加载器的实际来源与一致性未验证。

## 仍未知

- `ESPF` 词表与 `drug_codes_chembl_freq_1500.txt` 的生成流程未公开验证。
- `process_dataset/MPP/utils/master.csv` 的精确语义与覆盖范围未确认。
- `get_pre_emb.py` 与 `downstream_until.py` 的具体运行角色只能从文件名推断。
- `save/model_pre20.pth` 是否与当前模型代码完全匹配无法静态确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
