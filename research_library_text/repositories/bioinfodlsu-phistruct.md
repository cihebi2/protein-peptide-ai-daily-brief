# bioinfodlsu/phistruct

- **仓库：** [https://github.com/bioinfodlsu/phistruct](https://github.com/bioinfodlsu/phistruct)
- **固定 commit：** `77e5753c62d17b4f21cdbf9200008143aebf6551`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 37

## 仓库摘要

仓库是 PHIStruct 的静态代码与实验快照，覆盖序列/结构预处理、RBP 预筛、多个 embedding/classifier 基线、离线评测与示例推理；未见独立 checkpoint，数据与模型边界需逐项核验。

## 可复用模块与资源

### datasets

- `experiments/data/3Oct2023_data_excluding_refseq.tsv`
  - 能力：main curated dataset
  - 用途：主训练/评测数据表
  - 复用状态：partial；类型：unknown
- `experiments/temp/preprocessing/inphared.csv`
  - 能力：preprocessing source snapshot
  - 用途：预处理阶段的外部/中间来源表
  - 复用状态：partial；类型：unknown
- `experiments/temp/preprocessing/rbp_products.pickle`
  - 能力：cached product annotations
  - 用途：产品注释与筛选缓存
  - 复用状态：partial；类型：unknown
- `experiments/temp/eda/plddt.pickle`
  - 能力：structure confidence cache
  - 用途：pLDDT 统计与结构质量分析缓存
  - 复用状态：partial；类型：unknown

### evaluation

- `experiments/5.0. Classifier Building & Evaluation (SaProt).ipynb`
  - 能力：SaProt benchmark evaluation
  - 用途：SaProt 分类器构建与评测
  - 复用状态：partial；类型：unknown
- `experiments/5.3. Benchmarking - Classifier Building & Evaluation (ESM-1b).ipynb`
  - 能力：ESM-1b benchmark evaluation
  - 用途：ESM-1b 对照实验
  - 复用状态：partial；类型：unknown
- `experiments/5.4. Benchmarking - Classifier Building & Evaluation (ESM-2).ipynb`
  - 能力：ESM-2 benchmark evaluation
  - 用途：ESM-2 对照实验
  - 复用状态：partial；类型：unknown
- `experiments/5.5. Benchmarking - Classifier Building & Evaluation (ProtT5).ipynb`
  - 能力：ProtT5 benchmark evaluation
  - 用途：ProtT5 对照实验
  - 复用状态：partial；类型：unknown
- `experiments/5.10. Benchmarking - Classifier Building & Evaluation (SeqVec).ipynb`
  - 能力：SeqVec benchmark evaluation
  - 用途：SeqVec 对照实验
  - 复用状态：partial；类型：unknown
- `experiments/5.11. Benchmarking - Classifier Building & Evaluation (Random Forest).ipynb`
  - 能力：classical ML benchmark evaluation
  - 用途：Random Forest 对照实验
  - 复用状态：partial；类型：unknown
- `experiments/5.12. Benchmarking - Classifier Building & Evaluation (SVM).ipynb`
  - 能力：classical ML benchmark evaluation
  - 用途：SVM 对照实验
  - 复用状态：partial；类型：unknown
- `experiments/6.0. Comparison.ipynb`
  - 能力：comparison and plotting
  - 用途：汇总各模型比较结果
  - 复用状态：partial；类型：unknown
- `experiments/6.1. Plotting - F1.ipynb`
  - 能力：metric plotting
  - 用途：F1 可视化
  - 复用状态：partial；类型：unknown
- `experiments/6.2. Plotting - PR Curve.ipynb`
  - 能力：metric plotting
  - 用途：PR 曲线可视化
  - 复用状态：partial；类型：unknown
- `experiments/6.3. Confusion Matrix.ipynb`
  - 能力：error analysis
  - 用途：混淆矩阵与错误分析
  - 复用状态：partial；类型：unknown
- `figure.png`
  - 能力：evaluation figure
  - 用途：论文/报告中的汇总图
  - 复用状态：partial；类型：unknown
- `experiments/temp/results/saprot_relaxed_r3-mlp-eskapee-smotetomek-100.pickle`
  - 能力：evaluation output cache
  - 用途：保存 SaProt+MLP 的离线评测结果
  - 复用状态：partial；类型：unknown
- `experiments/temp/results/esm2-mlp-eskapee-smotetomek-100.pickle`
  - 能力：evaluation output cache
  - 用途：保存 ESM-2+MLP 的离线评测结果
  - 复用状态：partial；类型：unknown
- `experiments/temp/results/psiblast-eskapee-smotetomek-100.pickle`
  - 能力：baseline evaluation output cache
  - 用途：保存 PSI-BLAST 基线结果
  - 复用状态：partial；类型：unknown

### inference

- `phistruct.py`
  - 能力：inference entrypoint
  - 用途：对新序列/结构执行预测
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/RBPPredictionUtil.py`
  - 能力：RBP auxiliary inference
  - 用途：调用 RBP 预筛与结果整合
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/rbp_prediction/RBPdetect_xgb_model.json`
  - 能力：RBP prefilter model
  - 用途：推理阶段的 XGBoost 预筛权重
  - 复用状态：partial；类型：config
- `sample_pdb/ADG36134.1.pdb`
  - 能力：example input structure
  - 用途：示例推理输入 PDB
  - 复用状态：partial；类型：unknown
- `sample_results/ADG36134.1.csv`
  - 能力：example prediction output
  - 用途：示例推理结果 CSV
  - 复用状态：partial；类型：unknown

### reusable_assets

- `train.py`
  - 能力：phage-host interaction training
  - 用途：训练入口，组织数据、特征与分类器训练流程
  - 复用状态：ready_for_review；类型：code_entry
- `phistruct.py`
  - 能力：phage-host interaction inference
  - 用途：推理入口，用于对样本序列/结构做预测
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/MLPDropout.py`
  - 能力：classifier implementation
  - 用途：定义带 dropout 的 MLP 分类器
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/SequenceParsingUtil.py`
  - 能力：sequence parsing and cleaning
  - 用途：序列解析、清洗与格式转换
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/StructureUtil.py`
  - 能力：structure-aware feature handling
  - 用途：处理结构相关输入与结构特征
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/RBPPredictionUtil.py`
  - 能力：auxiliary RBP prediction utilities
  - 用途：RBPdetect/XGBoost 预筛与辅助调用
  - 复用状态：ready_for_review；类型：code_entry
- `environment_experiments.yaml`
  - 能力：training environment recipe
  - 用途：训练与实验依赖配置
  - 复用状态：partial；类型：config
- `experiments/rbp_prediction/RBPdetect_xgb_model.json`
  - 能力：RBP prefilter model
  - 用途：XGBoost 模型权重/序列级预筛
  - 复用状态：partial；类型：config

### training

- `train.py`
  - 能力：training entrypoint
  - 用途：组织训练流程并驱动模型拟合
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/1. Sequence Preprocessing.ipynb`
  - 能力：sequence preprocessing recipe
  - 用途：生成训练前的序列清洗、切分与过滤流程
  - 复用状态：partial；类型：unknown
- `experiments/3.0. Data Consolidation (SaProt).ipynb`
  - 能力：SaProt data consolidation recipe
  - 用途：SaProt 特征整理与样本汇总
  - 复用状态：partial；类型：unknown
- `experiments/3.6. Data Consolidation (ProstT5 - 3Di Tokens).ipynb`
  - 能力：ProstT5 3Di consolidation recipe
  - 用途：结构 token 的数据整理流程
  - 复用状态：partial；类型：unknown
- `environment.yaml`
  - 能力：training dependency recipe
  - 用途：基础训练环境与依赖锁定
  - 复用状态：partial；类型：config

## 使用限制

- 仅做静态审查，未执行代码或测试
- 依赖未安装，notebooks 未运行
- 仓库内 serialized 文件只能证明存在，不能证明可复现
- 未见独立 checkpoint 文件
- 大文件可能仅为 promisor/blob 占位，内容未核实
- 数据与模型来源、权属和再许可边界未完全确认

## 仍未知

- `experiments/rbp_prediction/RBPdetect_xgb_model.json` 是否为项目自训还是外部 vendored 模型未证实
- `experiments/temp/results/*.pickle` 内部是指标、预测还是模型对象未证实
- `sample_pdb/*.pdb` 与 `sample_results/*.csv` 是否为项目自生成示例未证实
- `experiments/data/3Oct2023_data_excluding_refseq.tsv` 的上游数据许可未证实

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
