# arontier/igpose

- **仓库：** [https://github.com/arontier/igpose](https://github.com/arontier/igpose)
- **固定 commit：** `caa585f030a60b28cdefe84e18850af8695e6780`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** found
- **资产记录数：** 12

## 仓库摘要

该仓库是 IgPose 的冻结实现，静态清单中可见模型架构、数据加载与样本封装、图/embedding 预处理、推理脚本、训练脚本和一个部署用 checkpoint；未见 bundled data、独立 evaluation 入口或 tests/CI。LICENSE 文件存在，但 SPDX 未解析，代码、checkpoint 与任何外部数据的复用边界需要分别核对，且未执行运行时验证。

## 可复用模块与资源

### checkpoints

- `checkpoints/deploy_models.tar.gz`
  - 能力：部署模型权重归档
  - 用途：推理或部署时加载的模型参数包
  - 复用状态：partial；类型：unknown

### inference

- `src/predict.py`
  - 能力：推理主入口
  - 用途：加载模型并输出预测结果的主入口
  - 复用状态：partial；类型：code_entry
- `scripts/generate_graphs/crossdock/generate_graph_slurm_nb_pmhc.sh`
  - 能力：CrossDock 图生成批处理
  - 用途：为 CrossDock 数据准备图结构或推理前处理
  - 复用状态：partial；类型：code_entry
- `scripts/generate_graphs/crossdock/generate_graph_slurm_tcr_agnb.sh`
  - 能力：CrossDock 图生成批处理
  - 用途：为 CrossDock 数据准备图结构或推理前处理
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `src/models/abepitope.py`
  - 能力：模型架构与集成
  - 用途：实现 IgPose 的核心建模、图网络变体与 ensemble 组合
  - 复用状态：partial；类型：code_entry
- `src/common/dataset_utils.py`
  - 能力：数据加载与样本封装
  - 用途：数据读取、划分或样本对象封装的公共层
  - 复用状态：partial；类型：code_entry
- `src/graph_gen/generate_esmif_embeds.py`
  - 能力：图生成与 embedding 预处理
  - 用途：生成 ESMIF embeddings，供后续图建模或推理使用
  - 复用状态：partial；类型：code_entry
- `configs/inference_classification.yaml`
  - 能力：推理配置
  - 用途：分类与回归推理参数模板
  - 复用状态：partial；类型：config

### training

- `scripts/train/crossdock/classification/train_ignore_cdr_interface.sh`
  - 能力：分类训练入口
  - 用途：CrossDock 上的分类训练调度
  - 复用状态：partial；类型：code_entry
- `scripts/train/crossdock/regression/train_ignore_cdr_interface_pooling_reg_ft.sh`
  - 能力：回归微调入口
  - 用途：CrossDock 上的回归微调调度
  - 复用状态：partial；类型：code_entry
- `scripts/train/crossdock/regression/train_ignore_cdr_interface_pooling_reg_scratch.sh`
  - 能力：回归从头训练入口
  - 用途：CrossDock 上的回归从零训练调度
  - 复用状态：partial；类型：code_entry
- `src/common/train_utils.py`
  - 能力：训练公共工具
  - 用途：训练流程公共辅助逻辑
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态审查，未运行代码或解包 checkpoint。
- 依赖未安装，无法验证训练/推理可执行性。
- 未发现 bundled data，实际数据来源与数据许可未知。
- 未见独立 evaluation、tests 或 CI 入口。
- LICENSE 存在但 SPDX 为空，自动化许可证边界判定受限。

## 仍未知

- checkpoints/deploy_models.tar.gz 的内部内容、训练来源和是否可直接用于推理未知。
- 训练脚本是否依赖外部下载器、手工准备数据或未列出的资源未知。
- configs/inference_classification.yaml 与 configs/inference_regression.yaml 对应的运行参数是否与 checkpoint 匹配未知。
- README 的声明性信息未逐项核验，无法把文字声明当作可执行证据。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
