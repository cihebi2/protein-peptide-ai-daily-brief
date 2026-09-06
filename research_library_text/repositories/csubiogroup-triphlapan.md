# CSUBioGroup/TripHLApan

- **仓库：** [https://github.com/CSUBioGroup/TripHLApan](https://github.com/CSUBioGroup/TripHLApan)
- **固定 commit：** `1b1ff44c275c5e5284d93babf9b11afbb9bd0897`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 24

## 仓库摘要

该仓库静态呈现了 TripHLApan/TripHLApanII 两套 HLA-peptide 结合预测流程：包含数据预处理、特征/预测辅助脚本、TripHLApanII 的模型定义、独立测试脚本、若干预测样例和多组 checkpoint；但未发现 LICENSE，也未执行任何代码或测试，因此只能给出静态复用分层。

## 可复用模块与资源

### checkpoints

- `TripHLApan/models/TripHLApan/validate_param_fold1epoch30_batch4154.pkl`
  - 能力：checkpoint
  - 用途：TripHLApan 5-fold checkpoint family 的代表文件。
  - 复用状态：blocked；类型：unknown
- `TripHLApan/models/TripHLApan_common_8/validate_param_fold1epoch4_batch332.pkl`
  - 能力：checkpoint
  - 用途：TripHLApan_common_8 模型权重代表文件。
  - 复用状态：blocked；类型：unknown
- `TripHLApan/models/TripHLApan_unseen_8/validate_param_fold1epoch46_batch9.pkl`
  - 能力：checkpoint
  - 用途：TripHLApan_unseen_8 模型权重代表文件。
  - 复用状态：blocked；类型：unknown
- `TripHLApan/models/TripHLApan_unseen_9_14/validate_param_fold1epoch7_batch90.pkl`
  - 能力：checkpoint
  - 用途：TripHLApan_unseen_9_14 模型权重代表文件。
  - 复用状态：blocked；类型：unknown
- `TripHLApanII/models/model/validate_param_fold1epoch27_batch12039.pkl`
  - 能力：checkpoint
  - 用途：TripHLApanII 模型权重代表文件。
  - 复用状态：blocked；类型：unknown

### datasets

- `TripHLApan/assistant_codes/hla_prot.fasta`
  - 能力：dataset
  - 用途：HLA protein sequence reference。
  - 复用状态：blocked；类型：unknown
- `TripHLApan/assistant_codes/map_allele_seq.txt`
  - 能力：dataset
  - 用途：allele-sequence 映射表。
  - 复用状态：blocked；类型：unknown
- `TripHLApan/assistant_codes/pretrain_train.txt`
  - 能力：dataset
  - 用途：预训练/训练样本列表或划分文件。
  - 复用状态：blocked；类型：unknown
- `TripHLApan/assistant_codes/pretrain_dev.txt`
  - 能力：dataset
  - 用途：预训练/验证样本列表或划分文件。
  - 复用状态：blocked；类型：unknown
- `TripHLApan/codes/blosum62.txt`
  - 能力：dataset
  - 用途：蛋白序列替换矩阵/特征资源。
  - 复用状态：unknown；类型：unknown
- `TripHLApan/assistant_codes/phy/AAIndex_name.data`
  - 能力：dataset
  - 用途：氨基酸理化特征索引目录。
  - 复用状态：unknown；类型：unknown
- `TripHLApan/codes/embedding_protein.txt`
  - 能力：dataset
  - 用途：蛋白 embedding 资源。
  - 复用状态：unknown；类型：unknown

### evaluation

- `TripHLApan/codes/independent_test.py`
  - 能力：evaluation
  - 用途：独立测试/评价脚本。
  - 复用状态：blocked；类型：code_entry
- `TripHLApanII/codes/independent_test.py`
  - 能力：evaluation
  - 用途：TripHLApanII 的独立测试/评价脚本。
  - 复用状态：blocked；类型：code_entry

### inference

- `TripHLApan/for_prediction/test.txt`
  - 能力：inference
  - 用途：推理输入示例；仓库还包含对应输出样例文件。
  - 复用状态：blocked；类型：unknown
- `TripHLApan/for_prediction/outputs/test.txt`
  - 能力：inference
  - 用途：推理输出样例。
  - 复用状态：blocked；类型：unknown
- `TripHLApanII/for_prediction/test.txt`
  - 能力：inference
  - 用途：TripHLApanII 的推理输入示例。
  - 复用状态：blocked；类型：unknown
- `TripHLApanII/for_prediction/test_output.txt`
  - 能力：inference
  - 用途：TripHLApanII 的推理输出样例。
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `TripHLApan/codes/data_pre_processing2.py`
  - 能力：data_loader
  - 用途：HLA-peptide 输入预处理与特征张量构造。
  - 复用状态：blocked；类型：code_entry
- `TripHLApanII/codes/data_pre_processing2.py`
  - 能力：data_loader
  - 用途：TripHLApanII 分支的输入预处理与特征构造。
  - 复用状态：blocked；类型：code_entry
- `TripHLApanII/codes/model.py`
  - 能力：model_architecture
  - 用途：TripHLApanII 的模型结构定义。
  - 复用状态：blocked；类型：code_entry
- `TripHLApan/assistant_codes/gene_predictions.py`
  - 能力：inference
  - 用途：基因/蛋白预测辅助脚本，疑似用于批量打分或输出预测结果。
  - 复用状态：blocked；类型：code_entry
- `TripHLApanII/assistant_codes/gene_predictions.py`
  - 能力：inference
  - 用途：TripHLApanII 分支的预测辅助脚本。
  - 复用状态：blocked；类型：code_entry
- `TripHLApan/assistant_codes/extract_allele_seq_mapping.py`
  - 能力：reusable_asset
  - 用途：等位基因到序列映射的整理/提取工具。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行仓库代码或测试。
- 未安装依赖，无法验证 import、运行路径或环境兼容性。
- 未初始化子模块；若有外部资源引用，当前不能确认完整性。
- `large_blobs_over_5MiB_may_be_promisor_only`，部分大文件可能只是指针级可见。
- checkpoint 仅能证明文件存在，不能证明可加载或性能可复现。

## 仍未知

- 未发现明确的训练入口脚本，因此训练流程只能从 checkpoint 与数据划分文件侧面推断。
- `for_prediction` 目录中的文件更像样例输入/输出，是否覆盖正式推理流程仍不明确。
- AAIndex、BLOSUM、embedding 等特征表的来源与授权未在冻结清单中确认。
- TripHLApan 与 TripHLApanII 的职责边界和主次版本关系仅能从路径名判断，未读文件内容。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
