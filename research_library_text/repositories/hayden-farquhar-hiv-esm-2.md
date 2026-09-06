# hayden-farquhar/hiv-esm-2

- **仓库：** [https://github.com/hayden-farquhar/hiv-esm-2](https://github.com/hayden-farquhar/hiv-esm-2)
- **固定 commit：** `ff32da16ae2ddbd696adb753bafd36cf2f33026b`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 19

## 仓库摘要

仓库以 notebook 驱动的 HIV drug resistance 预测与解释分析为主，含数据处理、模型定义、特征工程、评估和外部验证；冻结清单未见 bundled data、checkpoint 或独立 inference 入口。

## 可复用模块与资源

### evaluation

- `src/evaluation.py`
  - 能力：evaluation_metrics
  - 用途：评估指标、打分与验证逻辑；artifact_kind=code_entry
  - 复用状态：ready_for_review；类型：code_entry
- `notebooks/04_classification_evaluation.ipynb`
  - 能力：classification_evaluation
  - 用途：分类评估 notebook；artifact_kind=code_entry
  - 复用状态：partial；类型：unknown
- `notebooks/06_external_validation.ipynb`
  - 能力：external_validation
  - 用途：外部验证流程；artifact_kind=code_entry
  - 复用状态：partial；类型：unknown
- `notebooks/08_figures_and_statistics.ipynb`
  - 能力：figures_and_statistics
  - 用途：统计汇总与图表生成；artifact_kind=code_entry
  - 复用状态：partial；类型：unknown

### reusable_assets

- `src/data_processing.py`
  - 能力：data_loader
  - 用途：HIV 数据读取、清洗与特征准备；artifact_kind=code_entry
  - 复用状态：partial；类型：code_entry
- `src/models.py`
  - 能力：model_architecture
  - 用途：分类模型与基线模型定义；artifact_kind=code_entry
  - 复用状态：ready_for_review；类型：code_entry
- `src/feature_engineering.py`
  - 能力：feature_engineering
  - 用途：特征工程与表示构造；artifact_kind=code_entry
  - 复用状态：ready_for_review；类型：code_entry
- `src/interpretability.py`
  - 能力：interpretability
  - 用途：attention/可解释性分析；artifact_kind=code_entry
  - 复用状态：ready_for_review；类型：code_entry
- `src/plm_comparison.py`
  - 能力：plm_comparison
  - 用途：多 PLM 对照与基线比较；artifact_kind=code_entry
  - 复用状态：ready_for_review；类型：code_entry
- `src/statistical_tests.py`
  - 能力：statistical_testing
  - 用途：统计检验与显著性分析；artifact_kind=code_entry
  - 复用状态：ready_for_review；类型：code_entry
- `src/subtype_analysis.py`
  - 能力：subtype_analysis
  - 用途：HIV subtype 分析；artifact_kind=code_entry
  - 复用状态：ready_for_review；类型：code_entry
- `src/visualization.py`
  - 能力：visualization
  - 用途：图表与结果可视化；artifact_kind=code_entry
  - 复用状态：ready_for_review；类型：code_entry
- `notebooks/01_data_acquisition.ipynb`
  - 能力：data_acquisition
  - 用途：外部 HIV 数据集获取/整理流程；artifact_kind=code_entry
  - 复用状态：partial；类型：unknown
- `environment.yml`
  - 能力：config
  - 用途：Conda 环境定义；artifact_kind=config
  - 复用状态：partial；类型：config
- `requirements.txt`
  - 能力：config
  - 用途：Python 依赖清单；artifact_kind=config
  - 复用状态：partial；类型：unknown

### training

- `notebooks/02_baseline_development.ipynb`
  - 能力：baseline_training
  - 用途：基线模型开发与训练流程；artifact_kind=code_entry
  - 复用状态：partial；类型：unknown
- `notebooks/03_esm2_embedding_extraction.ipynb`
  - 能力：embedding_extraction
  - 用途：ESM-2 embedding 提取与特征预计算；artifact_kind=code_entry
  - 复用状态：partial；类型：unknown
- `notebooks/07_multi_plm_and_robustness.ipynb`
  - 能力：robustness_experiment
  - 用途：多 PLM 与鲁棒性实验；artifact_kind=code_entry
  - 复用状态：partial；类型：unknown
- `notebooks/07_multi_plm_and_robustness_colab.ipynb`
  - 能力：robustness_experiment
  - 用途：Colab 版多 PLM 与鲁棒性实验；artifact_kind=code_entry
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态盘点，未安装依赖、未运行脚本或 notebook。
- 未见 tracked checkpoint/权重文件，无法验证训练产物或直接推理能力。
- 未见 bundled data，外部 HIV 数据来源与许可未在冻结清单中确认。
- 主要流程以 notebook 组织，自动化复用程度未通过执行验证。

## 仍未知

- 各 notebook 内部单元与数据依赖未逐页读取，是否可无交互运行不明。
- `data/README.md`、`docs/METHODS.md` 的具体内容未展开，数据与方法说明仍有空白。
- `results/revision/subtype_assignments.csv` 更像派生结果文件，其是否作为可重用输入数据不明确。
- 外部数据集与预训练 ESM-2 权重的版本和许可边界未在冻结清单中确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
