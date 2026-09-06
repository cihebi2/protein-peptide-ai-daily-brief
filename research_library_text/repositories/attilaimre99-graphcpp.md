# attilaimre99/graphcpp

- **仓库：** [https://github.com/attilaimre99/graphcpp](https://github.com/attilaimre99/graphcpp)
- **固定 commit：** `628c4fb9b9fc345f37bc2844ea2ed63efef6eea8`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 19

## 仓库摘要

该仓库是 GraphCPP 的静态实现包，核心为 GNN 预测模型与数据加载器，配套 4 个 CSV 数据集、1 个 checkpoint 和若干配置/分析脚本；未见 LICENSE，代码直接复用受限。

## 可复用模块与资源

### checkpoints

- `model/checkpoints/epoch=22-step=69.ckpt`
  - 能力：模型权重
  - 用途：训练后 checkpoint，可用于加载已训练参数。
  - 复用状态：unknown；类型：model_weight

### datasets

- `dataset/mlcpp2_independent.csv`
  - 能力：独立评估数据
  - 用途：独立测试/外部评估 CSV。
  - 复用状态：unknown；类型：unknown
- `dataset/raw/2024-07-14-15-40-08/train.csv`
  - 能力：训练集
  - 用途：训练数据 CSV。
  - 复用状态：unknown；类型：unknown
- `dataset/raw/2024-07-14-15-40-08/val.csv`
  - 能力：验证集
  - 用途：验证数据 CSV。
  - 复用状态：unknown；类型：unknown
- `dataset/raw/2024-07-14-15-40-08/test.csv`
  - 能力：测试集
  - 用途：测试数据 CSV。
  - 复用状态：unknown；类型：unknown

### evaluation

- `cv.py`
  - 能力：交叉验证辅助
  - 用途：从文件名看是交叉验证/性能统计脚本；未执行，无法确认实现细节。
  - 复用状态：unknown；类型：code_entry
- `notebooks/analyse_hp_search_metrics.ipynb`
  - 能力：超参数搜索分析
  - 用途：分析超参数搜索指标的 notebook，属于评估/分析辅助。
  - 复用状态：unknown；类型：unknown

### inference

- `predict.yml`
  - 能力：预测配置
  - 用途：预测/推理阶段的配置入口候选。
  - 复用状态：unknown；类型：config
- `uncertainty.py`
  - 能力：不确定性后处理
  - 用途：推断后不确定性估计或筛选辅助脚本候选。
  - 复用状态：unknown；类型：code_entry

### reusable_assets

- `graphcpp/model.py`
  - 能力：模型主干
  - 用途：GraphCPP 核心图神经网络模型定义。
  - 复用状态：blocked；类型：code_entry
- `graphcpp/dataset.py`
  - 能力：数据加载器
  - 用途：CSV 样本读取、划分与前处理逻辑。
  - 复用状态：blocked；类型：code_entry
- `graphcpp/generalconv.py`
  - 能力：消息传递/卷积算子
  - 用途：自定义 GNN 卷积层实现。
  - 复用状态：blocked；类型：code_entry
- `graphcpp/pooling.py`
  - 能力：图池化
  - 用途：图级读出/池化模块。
  - 复用状态：blocked；类型：code_entry
- `graphcpp/act.py`
  - 能力：激活函数封装
  - 用途：非线性激活辅助层。
  - 复用状态：blocked；类型：code_entry
- `graphcpp/fp_generators.py`
  - 能力：特征生成
  - 用途：指纹或特征生成辅助模块。
  - 复用状态：blocked；类型：code_entry
- `graphcpp/model_for_tsne.py`
  - 能力：表示分析
  - 用途：t-SNE/嵌入可视化相关模型变体。
  - 复用状态：blocked；类型：code_entry
- `main.py`
  - 能力：代码入口候选
  - 用途：仓库级入口脚本；静态清单无法区分其是训练还是推理入口。
  - 复用状态：blocked；类型：code_entry

### training

- `model/hparams.yaml`
  - 能力：训练超参数配置
  - 用途：训练配方与超参数设置。
  - 复用状态：unknown；类型：config
- `environment.yml`
  - 能力：运行环境配置
  - 用途：依赖环境定义，便于复现实验环境。
  - 复用状态：unknown；类型：config

## 使用限制

- 仅做静态审查，未运行代码。
- 依赖未安装，无法验证导入、训练或推理是否可用。
- 仓库未见 LICENSE，代码直接复用受阻。
- large_blobs_over_5MiB_may_be_promisor_only，因此 checkpoint 与部分大文件仅能视为存在。
- 路径存在不等于可复现、可训练或可推理。

## 仍未知

- `main.py`、`predict.yml`、`uncertainty.py`、`cv.py` 的具体职责仅能从文件名推断。
- `dataset/mlcpp2_independent.csv` 与 raw CSV 的来源、标签定义、切分规则未知。
- `model/checkpoints/epoch=22-step=69.ckpt` 的训练数据、验证指标与保存条件未知。
- `graphcpp/model.py` 的具体层次、损失函数与超参数未核实。
- 数据集与 checkpoint 的独立许可状态未知。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
