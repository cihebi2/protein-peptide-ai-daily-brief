# cmb-chula/MHCSeqNet2

- **仓库：** [https://github.com/cmb-chula/MHCSeqNet2](https://github.com/cmb-chula/MHCSeqNet2)
- **固定 commit：** `0d38b6598fbc10fd87e5452f1ff37834bfbad68d`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 14

## 仓库摘要

冻结仓库是 MHCSeqNet2 的研究代码包，包含模型定义、数据加载、预训练配置和 train.py；未见独立 inference/evaluation/checkpoint 产物，也未发现 LICENSE，因此只能做静态审查，不能证明可复现或可直接复用。

## 可复用模块与资源

### datasets

- `resources/VOCAB.txt`
  - 能力：dataset_resource
  - 用途：序列词表资源
  - 复用状态：blocked；类型：tokenizer
- `resources/VOCAB_ALLELE.txt`
  - 能力：dataset_resource
  - 用途：allele 词表资源
  - 复用状态：blocked；类型：tokenizer
- `resources/NEGATIVE_AMINO.txt`
  - 能力：dataset_resource
  - 用途：负样本氨基酸资源
  - 复用状态：blocked；类型：unknown
- `resources/allele_mapper/0_allele_mapper.yaml`
  - 能力：dataset_resource
  - 用途：allele 映射资源
  - 复用状态：blocked；类型：config

### reusable_assets

- `core/models/mhcseqnet2.py`
  - 能力：model_architecture
  - 用途：主模型结构，负责 peptide/MHC binding 预测相关计算
  - 复用状态：blocked；类型：code_entry
- `core/models/pretraining_model.py`
  - 能力：model_architecture
  - 用途：预训练或辅助模型定义
  - 复用状态：blocked；类型：code_entry
- `core/datasets/csv_datasets.py`
  - 能力：data_loader
  - 用途：CSV 输入解析与样本封装
  - 复用状态：blocked；类型：code_entry
- `core/datasets/msi011320.py`
  - 能力：data_loader
  - 用途：特定数据集加载逻辑
  - 复用状态：blocked；类型：code_entry
- `resources/datasets/PRETRAIN_3D/central2context.yaml`
  - 能力：config_recipe
  - 用途：3D 预训练上下文配置
  - 复用状态：blocked；类型：config
- `resources/datasets/PRETRAIN_HUMAN_PROTEIN/pair_map_counter.yaml`
  - 能力：config_recipe
  - 用途：human protein 预训练的 pair-map 配置
  - 复用状态：blocked；类型：config

### training

- `train.py`
  - 能力：training_entrypoint
  - 用途：训练入口与训练流程编排
  - 复用状态：blocked；类型：code_entry
- `scripts/prepare.py`
  - 能力：training_preparation
  - 用途：数据准备/预处理脚本
  - 复用状态：blocked；类型：code_entry
- `scripts/prepare_pretraining_3d_allele.py`
  - 能力：training_preparation
  - 用途：3D 预训练数据准备脚本
  - 复用状态：blocked；类型：code_entry
- `scripts/prepare_pretraining_human_protein.py`
  - 能力：training_preparation
  - 用途：human protein 预训练数据准备脚本
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未运行测试。
- 未安装依赖，未验证训练或推理链路。
- 未发现独立的 inference、evaluation 或 checkpoint 产物。
- 资源文件与 YAML 的真实来源、生成方式和数据规模未确认。
- 缺少 LICENSE，直接复用受限。

## 仍未知

- core/datasets/*.py 的具体输入列、过滤规则和样本来源未解析。
- resources/datasets/*.yaml 对应的采样参数与预训练任务未验证。
- 仓库是否依赖外部下载的数据或权重未确认。
- main.py / mhctool.py / InferenceOption.py 是否构成可用推理入口未能从冻结库存中确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
