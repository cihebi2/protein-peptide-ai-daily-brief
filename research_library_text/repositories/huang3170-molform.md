# huang3170/MolForm

- **仓库：** [https://github.com/huang3170/MolForm](https://github.com/huang3170/MolForm)
- **固定 commit：** `7a05ede432f2fb1574924140119c58fcbac1377e`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 30

## 仓库摘要

仓库包含结构基础药物设计相关的生成、性质预测、采样与评估流水线；冻结清单未见实际数据包或 checkpoint，且仅做了静态审查，源码许可为 MIT，但外部数据与第三方评分资源边界仍需单独核验。

## 可复用模块与资源

### datasets

- `datasets/pdbbind.py`
  - 能力：PDBBind_loader
  - 用途：PDBBind 相关样本读取与组织
  - 复用状态：ready_for_review；类型：code_entry
- `datasets/pl_pair_dataset.py`
  - 能力：protein_ligand_pair_dataset
  - 用途：protein-ligand pair 数据封装
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/data_preparation/clean_crossdocked.py`
  - 能力：CrossDocked_cleaning
  - 用途：清洗 CrossDocked 来源数据；实际原始数据未冻结在仓库中
  - 复用状态：partial；类型：code_entry
- `scripts/data_preparation/extract_pockets.py`
  - 能力：pocket_extraction
  - 用途：从蛋白-配体复合物中提取 pocket
  - 复用状态：partial；类型：code_entry
- `scripts/data_preparation/split_pl_dataset.py`
  - 能力：dataset_split_builder
  - 用途：构建 protein-ligand 数据切分
  - 复用状态：partial；类型：code_entry

### evaluation

- `scripts/evaluate_diffusion.py`
  - 能力：diffusion_evaluation
  - 用途：生成结果评估入口
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/evaluate_from_meta.py`
  - 能力：meta_based_evaluation
  - 用途：基于 meta 信息的评估入口
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/property_prediction/eval_prop.py`
  - 能力：property_eval
  - 用途：性质预测评估入口
  - 复用状态：ready_for_review；类型：code_entry
- `utils/evaluation/docking_vina.py`
  - 能力：docking_vina
  - 用途：Vina docking 评分
  - 复用状态：ready_for_review；类型：code_entry
- `utils/evaluation/docking_qvina.py`
  - 能力：docking_qvina
  - 用途：QVina docking 评分
  - 复用状态：ready_for_review；类型：code_entry
- `utils/evaluation/eval_atom_type.py`
  - 能力：atom_type_metric
  - 用途：原子类型一致性评估
  - 复用状态：ready_for_review；类型：code_entry
- `utils/evaluation/eval_bond_length.py`
  - 能力：bond_length_metric
  - 用途：键长分布评估
  - 复用状态：ready_for_review；类型：code_entry
- `utils/evaluation/scoring_func.py`
  - 能力：scoring_aggregation
  - 用途：综合评分/指标聚合
  - 复用状态：ready_for_review；类型：code_entry
- `utils/evaluation/similarity.py`
  - 能力：similarity_metric
  - 用途：相似度评估
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `scripts/sample_diffusion.py`
  - 能力：diffusion_sampling
  - 用途：扩散/flow matching 采样
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/sample_for_pocket.py`
  - 能力：pocket_conditioned_sampling
  - 用途：按 pocket 条件生成/采样
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/property_prediction/inference.py`
  - 能力：property_prediction_inference
  - 用途：性质预测推理入口
  - 复用状态：ready_for_review；类型：code_entry
- `configs/sampling.yml`
  - 能力：sampling_recipe
  - 用途：采样配置
  - 复用状态：ready_for_review；类型：config

### reusable_assets

- `models/egnn.py`
  - 能力：core_model_backbone
  - 用途：结构感知图神经网络骨干，用于分子/蛋白-配体表示学习
  - 复用状态：ready_for_review；类型：code_entry
- `models/uni_transformer.py`
  - 能力：multimodal_generation_model
  - 用途：多模态 Transformer 组件，用于结构/语义联合建模
  - 复用状态：ready_for_review；类型：code_entry
- `models/molopt_score_model.py`
  - 能力：optimization_score_model
  - 用途：分子优化相关打分/选择模型模块
  - 复用状态：ready_for_review；类型：code_entry
- `utils/reconstruct.py`
  - 能力：reconstruction_utility
  - 用途：将生成表示重建为可分析的分子结构
  - 复用状态：ready_for_review；类型：code_entry
- `utils/evaluation/sascorer.py`
  - 能力：SA_score_helper
  - 用途：SA score 评估实现；应与 companion 数据表一起核验来源与许可
  - 复用状态：partial；类型：code_entry
- `utils/evaluation/fpscores.pkl.gz`
  - 能力：SA_score_lookup_table
  - 用途：SA score 计算所需的 fragment score 表
  - 复用状态：partial；类型：unknown

### training

- `utils/train.py`
  - 能力：generic_training_entrypoint
  - 用途：通用训练入口与调度
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/train_diffusion.py`
  - 能力：diffusion_training
  - 用途：扩散/flow matching 相关训练入口
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/property_prediction/train_prop.py`
  - 能力：property_prediction_training
  - 用途：性质预测模型训练入口
  - 复用状态：ready_for_review；类型：code_entry
- `configs/training_standard.yml`
  - 能力：standard_training_recipe
  - 用途：标准训练配置
  - 复用状态：ready_for_review；类型：config
- `configs/training_dpo.yml`
  - 能力：dpo_training_recipe
  - 用途：DPO 训练配置
  - 复用状态：ready_for_review；类型：config
- `configs/prop/pdbbind_general_egnn.yml`
  - 能力：property_prediction_recipe
  - 用途：PDBBind 上的性质预测配置
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做静态审查，未执行代码、训练、测试或评估。
- 冻结清单未包含任何 checkpoint 或模型权重。
- 未发现 bundled data；实际数据依赖外部下载/预处理，许可边界未被该仓库许可自动覆盖。
- `utils/evaluation/sascorer.py` 与 `utils/evaluation/fpscores.pkl.gz` 的原始来源与再分发条件仅能从路径推测，未被静态证据完全确认。

## 仍未知

- README 与脚本中的具体超参数、数据切分规则和命令行参数未做内容核验。
- `sascorer`/`fpscores` 是否为完整 vendored 第三方实现及其上游许可仍需单独确认。
- 仓库是否存在未列出的外部下载产物或私有权重，静态清单无法证明。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
