# AhmedESamy/dsgrl

- **仓库：** [https://github.com/AhmedESamy/dsgrl](https://github.com/AhmedESamy/dsgrl)
- **固定 commit：** `8f085283e434cf353b1159b0dd85d710d2700be4`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 21

## 仓库摘要

该仓库是一个图表示学习项目的静态冻结清单，能看到 node_classification 与 graph_property_pred 两套实现、数据加载/预处理、模型、增强、loss、工具函数和训练入口；同时未发现独立 LICENSE、原始数据、checkpoint、显式 inference 或 evaluation 入口，因此只能做静态盘点，不能证明可复现或可直接复用。

## 可复用模块与资源

### datasets

- `graph_property_pred/dataset/dataset.py`
  - 能力：graph_property_pred dataset loader
  - 用途：graph property prediction 的数据集读取与封装
  - 复用状态：blocked；类型：code_entry
- `graph_property_pred/dataset/dsutils.py`
  - 能力：graph_property_pred dataset utilities
  - 用途：数据集辅助函数与切分/采样支持
  - 复用状态：blocked；类型：code_entry
- `graph_property_pred/dataset/transforms.py`
  - 能力：graph_property_pred transforms
  - 用途：图数据预处理与变换
  - 复用状态：blocked；类型：code_entry
- `node_classification/datasets.py`
  - 能力：node_classification dataset loader
  - 用途：节点分类的数据集读取与封装
  - 复用状态：blocked；类型：code_entry
- `graph_property_pred/params/collab/feature.yaml`
  - 能力：graph_property_pred dataset configuration
  - 用途：collab/dd/enzymes/imdb-binary/imdb-multi/nci1/proteins/reddit-binary 等数据集的 feature/topology 配置
  - 复用状态：blocked；类型：config
- `node_classification/params/cs/feature_.yaml`
  - 能力：node_classification dataset configuration
  - 用途：cs/deezer/git/imdb/photo/pubmed/reddit/wikics/yelp 等数据集的 feature/topology 配置
  - 复用状态：blocked；类型：config

### reusable_assets

- `graph_property_pred/gnn.py`
  - 能力：graph_property_pred core GNN
  - 用途：graph property prediction 的图编码/骨干网络实现
  - 复用状态：blocked；类型：code_entry
- `graph_property_pred/model.py`
  - 能力：graph_property_pred model
  - 用途：graph property prediction 的主模型/任务头封装
  - 复用状态：blocked；类型：code_entry
- `graph_property_pred/augmentors.py`
  - 能力：graph_property_pred augmentation
  - 用途：图增强与视图构造
  - 复用状态：blocked；类型：code_entry
- `graph_property_pred/loss.py`
  - 能力：graph_property_pred loss
  - 用途：graph property prediction 的训练损失
  - 复用状态：blocked；类型：code_entry
- `graph_property_pred/utils.py`
  - 能力：graph_property_pred utils
  - 用途：训练与数据处理辅助函数
  - 复用状态：blocked；类型：code_entry
- `node_classification/gnn.py`
  - 能力：node_classification core GNN
  - 用途：节点分类的图编码/骨干网络实现
  - 复用状态：blocked；类型：code_entry
- `node_classification/hgnn.py`
  - 能力：node_classification HGNN
  - 用途：节点分类的 HGNN 变体/层次网络模块
  - 复用状态：blocked；类型：code_entry
- `node_classification/model.py`
  - 能力：node_classification model
  - 用途：节点分类的主模型/任务头封装
  - 复用状态：blocked；类型：code_entry
- `node_classification/augmentor.py`
  - 能力：node_classification augmentation
  - 用途：节点分类的图增强与扰动
  - 复用状态：blocked；类型：code_entry
- `node_classification/loss.py`
  - 能力：node_classification loss
  - 用途：节点分类的训练损失
  - 复用状态：blocked；类型：code_entry
- `node_classification/utils.py`
  - 能力：node_classification utils
  - 用途：训练与数据处理辅助函数
  - 复用状态：blocked；类型：code_entry

### training

- `graph_property_pred/train.py`
  - 能力：graph_property_pred training entrypoint
  - 用途：graph property prediction 的训练入口
  - 复用状态：blocked；类型：code_entry
- `graph_property_pred/main.py`
  - 能力：graph_property_pred launcher
  - 用途：graph property prediction 的命令行启动脚本
  - 复用状态：blocked；类型：code_entry
- `node_classification/main.py`
  - 能力：node_classification training entrypoint
  - 用途：节点分类的训练入口
  - 复用状态：blocked；类型：code_entry
- `node_classification/tune.py`
  - 能力：node_classification tuning
  - 用途：节点分类的超参搜索/调参脚本
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 静态盘点不等于真实执行，不能证明训练、评估或推理可复现
- 当前冻结清单未包含可识别的 checkpoint 文件
- .wandb/log 只能证明有实验产物痕迹，不能证明结果有效
- clone_depth=1 且 large blobs may be promisor-only，仍可能存在未取回资源

## 仍未知

- graph_property_pred/params 与 node_classification/params 可能只含超参数，也可能编码数据划分与预处理细节；仅凭路径无法区分
- tracked .wandb 运行记录是否对应成功完成的训练与最终指标，当前无法验证
- 仓库是否依赖未初始化的 submodule 或外部下载数据/模型，静态清单无法确认

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
