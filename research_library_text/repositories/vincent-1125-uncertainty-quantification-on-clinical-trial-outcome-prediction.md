# Vincent-1125/Uncertainty-Quantification-on-Clinical-Trial-Outcome-Prediction

- **仓库：** [https://github.com/Vincent-1125/Uncertainty-Quantification-on-Clinical-Trial-Outcome-Prediction](https://github.com/Vincent-1125/Uncertainty-Quantification-on-Clinical-Trial-Outcome-Prediction)
- **固定 commit：** `43725ed0c25aff009f1b6b8922620726926d5ed3`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 22

## 仓库摘要

该仓库是临床试验结局预测与不确定性量化的代码发布，包含 HINT 主模型、特征编码器、分阶段训练脚本、数据拆分/预处理工具、以及多个已打包数据集和 checkpoint；但未发现 LICENSE，且本次仅做静态盘点，不能证明可直接复用或可复现。

## 可复用模块与资源

### checkpoints

- `save_model/phase_I.ckpt`
  - 能力：phase_model_checkpoints
  - 用途：phase I/II/III 训练得到的模型权重
  - 复用状态：blocked；类型：model_weight
- `save_model/toy.ckpt`
  - 能力：auxiliary_and_fallback_checkpoints
  - 用途：toy / ADMET / 备份权重
  - 复用状态：blocked；类型：model_weight

### datasets

- `data/phase_I_train.csv`
  - 能力：phase_I_split_data
  - 用途：phase I 训练/验证/测试分割
  - 复用状态：blocked；类型：unknown
- `data/phase_II_train.csv`
  - 能力：phase_II_split_data
  - 用途：phase II 训练/验证/测试分割
  - 复用状态：blocked；类型：unknown
- `data/phase_III_train.csv`
  - 能力：phase_III_split_data
  - 用途：phase III 训练/验证/测试分割
  - 复用状态：blocked；类型：unknown
- `data/toy_train.csv`
  - 能力：toy_split_data
  - 用途：小规模 toy 实验分割
  - 复用状态：blocked；类型：unknown
- `data/ADMET/cooked/absorption_train.txt`
  - 能力：admet_aux_data
  - 用途：ADMET 辅助任务的 cooked 训练/验证语料
  - 复用状态：blocked；类型：unknown
- `data/raw_data.csv`
  - 能力：raw_aggregation_table
  - 用途：原始试验聚合表
  - 复用状态：unknown；类型：unknown
- `data/sponsor2approvalrate.csv`
  - 能力：sponsor_summary_tables
  - 用途：sponsor 统计特征与计数表
  - 复用状态：blocked；类型：unknown
- `data/drugbank_mini.csv`
  - 能力：drugbank_reference_subset
  - 用途：药物参考子集，供分子侧特征或对照使用
  - 复用状态：blocked；类型：unknown
- `icdcode/DXCCSR_v2021-1.CSV`
  - 能力：icd_mapping_resources
  - 用途：ICD/CCSR 码映射与描述资源
  - 复用状态：blocked；类型：unknown
- `IQVIA/trial_outcomes_v1.csv`
  - 能力：trial_outcomes_reference
  - 用途：试验结局标签/参考表
  - 复用状态：unknown；类型：unknown

### evaluation

- `benchmark/data_split.py`
  - 能力：split_generation_and_benchmarking
  - 用途：phase / ongoing 数据拆分生成
  - 复用状态：blocked；类型：code_entry
- `benchmark/collect_raw_data.py`
  - 能力：raw_data_collection_and_features
  - 用途：原始数据收集、汇总与特征构造
  - 复用状态：blocked；类型：code_entry
- `benchmark/description2icd10.py`
  - 能力：coding_and_mapping_utilities
  - 用途：disease/drug/protocol 与 ICD / sponsor / date 的映射与编码工具
  - 复用状态：blocked；类型：code_entry
- `benchmark/check_statistics_of_raw_data.py`
  - 能力：sanity_and_statistics_checks
  - 用途：数据统计、质量检查与辅助分析
  - 复用状态：blocked；类型：code_entry

### inference

- `HINT/sponsor_inference.py`
  - 能力：sponsor_inference
  - 用途：sponsor 相关推理与打分
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `HINT/model.py`
  - 能力：core_model
  - 用途：主模型结构，承载临床试验结局预测的多模态融合与分类逻辑
  - 复用状态：blocked；类型：code_entry
- `HINT/molecule_encode.py`
  - 能力：feature_encoders
  - 用途：分子、protocol 与 ICD 特征编码
  - 复用状态：blocked；类型：code_entry
- `HINT/dataloader.py`
  - 能力：data_loading
  - 用途：训练与推理的数据读取、batch 组装
  - 复用状态：blocked；类型：code_entry

### training

- `HINT/learn_phaseI.py`
  - 能力：phase_training_scripts
  - 用途：phase I/II/III 训练入口分散在多个脚本中
  - 复用状态：blocked；类型：code_entry
- `HINT/learn_indication.py`
  - 能力：task_specific_training
  - 用途：indication / multiple aim 相关训练
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态复核，未执行仓库代码、未跑测试、未验证输出
- 依赖未安装，运行环境与实际行为无法确认
- 未发现统一 training_entrypoint，训练逻辑分散在多个脚本
- 子模块未初始化，外部依赖内容不可见
- 存在 >5MiB 大文件，部分 blob 可能仅为 promisor 内容
- path presence 不能证明可复现或已成功训练

## 仍未知

- `data/raw_data.csv` 与 `IQVIA/trial_outcomes_v1.csv` 的具体来源、许可和清洗流程未证实
- `save_model/*.ckpt` 的训练超参、数据划分和对应脚本未能从静态清单中完整反推
- `benchmark/*` 是否覆盖完整评估协议与论文口径无法从静态路径本身确认
- `icdcode`、`DrugBank` 等外部参考资源是否完整保留原始许可边界仍不明确

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
