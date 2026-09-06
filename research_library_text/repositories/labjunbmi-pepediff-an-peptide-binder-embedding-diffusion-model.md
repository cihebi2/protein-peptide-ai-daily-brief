# labjunbmi/pepediff-an-peptide-binder-embedding-diffusion-model

- **仓库：** [https://github.com/labjunbmi/pepediff-an-peptide-binder-embedding-diffusion-model](https://github.com/labjunbmi/pepediff-an-peptide-binder-embedding-diffusion-model)
- **固定 commit：** `aa6553e561106b8a4f68eb83667ddfd22ed1e9a1`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 24

## 仓库摘要

该仓库是一个面向 peptide binder 设计的核心实现库，包含模型、数据加载、训练与采样脚本，以及生成的 FASTA 输出；静态清单未见可复现的评测流程或模型权重 checkpoint。

## 可复用模块与资源

### datasets

- `data/generated_sequences/TIGIT/gen_tigit_peptide.fasta`
  - 能力：generated_peptide_sequences
  - 用途：TIGIT 目标相关的生成序列 FASTA
  - 复用状态：partial；类型：unknown
- `data/generated_sequences/testing_set/seq_checked_peptide_0.fasta`
  - 能力：bundled_test_sequences
  - 用途：testing_set 中的已检查肽序列之一；目录内共有 10 个同类 FASTA 文件
  - 复用状态：partial；类型：unknown
- `data/generated_sequences/testing_set/seq_checked_peptide_1.fasta`
  - 能力：bundled_test_sequences
  - 用途：testing_set 中的已检查肽序列之一；目录内共有 10 个同类 FASTA 文件
  - 复用状态：partial；类型：unknown
- `data/generated_sequences/testing_set/seq_checked_peptide_2.fasta`
  - 能力：bundled_test_sequences
  - 用途：testing_set 中的已检查肽序列之一；目录内共有 10 个同类 FASTA 文件
  - 复用状态：partial；类型：unknown
- `data/generated_sequences/testing_set/seq_checked_peptide_3.fasta`
  - 能力：bundled_test_sequences
  - 用途：testing_set 中的已检查肽序列之一；目录内共有 10 个同类 FASTA 文件
  - 复用状态：partial；类型：unknown
- `data/generated_sequences/testing_set/seq_checked_peptide_4.fasta`
  - 能力：bundled_test_sequences
  - 用途：testing_set 中的已检查肽序列之一；目录内共有 10 个同类 FASTA 文件
  - 复用状态：partial；类型：unknown
- `data/generated_sequences/testing_set/seq_checked_peptide_5.fasta`
  - 能力：bundled_test_sequences
  - 用途：testing_set 中的已检查肽序列之一；目录内共有 10 个同类 FASTA 文件
  - 复用状态：partial；类型：unknown
- `data/generated_sequences/testing_set/seq_checked_peptide_6.fasta`
  - 能力：bundled_test_sequences
  - 用途：testing_set 中的已检查肽序列之一；目录内共有 10 个同类 FASTA 文件
  - 复用状态：partial；类型：unknown
- `data/generated_sequences/testing_set/seq_checked_peptide_7.fasta`
  - 能力：bundled_test_sequences
  - 用途：testing_set 中的已检查肽序列之一；目录内共有 10 个同类 FASTA 文件
  - 复用状态：partial；类型：unknown
- `data/generated_sequences/testing_set/seq_checked_peptide_8.fasta`
  - 能力：bundled_test_sequences
  - 用途：testing_set 中的已检查肽序列之一；目录内共有 10 个同类 FASTA 文件
  - 复用状态：partial；类型：unknown
- `data/generated_sequences/testing_set/seq_checked_peptide_9.fasta`
  - 能力：bundled_test_sequences
  - 用途：testing_set 中的已检查肽序列之一；目录内共有 10 个同类 FASTA 文件
  - 复用状态：partial；类型：unknown

### inference

- `sample.py`
  - 能力：sampling_entrypoint
  - 用途：从已训练模型生成/采样候选序列
  - 复用状态：ready_for_review；类型：code_entry
- `sample_by_seq.py`
  - 能力：conditional_sampling_entrypoint
  - 用途：按输入序列进行条件采样
  - 复用状态：ready_for_review；类型：code_entry
- `emb_to_seq.py`
  - 能力：inference_helper
  - 用途：embedding 到序列的辅助转换逻辑
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `dataset.py`
  - 能力：data_loader
  - 用途：读取并组织训练/采样所需样本与输入特征
  - 复用状态：ready_for_review；类型：code_entry
- `model.py`
  - 能力：model_architecture
  - 用途：定义 PepEDiff 的模型结构与扩散相关组件
  - 复用状态：ready_for_review；类型：code_entry
- `train_model.py`
  - 能力：training_entrypoint
  - 用途：训练入口与训练循环编排
  - 复用状态：ready_for_review；类型：code_entry
- `sample.py`
  - 能力：inference
  - 用途：采样/推断入口
  - 复用状态：ready_for_review；类型：code_entry
- `sample_by_seq.py`
  - 能力：inference
  - 用途：按输入序列执行条件采样/推断
  - 复用状态：ready_for_review；类型：code_entry
- `emb_to_seq.py`
  - 能力：inference_helper
  - 用途：embedding 到序列的转换辅助逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `utils.py`
  - 能力：utility_helpers
  - 用途：通用辅助函数
  - 复用状态：ready_for_review；类型：code_entry
- `environment.yaml`
  - 能力：environment_recipe
  - 用途：依赖环境说明与安装配方
  - 复用状态：partial；类型：config
- `z_score_scaler.pkl`
  - 能力：normalization_artifact
  - 用途：z-score 标准化/反标准化相关对象，具体格式与来源未验证
  - 复用状态：partial；类型：unknown

### training

- `train_model.py`
  - 能力：training_entrypoint
  - 用途：训练入口与优化循环编排
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单审查，代码未执行、测试未运行、依赖未安装。
- 未见权重型 checkpoint；`z_score_scaler.pkl` 更像预处理/标定对象而非模型参数。
- `data/generated_sequences/*` 更像仓库内附带的生成结果，是否可作为独立数据集复用尚不明确。
- 无法仅凭路径 presence 证明这些 FASTA 一定由本次冻结 commit 生成。

## 仍未知

- `z_score_scaler.pkl` 的具体格式、训练来源与可逆性未验证。
- 未发现明确的 evaluation 脚本、指标汇总或基准对比文件。
- `method_flow.png`、README 以及源码内部逻辑未展开阅读，无法细分全部子模块职责。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
