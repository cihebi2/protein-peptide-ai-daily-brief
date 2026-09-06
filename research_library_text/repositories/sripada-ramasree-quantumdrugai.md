# sripada-ramasree/quantumdrugai

- **仓库：** [https://github.com/sripada-ramasree/quantumdrugai](https://github.com/sripada-ramasree/quantumdrugai)
- **固定 commit：** `6d3937ffd4c234361991418dd3f582d65a914eb9`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 16

## 仓库摘要

这是一个面向分子性质预测与分子优化的量子-经典混合研究原型；静态库存显示主要可复用内容集中在模型、数据处理、训练和评估代码，但没有可识别的数据集、检查点或已确认许可证，直接复用边界仍受限。

## 可复用模块与资源

### evaluation

- `evaluation/metrics.py`
  - 能力：metrics
  - 用途：评估指标计算
  - 复用状态：blocked；类型：code_entry
- `evaluation/compare_models.py`
  - 能力：model_comparison
  - 用途：模型对比评估
  - 复用状态：blocked；类型：code_entry
- `evaluation/visualization.py`
  - 能力：visualization
  - 用途：结果可视化
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `main.py`
  - 能力：code_entry
  - 用途：项目主入口，编排训练、生成与评估流程
  - 复用状态：blocked；类型：code_entry
- `data/download_datasets.py`
  - 能力：data_acquisition
  - 用途：下载外部分子数据集的脚本
  - 复用状态：blocked；类型：code_entry
- `data/preprocess.py`
  - 能力：data_processing
  - 用途：数据清洗、拆分与预处理
  - 复用状态：blocked；类型：code_entry
- `data/molecular_features.py`
  - 能力：feature_engineering
  - 用途：分子特征构建与编码
  - 复用状态：blocked；类型：code_entry
- `models/classical_gnn.py`
  - 能力：classical_baseline_model
  - 用途：经典 GNN 分子建模基线
  - 复用状态：blocked；类型：code_entry
- `models/hybrid_qc_model.py`
  - 能力：hybrid_model
  - 用途：量子-经典混合分子建模主干
  - 复用状态：blocked；类型：code_entry
- `models/quantum_layer.py`
  - 能力：quantum_component
  - 用途：混合模型中的 quantum layer 组件
  - 复用状态：blocked；类型：code_entry
- `models/molecule_generator.py`
  - 能力：generator_model
  - 用途：分子生成与候选优化相关组件
  - 复用状态：blocked；类型：code_entry
- `explainability/atom_importance.py`
  - 能力：explainability
  - 用途：原子重要性解释模块
  - 复用状态：blocked；类型：code_entry
- `explainability/feature_attribution.py`
  - 能力：explainability
  - 用途：特征归因解释模块
  - 复用状态：blocked；类型：code_entry

### training

- `training/train_property_model.py`
  - 能力：property_model_training
  - 用途：训练分子性质预测模型
  - 复用状态：blocked；类型：code_entry
- `training/train_generator.py`
  - 能力：generator_training
  - 用途：训练分子生成器
  - 复用状态：blocked；类型：code_entry
- `training/optimize_molecules.py`
  - 能力：optimization_pipeline
  - 用途：分子优化与候选生成流程
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审计，未执行仓库代码。
- 未安装依赖，未运行 tests。
- 未发现可确认的 bundled data 或 checkpoint 资产。
- 路径存在不等于可复现执行。
- 代码许可证未被静态解析确认，直接复用受限。

## 仍未知

- data/download_datasets.py 实际会下载哪些外部数据集，冻结清单未给出数据明细。
- main.py 的具体运行模式（训练、生成还是评估编排）无法仅凭路径确认。
- 仓库是否存在未跟踪的大文件权重或额外模型资产，静态库存无法排除。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
