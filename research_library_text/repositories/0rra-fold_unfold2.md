# 0rra/fold_unfold2

- **仓库：** [https://github.com/0rra/fold_unfold2](https://github.com/0rra/fold_unfold2)
- **固定 commit：** `fb5f2c5c5dd2a457637154cedbc366af644d913e`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 24

## 仓库摘要

静态审查显示该仓库主要围绕序列筛选、结构预测、PAE/AFDB 解析与 GPC 训练/验证展开，属于可迁移的预测/评分型工作流；未见 checkpoint，且未执行代码。

## 可复用模块与资源

### datasets

- `part1_refoldunfold/1_sequence_selection/sequences/antifam_seed_seqs/AntiFam.seed`
  - 能力：seed_sequences
  - 用途：作为 AntiFam 种子序列输入，供后续筛选/对照构建
  - 复用状态：partial；类型：unknown
- `part1_refoldunfold/1_sequence_selection/sequences/swissprot_seqs/sp_seqs.fasta`
  - 能力：reference_sequences
  - 用途：SwissProt 序列子集，用于对照与结构预测
  - 复用状态：partial；类型：unknown
- `part1_refoldunfold/1_sequence_selection/sequences/random_seqs/weighted_rdm.fasta`
  - 能力：negative_controls
  - 用途：加权随机序列对照集
  - 复用状态：ready_for_review；类型：unknown
- `part2_gpc_training/1_sequence_selection/sequences/train/train_swissprot.fasta`
  - 能力：training_sequences
  - 用途：GPC 训练集中的 SwissProt 样本
  - 复用状态：ready_for_review；类型：unknown
- `part2_gpc_training/1_sequence_selection/sequences/synth_afms/sampled_fakes_orgs.fasta`
  - 能力：synthetic_sequences
  - 用途：合成/采样的 fake organism 序列，用于训练或验证
  - 复用状态：ready_for_review；类型：unknown
- `data/taxonomy/taxonomy.txt`
  - 能力：reference_taxonomy
  - 用途：物种/分类学辅助表，支撑序列筛选与注释
  - 复用状态：partial；类型：unknown

### evaluation

- `part1_refoldunfold/2_structure_prediction/parsed_results/af_res_af3_info.csv`
  - 能力：prediction_summaries
  - 用途：保存 AF 组的 AlphaFold3 结果汇总，用于比较分析
  - 复用状态：ready_for_review；类型：unknown
- `part1_refoldunfold/2_structure_prediction/parsed_results/sp_af3_info.csv`
  - 能力：prediction_summaries
  - 用途：保存 SwissProt 组的 AlphaFold3 结果汇总
  - 复用状态：ready_for_review；类型：unknown
- `part3_gpc_testing/2_gpc_validation/scripts/run_pred_checks_traf.sh`
  - 能力：validation_scripts
  - 用途：运行测试/验证阶段的预测检查
  - 复用状态：ready_for_review；类型：code_entry
- `part3_gpc_testing/3_results_plotting/20260204_sum_preds_v1.ipynb`
  - 能力：results_plotting
  - 用途：汇总与可视化预测结果
  - 复用状态：ready_for_review；类型：unknown
- `supplementary/20260204_ptm_paeptm_v1.ipynb`
  - 能力：supplementary_analysis
  - 用途：补充分析 PTM/PAE/PTM 相关指标
  - 复用状态：ready_for_review；类型：unknown

### inference

- `nf_foldunfold/modules/colabfold/main.nf`
  - 能力：sequence_to_prediction_pipeline
  - 用途：封装 ColabFold 推理步骤
  - 复用状态：ready_for_review；类型：unknown
- `nf_foldunfold/modules/esmfold/main.nf`
  - 能力：sequence_to_prediction_pipeline
  - 用途：封装 ESMFold 推理步骤
  - 复用状态：ready_for_review；类型：unknown
- `part3_gpc_testing/1_gpc_run/scripts/afdb_search.py`
  - 能力：afdb_sequence_retrieval
  - 用途：从 AFDB 检索候选序列，支撑后续打分/验证
  - 复用状态：ready_for_review；类型：code_entry
- `part3_gpc_testing/1_gpc_run/scripts/process_preds.sh`
  - 能力：postprocess_predictions
  - 用途：整理与汇总预测输出
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/run_iupred.py`
  - 能力：structure_scoring
  - 用途：运行 IUPred 蛋白无序度评分，作为推理辅助特征
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `nf_foldunfold/main.nf`
  - 能力：structure_prediction_workflow
  - 用途：统一调度 AlphaFold3、ColabFold、ESMFold 的推理流程
  - 复用状态：ready_for_review；类型：unknown
- `nf_foldunfold/modules/alphafold3/main.nf`
  - 能力：structure_prediction_module
  - 用途：封装 AlphaFold3 结构预测步骤
  - 复用状态：ready_for_review；类型：unknown
- `nf_foldunfold/scripts/fasta2json.py`
  - 能力：utility_conversion
  - 用途：将 FASTA 输入转换为推理所需 JSON 结构
  - 复用状态：ready_for_review；类型：code_entry
- `part1_refoldunfold/1_sequence_selection/scripts/generate_controls.py`
  - 能力：sequence_selection
  - 用途：生成对照序列集合
  - 复用状态：ready_for_review；类型：code_entry
- `data/afdb_paes/scripts/parse_pae_json.py`
  - 能力：score_parsing
  - 用途：解析 AlphaFold DB 的 PAE JSON 结果
  - 复用状态：ready_for_review；类型：code_entry

### training

- `part2_gpc_training/3_train_test_gpc/20260204_gpc_dev_v2.ipynb`
  - 能力：gpc_training_notebook
  - 用途：GPC 开发、训练与测试的主要 notebook 入口
  - 复用状态：ready_for_review；类型：unknown
- `part2_gpc_training/1_sequence_selection/scripts/sample_swissprots.py`
  - 能力：training_sample_preparation
  - 用途：抽样 SwissProt 序列，构建训练/验证输入
  - 复用状态：ready_for_review；类型：code_entry
- `part2_gpc_training/1_sequence_selection/scripts/make_antifams_pt1.py`
  - 能力：training_sample_preparation
  - 用途：构建 pseudo-antifam 训练样本的一部分
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态盘点，未执行任何代码或 notebook。
- 依赖未安装，无法验证运行时输入输出。
- 未运行测试或 CI。
- 没有可见 checkpoint，无法核实模型权重/恢复点。
- 路径存在不等于数据来源、许可或可复现性已确认。

## 仍未知

- `data/taxonomy/taxonomy.txt`、`data/ref_prot/gen_af_proteomes.csv` 等辅助数据的原始来源与许可未能从清单中确认。
- `parsed_results/*.csv` 和结构预测汇总表是原始运行结果还是手工整理归档，静态清单无法区分。
- GPC notebook 内部是否包含最终实验设置、超参数与指标定义，当前未展开内容。
- 未见任何模型 checkpoint，因此训练产物是否另存于外部位置未知。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
