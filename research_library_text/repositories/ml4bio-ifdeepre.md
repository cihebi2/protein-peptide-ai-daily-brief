# ml4bio/ifdeepre

- **仓库：** [https://github.com/ml4bio/ifdeepre](https://github.com/ml4bio/ifdeepre)
- **固定 commit：** `890ce62acb0219161118ccfb80f6dd3b61799244`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 16

## 仓库摘要

仓库提供 ifDEEPre 的静态推理管线：从 FASTA 预处理、ESM-1b/Pfam 特征提取到 EC 四位数字分级预测与结果输出；未见训练入口或独立评测流程。

## 可复用模块与资源

### checkpoints

- `tmp/ifdeepre_inputExample_processed/esm_1b_output/0.pt`
  - 能力：ESM-1b tensor cache
  - 用途：50 个同类 `.pt` 文件中的代表项，作为下游 EC 预测的嵌入缓存。
  - 复用状态：partial；类型：model_weight
- `tmp/ifdeepre_inputExample_processed/feature_and_result/funcd_esm1b.pickle`
  - 能力：serialized feature cache
  - 用途：保存抽取后的特征字典/中间结果。
  - 复用状态：partial；类型：unknown
- `test_sequence/ifdeepre_inputExample_processed_fasta_ID_sequences_with_predictions.p`
  - 能力：demo prediction cache
  - 用途：保存示例输入的预测结果。
  - 复用状态：partial；类型：unknown

### datasets

- `test_sequence/ifdeepre_inputExample.fasta`
  - 能力：demo input FASTA
  - 用途：示例蛋白序列输入。
  - 复用状态：partial；类型：unknown
- `test_sequence/ifdeepre_inputExample_processed.fasta`
  - 能力：processed demo FASTA
  - 用途：预处理后的示例输入。
  - 复用状态：partial；类型：unknown
- `src_v6_Final_server/ec_function_mapping.csv`
  - 能力：EC lookup table
  - 用途：EC 号与功能映射参考。
  - 复用状态：partial；类型：unknown
- `src_v6_Final_server/ec_mapping_3_digits.csv`
  - 能力：three-digit EC mapping table
  - 用途：三位 EC 号映射参考。
  - 复用状态：partial；类型：unknown

### inference

- `src_v6_Final_server/code_1_first_digit.py`
  - 能力：staged EC number inference
  - 用途：与 `first_num_predict.py`、`second_num_predict.py`、`third_num_predict.py`、`fourth_num_predict.py` 及后处理脚本共同完成 EC 1-4 位分级预测。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src_v6_Final_server/code_0_pre_processing.py`
  - 能力：sequence preprocessing
  - 用途：对输入 FASTA 做预处理，生成后续特征抽取所需的中间序列。
  - 复用状态：ready_for_review；类型：code_entry
- `src_v6_Final_server/generate_features.py`
  - 能力：ESM-1b feature extraction orchestration
  - 用途：串联特征生成、Pfam/ESM 中间文件写入与结果目录组织。
  - 复用状态：ready_for_review；类型：code_entry
- `src_v6_Final_server/extract_esm_1b.py`
  - 能力：ESM-1b embedding extraction
  - 用途：生成下游 EC 预测所需的 `.pt` 级别 ESM-1b 表征文件。
  - 复用状态：ready_for_review；类型：code_entry
- `src_v6_Final_server/protein_sequence_process_functions.py`
  - 能力：sequence helper functions
  - 用途：提供序列处理、过滤与辅助函数。
  - 复用状态：ready_for_review；类型：code_entry
- `src_v6_Final_server/code_2_second_digit_post_processing.py`
  - 能力：post-processing for EC digit predictions
  - 用途：对第二位数字预测结果做后处理。
  - 复用状态：ready_for_review；类型：code_entry
- `src_v6_Final_server/code_3_third_digit_post_processing.py`
  - 能力：post-processing for EC digit predictions
  - 用途：对第三位数字预测结果做后处理。
  - 复用状态：ready_for_review；类型：code_entry
- `src_v6_Final_server/result_print.py`
  - 能力：result formatting
  - 用途：汇总并打印预测结果。
  - 复用状态：ready_for_review；类型：code_entry
- `environment.yml`
  - 能力：runtime environment spec
  - 用途：描述 Python 依赖环境。
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做静态审计，未运行仓库代码。
- 依赖未安装，tests 未运行。
- 未见训练入口或训练模块。
- 未见独立 evaluation 脚本；现有 result/log 文件不能证明可复现评测。
- `tmp/` 下 `.pt` 与 `.pickle` 仅能证明存在，不能证明可复现推理或训练。

## 仍未知

- `tmp/` 下 50 个 `.pt` 文件的确切来源与生成参数无法从静态文件名确认。
- `ec_function_mapping.csv` 和 `ec_mapping_3_digits.csv` 的外部来源/版权状态不明。
- `environment.yml` 未安装，无法验证依赖是否足以复现当前流程。
- `.pickle` 与 `.out` 文件更像中间产物或结果缓存，未能确认是否属于作者刻意发布的可复用资产。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
