# dahuilangda/stapep_package

- **仓库：** [https://github.com/dahuilangda/stapep_package](https://github.com/dahuilangda/stapep_package)
- **固定 commit：** `dcbb648a017ab59028aa4b5a0af8e3093b166c71`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 27

## 仓库摘要

该仓库是 StaPep 工具包的静态库存，覆盖结构预测、模板生成、MD、特征提取与 permeability 预测示例；未发现 LICENSE，且仅能做静态盘点，无法证明可复现执行或授权复用。

## 可复用模块与资源

### checkpoints

- `stapep/models/lgb_model.sav`
  - 能力：LightGBM 序列化模型
  - 用途：permeability 分类/预测模型文件
  - 复用状态：unknown；类型：unknown
- `stapep/models/rf_cls_model.pkl`
  - 能力：RandomForest 序列化模型
  - 用途：permeability 分类器文件
  - 复用状态：unknown；类型：unknown

### datasets

- `stapep/example/data/template.pdb`
  - 能力：示例结构模板
  - 用途：示例输入结构模板
  - 复用状态：unknown；类型：unknown
- `stapep/example/datasets/Stapled-peptide_permeability.csv`
  - 能力：permeability 标注数据
  - 用途：用于 permeability 训练/预测示例的数据表
  - 复用状态：unknown；类型：unknown
- `stapep/example/datasets/Stapled-peptide_permeability_filtered.csv`
  - 能力：过滤后 permeability 数据
  - 用途：过滤后的样本子集
  - 复用状态：unknown；类型：unknown
- `stapep/example/datasets/RCSB-STAPED-PEP_RMSD.xlsx`
  - 能力：RMSD 评估表
  - 用途：结构/RMSD 统计与评估
  - 复用状态：unknown；类型：unknown
- `stapep/example/datasets/stapled-peptide-datasets_Peptide.xlsx`
  - 能力：peptide 示例数据
  - 用途：peptide 相关示例数据表
  - 复用状态：unknown；类型：unknown

### evaluation

- `stapep/example/img/ROC.png`
  - 能力：分类性能评估
  - 用途：ROC 曲线评估分类器表现
  - 复用状态：blocked；类型：unknown
- `stapep/example/img/Feature_importance.png`
  - 能力：特征重要性分析
  - 用途：特征重要性可视化
  - 复用状态：blocked；类型：unknown
- `stapep/example/img/Feature_distrbution.png`
  - 能力：特征分布分析
  - 用途：特征分布可视化
  - 复用状态：blocked；类型：unknown
- `stapep/example/img/Permeability_distrbution.png`
  - 能力：permeability 分布对比
  - 用途：目标标签分布/对比图
  - 复用状态：blocked；类型：unknown
- `stapep/example/img/Lyticity_index.png`
  - 能力：lyticity 指标分析
  - 用途：lyticity index 相关分析图
  - 复用状态：blocked；类型：unknown
- `stapep/example/ex3.2_machine_learning_predictor_for_permeability.ipynb`
  - 能力：Notebook 评估示例
  - 用途：预测器演示与结果展示
  - 复用状态：blocked；类型：unknown

### inference

- `stapep/esmfold.py`
  - 能力：结构预测推理
  - 用途：结构预测推理封装
  - 复用状态：blocked；类型：code_entry
- `stapep/generate_template.py`
  - 能力：模板生成推理
  - 用途：标准模板生成
  - 复用状态：blocked；类型：code_entry
- `stapep/generate_covalent_template.py`
  - 能力：共价模板生成推理
  - 用途：共价 stapled 模板生成
  - 复用状态：blocked；类型：code_entry
- `stapep/run_pipeline.py`
  - 能力：端到端 pipeline 推理
  - 用途：把结构预测、特征提取与预测串成单次流程
  - 复用状态：blocked；类型：code_entry
- `stapep/example/ex3.2_machine_learning_predictor_for_permeability.ipynb`
  - 能力：Notebook 推理示例
  - 用途：permeability 预测演示与示例推理
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `stapep/esmfold.py`
  - 能力：结构预测封装
  - 用途：封装/调用结构预测流程，为 stapled peptide 生成结构结果
  - 复用状态：blocked；类型：code_entry
- `stapep/generate_template.py`
  - 能力：标准模板生成
  - 用途：为 peptide/残基生成模板文件
  - 复用状态：blocked；类型：code_entry
- `stapep/generate_covalent_template.py`
  - 能力：共价 stapled 模板生成
  - 用途：生成交联/共价 stapled peptide 的模板
  - 复用状态：blocked；类型：code_entry
- `stapep/molecular_dynamics.py`
  - 能力：分子动力学流程
  - 用途：运行/整理 MD 相关流程与分析
  - 复用状态：blocked；类型：code_entry
- `stapep/filter.py`
  - 能力：筛选与辅助函数
  - 用途：对候选/数据进行筛选
  - 复用状态：blocked；类型：code_entry
- `stapep/run_pipeline.py`
  - 能力：端到端流水线编排
  - 用途：串联结构预测、特征提取与推理
  - 复用状态：blocked；类型：code_entry
- `stapep/utils.py`
  - 能力：通用工具函数
  - 用途：提供包内通用辅助逻辑
  - 复用状态：blocked；类型：code_entry
- `stapep/templates/AIB/aib.prepin`
  - 能力：非标准残基参数模板
  - 用途：AIB/NLE/PR3/PR5/PR8/PS3/PS5/PS8 等非标准氨基酸参数与拓扑模板
  - 复用状态：blocked；类型：unknown

### training

- `stapep/example/ex3.1_machine_learning_training_for_permeability.ipynb`
  - 能力：permeability 模型训练
  - 用途：机器学习训练示例；仓库中未见独立训练入口模块
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态盘点，未执行仓库代码
- dependencies 未安装，无法验证 import 或环境要求
- tests/CI 未见且未运行
- 无 LICENSE 文件，直接复用边界不清
- build/dist 产物与源码并存，可能只是打包副本而非独立贡献

## 仍未知

- `lgb_model.sav` 与 `rf_cls_model.pkl` 是否为仓库内训练产物无法从静态库存确认
- CSV/XLSX 示例数据的原始来源、标注流程与数据许可未知
- notebook 的实际 cell 内容与运行结果未验证
- `build/lib/...` 目录是构建副本还是额外维护的源码镜像无法确认
- 仓库是否可在现有依赖下成功安装和运行未知

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
