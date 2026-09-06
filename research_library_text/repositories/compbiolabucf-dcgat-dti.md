# compbiolabucf/dcgat-dti

- **仓库：** [https://github.com/compbiolabucf/dcgat-dti](https://github.com/compbiolabucf/dcgat-dti)
- **固定 commit：** `0df8f7beab9c8afc46c18bdcd6adedce7bcbc3bf`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 12

## 仓库摘要

该冻结快照主要是一个用于 DTI 预测的静态训练/预处理仓库：包含 GAT/MLP/跨图注意力模型、数据加载与预处理、以及多数据集与多划分的配置，但没有 tracked 原始数据、checkpoint 或明确 LICENSE。

## 可复用模块与资源

### datasets

- `configs/preprocess/bindingDB.yaml`
  - 能力：dataset: BindingDB 预处理与加载
  - 用途：定义 BindingDB 的清洗、数据模块与训练输入
  - 复用状态：blocked；类型：config
- `configs/preprocess/drugbank.yaml`
  - 能力：dataset: DrugBank 预处理与加载
  - 用途：定义 DrugBank 的清洗、数据模块与训练输入
  - 复用状态：blocked；类型：config
- `configs/preprocess/luo.yaml`
  - 能力：dataset: Luo 预处理与加载
  - 用途：定义 Luo benchmark 的清洗、数据模块与训练输入
  - 复用状态：blocked；类型：config
- `configs/preprocess/yamanishi.yaml`
  - 能力：dataset: Yamanishi 预处理与加载
  - 用途：定义 Yamanishi benchmark 的清洗、数据模块与训练输入
  - 复用状态：blocked；类型：config

### evaluation

- `configs/best_params/random_balanced.yaml`
  - 能力：evaluation_recipes: split / best_params / tuning 配置
  - 用途：记录 cold-start / random / benchmark 划分下的参数选择与调优 recipe
  - 复用状态：blocked；类型：config

### inference

- `module/GAT.py`
  - 能力：prediction_forward_path: 模型前向推断代码
  - 用途：提供 DTI 预测所需的前向计算；未发现独立 inference 脚本
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `run.py`
  - 能力：code_entry: 主训练启动入口
  - 用途：串联模型、数据模块与配置，作为仓库的主要启动脚本
  - 复用状态：blocked；类型：code_entry
- `module/GAT.py`
  - 能力：model_code: GAT / MLP / cross-graph attention
  - 用途：实现主要 DTI 预测网络及其变体
  - 复用状态：blocked；类型：code_entry
- `datamodule/dataloader.py`
  - 能力：data_pipeline: dataloader 与通用预处理
  - 用途：组织输入样本、划分与批次构造，支撑四套 benchmark 数据流程
  - 复用状态：blocked；类型：code_entry
- `module/featurizer/drug_featurizer/chembert_featurizer.py`
  - 能力：feature_extraction: drug / protein featurizers
  - 用途：封装分子与蛋白特征读取/转换，面向下游 DTI 预测
  - 复用状态：blocked；类型：code_entry

### training

- `run.py`
  - 能力：training_entrypoint: 训练主程序
  - 用途：启动训练流程、读取配置并连接模型与 datamodule
  - 复用状态：blocked；类型：code_entry
- `configs/bindingDB_train_GAT.yaml`
  - 能力：training_recipes: 数据集/模型训练配置
  - 用途：定义不同数据集与模型变体的训练超参数和默认设置
  - 复用状态：blocked；类型：config

## 使用限制

- 仅做静态盘点，未执行代码或测试。
- tracked 快照中没有 raw data / checkpoint。
- 未发现独立 inference 或 evaluation 可执行脚本；相关能力主要体现在配置与模型模块中。
- 依赖环境存在，但未安装和验证。

## 仍未知

- README 的运行说明和实验结果未读，无法确认默认命令与指标细节。
- ESM / ChemBERT 相关特征器是否在运行时下载外部权重未能从冻结清单确认。
- 是否存在未跟踪的权重、数据或导出推断产物未知。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
