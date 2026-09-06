# Aalto-QuML/DiffAlign

- **仓库：** [https://github.com/Aalto-QuML/DiffAlign](https://github.com/Aalto-QuML/DiffAlign)
- **固定 commit：** `23676bca2066c02a255616a294023ec760d6f0f4`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 12

## 仓库摘要

从静态路径看，这个 DiffAlign 仓库主要提供图扩散建模、训练/采样/评估脚手架和 USPTO-50K 配置；未见 bundled data、checkpoint 或 LICENSE，因此只能判断代码与配置边界，不能视为可直接复用或已复现。

## 可复用模块与资源

### datasets

- `configs/dataset/uspto-50k.yaml`
  - 能力：USPTO-50K 配置
  - 用途：指定数据集/切分/预处理 recipe；仓库快照未见实际数据文件。
  - 复用状态：blocked；类型：config
- `diffalign/datasets/supernode_dataset.py`
  - 能力：图数据加载器
  - 用途：构造数据样本与超节点图输入。
  - 复用状态：blocked；类型：code_entry

### evaluation

- `scripts/evaluate.py`
  - 能力：评估入口与指标汇总
  - 用途：运行评估并汇总实验指标。
  - 复用状态：blocked；类型：code_entry
- `scripts/aggregate_scores.py`
  - 能力：结果聚合脚本
  - 用途：汇总多个采样/实验得分；静态存在不代表指标已计算。
  - 复用状态：blocked；类型：code_entry

### inference

- `scripts/sample.py`
  - 能力：采样/生成推理
  - 用途：从训练模型进行样本生成与推断。
  - 复用状态：blocked；类型：code_entry
- `api/predict.py`
  - 能力：API 预测接口
  - 用途：对外提供推理/预测封装。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `diffalign/model.py`
  - 能力：核心图扩散模型
  - 用途：组织 DiffAlign 主模型与扩散/对齐相关前向逻辑。
  - 复用状态：blocked；类型：code_entry
- `diffalign/neuralnet/transformer_model_with_y.py`
  - 能力：Transformer 表示学习骨干
  - 用途：提供带 y 条件/特征的 Transformer 实现。
  - 复用状态：blocked；类型：code_entry
- `diffalign/utils/graph_builder.py`
  - 能力：图/分子工具
  - 用途：图构建、分子结构与辅助数值/IO 工具。
  - 复用状态：blocked；类型：code_entry
- `diffalign/utils/orca/orca`
  - 能力：ORCA 辅助组件
  - 用途：编译后二进制及 C++ 源码辅助件；静态快照无法确认来源、编译方式和授权。
  - 复用状态：blocked；类型：unknown

### training

- `scripts/train.py`
  - 能力：训练入口
  - 用途：启动训练流程并组合配置、模型与数据加载器。
  - 复用状态：blocked；类型：code_entry
- `configs/trained_experiment/2709_marginal_product_and_sn_dummy15_loss_ce_smiles_pos_encnum_gpus_2-seed1.yaml`
  - 能力：冻结训练/调参配置
  - 用途：记录特定实验超参与损失设置；不是 checkpoint。
  - 复用状态：blocked；类型：config

## 使用限制

- 仅做静态盘点，未执行代码、未安装依赖、未运行测试。
- 仓库未见 bundled data 或 checkpoint；数据与权重不可由路径存在直接证明。
- 存在 promisor-only/大文件与未初始化子模块的风险，完整性无法仅凭清单确认。
- 路径存在不等于训练、推理或评估已可运行。
- 未发现显式许可文件，直接复用边界受限。

## 仍未知

- configs/dataset/uspto-50k.yaml 对应的真实数据源、下载方式和数据许可未在清单中确认。
- configs/trained_experiment/* 仅是训练配置名，未见对应权重文件，是否有公开 checkpoint 不明。
- diffalign/utils/orca/orca 是否为 vendored_third_party 及其许可证未确认。
- README.md 内容未被提供为可核验证据，无法据此确认作者声明的使用边界。
- tests/* 仅表明存在测试脚本，不代表测试通过或覆盖充分。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
