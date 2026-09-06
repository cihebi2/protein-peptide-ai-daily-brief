# janecai0714/AMP_regression_EC_SA

- **仓库：** [https://github.com/janecai0714/AMP_regression_EC_SA](https://github.com/janecai0714/AMP_regression_EC_SA)
- **固定 commit：** `a2d05054b0c6cd049f6bc0b20253289c507df77e`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 17

## 仓库摘要

该仓库静态上是一个面向 EC/SA 抗菌肽 MIC 回归的实现包，包含 BERT 微调模型、传统特征工程与训练/测试脚本、推理脚本，以及成组 CSV 数据和实验结果；未见 checkpoint，且未发现 LICENSE 文件，因此复用边界仍需谨慎。[repo:https://github.com/janecai0714/AMP_regression_EC_SA@a2d05054b0c6cd049f6bc0b20253289c507df77e, path:EC/bert_finetune/model_def.py]

## 可复用模块与资源

### datasets

- `EC/data/EC.csv`
  - 能力：EC MIC regression dataset bundle
  - 用途：EC 抗菌肽 MIC 数据及其训练/测试拆分
  - 复用状态：blocked；类型：unknown
- `data/SA.csv`
  - 能力：SA MIC regression dataset bundle
  - 用途：SA 抗菌肽 MIC 数据及其训练/测试拆分
  - 复用状态：blocked；类型：unknown
- `predict/train_po.csv`
  - 能力：prediction input bundle
  - 用途：推理阶段的待预测序列输入或示例输入
  - 复用状态：blocked；类型：unknown

### evaluation

- `results_analysis_R_scripts/EC/result/ec_finetune_result.csv`
  - 能力：EC result tables
  - 用途：EC 实验指标与汇总结果的静态记录
  - 复用状态：blocked；类型：unknown
- `results_analysis_R_scripts/SA/result/sa_finetune_result.csv`
  - 能力：SA result tables
  - 用途：SA 实验指标与汇总结果的静态记录
  - 复用状态：blocked；类型：unknown
- `results_analysis_R_scripts/vis/ablation_study.csv`
  - 能力：ablation and visualization tables
  - 用途：可视化、ablation 和训练比例统计表
  - 复用状态：blocked；类型：unknown

### inference

- `predict/model_def.py`
  - 能力：sequence inference pipeline
  - 用途：读取序列、组装推理数据并输出预测值
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `EC/bert_finetune/model_def.py`
  - 能力：BERT fine-tuning model definition (EC)
  - 用途：定义 EC 回归模型结构，支撑微调实现
  - 复用状态：blocked；类型：code_entry
- `SA/bert_finetune/model_def.py`
  - 能力：BERT fine-tuning model definition (SA)
  - 用途：定义 SA 回归模型结构，支撑微调实现
  - 复用状态：blocked；类型：code_entry
- `predict/model_def.py`
  - 能力：prediction pipeline
  - 用途：加载序列、组装推理输入并输出预测值
  - 复用状态：blocked；类型：code_entry
- `EC/ml_base/ifeature/codes/AAC.py`
  - 能力：classical feature engineering code family
  - 用途：蛋白序列特征编码与分析，覆盖 AAC、PSSM、聚类/降维等辅助流程
  - 复用状态：blocked；类型：code_entry
- `EC/bert_finetune/train_test.py`
  - 能力：training/test harness
  - 用途：执行 BERT 微调与传统 ML 的训练/测试流程
  - 复用状态：blocked；类型：code_entry
- `results_analysis_R_scripts/vis/result.Rmd`
  - 能力：analysis and visualization
  - 用途：汇总训练比例、ablation 与结果图表，属于后处理分析资产
  - 复用状态：blocked；类型：unknown
- `requirements.txt`
  - 能力：dependency specification
  - 用途：记录 Python 依赖，辅助环境重建
  - 复用状态：blocked；类型：unknown

### training

- `EC/bert_finetune/train_test.py`
  - 能力：BERT fine-tuning training/test
  - 用途：BERT 微调回归的训练与测试主流程
  - 复用状态：blocked；类型：code_entry
- `EC/ml_base/ml_train_test.py`
  - 能力：classical ML training/test
  - 用途：传统机器学习特征与模型的训练/测试流程
  - 复用状态：blocked；类型：code_entry
- `results_analysis_R_scripts/vis/train_frac_ec_sa.py`
  - 能力：training-fraction analysis
  - 用途：训练比例敏感性分析与绘图，不是主训练入口
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审计，未运行任何代码、未安装依赖、未执行测试。
- 没有发现 checkpoint，无法静态证实可直接加载的训练权重。
- 仓库缺少顶层统一训练入口或明确 config recipe，复现路径需要逐个脚本推断。
- 结果 CSV/PNG 只是静态产物，不能证明训练或评估已经成功复现。
- 未发现 LICENSE 文件，直接复用存在明显许可阻断。

## 仍未知

- `EC/data/EC.csv` 与 `data/EC.csv` 是否为重复副本、镜像或不同版本，静态清单无法判定。
- `EC/ml_base/ifeature/` 下大量特征代码的 provenance 不明，可能是项目自有实现，也可能改写自外部资源。
- `predict/train_po.csv` 与 `predict/train_po.fasta` 更像推理输入，但其是否只是示例数据、测试集或另有训练用途无法确认。
- `results_analysis_R_scripts/*/result/*.csv` 是真实实验输出还是示例/占位文件，静态存在性无法验证。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
