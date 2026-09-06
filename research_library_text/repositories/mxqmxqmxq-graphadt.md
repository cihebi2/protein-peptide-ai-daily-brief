# mxqmxqmxq/GraphADT

- **仓库：** [https://github.com/mxqmxqmxq/GraphADT](https://github.com/mxqmxqmxq/GraphADT)
- **固定 commit：** `dcf9ac4f23c851048081cc188bb0cbce25ae81ff`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 16

## 仓库摘要

GraphADT 仓库围绕急性皮肤毒性预测与可解释性展开，包含结构重映射、3D 分子特征化、MVPool 图模型、若干统计/热图分析脚本，以及 Rabbit/Rat 的内外部 CSV 数据；静态清单未见许可证、模型 checkpoint 或可验证的复现执行证据。

## 可复用模块与资源

### datasets

- `dataset/Rabbit.csv`
  - 能力：rabbit acute dermal toxicity dataset
  - 用途：仓库内置 Rabbit 任务数据，疑似用于训练或主实验划分
  - 复用状态：blocked；类型：unknown
- `dataset/Rabbit_external.csv`
  - 能力：rabbit external set
  - 用途：Rabbit 外部验证/测试数据
  - 复用状态：blocked；类型：unknown
- `dataset/Rat.csv`
  - 能力：rat acute dermal toxicity dataset
  - 用途：仓库内置 Rat 任务数据，疑似用于训练或主实验划分
  - 复用状态：blocked；类型：unknown
- `dataset/Rat_external.csv`
  - 能力：rat external set
  - 用途：Rat 外部验证/测试数据
  - 复用状态：blocked；类型：unknown

### evaluation

- `evalution.py`
  - 能力：evaluation / benchmarking script
  - 用途：评估模型表现、汇总指标或生成实验结果；文件名疑似 evaluation 的拼写变体
  - 复用状态：blocked；类型：code_entry
- `Graph_based_interpretability/statistic0.py`
  - 能力：post-hoc statistics / analysis
  - 用途：对解释结果或实验结果做统计分析
  - 复用状态：blocked；类型：code_entry
- `Graph_based_interpretability/statistic1.py`
  - 能力：post-hoc statistics / analysis
  - 用途：对解释结果或实验结果做统计分析
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `structuralremap_construction/data/bondgraph/to_bondgraph.py`
  - 能力：structural remapping / bond graph construction
  - 用途：把分子结构转换为 bond graph 或结构重映射表示，供后续图模型消费
  - 复用状态：blocked；类型：code_entry
- `structuralremap_construction/data/featurization/smiles_to_3d_mol.py`
  - 能力：SMILES to 3D molecule featurization
  - 用途：把 SMILES 转成 3D 分子表示，作为图/几何特征前处理
  - 复用状态：blocked；类型：code_entry
- `structuralremap_construction/data/featurization/mol_to_data.py`
  - 能力：molecule-to-data conversion
  - 用途：把 RDKit 分子对象整理成图学习所需的数据结构
  - 复用状态：blocked；类型：code_entry
- `models/model.py`
  - 能力：top-level model definition
  - 用途：组织 GraphADT 的主模型结构与前向计算逻辑
  - 复用状态：blocked；类型：code_entry
- `models/MVPool/layers.py`
  - 能力：MVPool layers and pooling operators
  - 用途：提供 multi-view graph pooling 的基础算子与层实现
  - 复用状态：blocked；类型：code_entry
- `Graph_based_interpretability/rdkit_heatmaps/heatmaps.py`
  - 能力：RDKit heatmap / interpretability utilities
  - 用途：生成分子可解释性热图或映射结果
  - 复用状态：blocked；类型：code_entry

### training

- `main.py`
  - 能力：experiment / training entry script
  - 用途：可能作为主实验脚本，承担训练流程、参数装配或运行入口
  - 复用状态：blocked；类型：code_entry
- `create_data.py`
  - 能力：dataset construction / preprocessing
  - 用途：构造数据集、划分样本或生成训练前中间文件
  - 复用状态：blocked；类型：code_entry
- `nt_xent.py`
  - 能力：contrastive loss component
  - 用途：为训练过程提供 NT-Xent 对比学习损失或相关优化目标
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审查，未运行代码、未安装依赖、未执行测试。
- 仓库未发现模型 checkpoint；两个 .pkl 更像中间数据，不应默认视为权重。
- 文件级路径存在不等于功能可用，main.py / evalution.py 的真实职责未被执行验证。
- 数据集 CSV 的来源与许可未被文件内容证实。

## 仍未知

- `Graph_based_interpretability/rdkit_heatmaps/*` 是否为项目自写还是 vendored 第三方实现无法仅凭路径确认。
- `main.py` 是否承担完整训练入口、推理入口或仅作实验驱动，静态目录证据不足。
- `dataset/*.csv` 的具体样本构成、标签定义和划分策略未读取。
- 无 checkpoint、无测试、无 CI，因而不能判断复现质量。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
