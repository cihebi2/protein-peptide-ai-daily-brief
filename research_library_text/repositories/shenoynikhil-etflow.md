# shenoynikhil/ETFlow

- **仓库：** [https://github.com/shenoynikhil/ETFlow](https://github.com/shenoynikhil/ETFlow)
- **固定 commit：** `80f82d7d142bc3872412d2966a8d71ed14462b18`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 13

## 仓库摘要

该仓库是 ET-Flow 的静态代码实现，包含模型、数据加载、训练、采样与评测入口；配置文件覆盖 QM9 与 drugs 场景，但冻结清单中未见原始数据或 checkpoints。

## 可复用模块与资源

### datasets

- `etflow/data/dataset.py`
  - 能力：QM9 数据管线
  - 用途：面向 QM9 的数据集读取/预处理与实验对接；冻结清单未包含原始数据文件。
  - 复用状态：partial；类型：code_entry
- `etflow/data/datamodule.py`
  - 能力：drugs 数据管线
  - 用途：面向 drugs 场景的数据加载与实验对接；冻结清单未包含原始数据文件。
  - 复用状态：partial；类型：code_entry

### evaluation

- `scripts/eval.py`
  - 能力：总评测入口
  - 用途：统一评测调度入口。
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/eval_cov_mat.py`
  - 能力：协方差矩阵评测
  - 用途：评估生成构象分布的 covariance matrix 相关指标。
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/eval_prop.py`
  - 能力：性质评测
  - 用途：评估分子性质相关指标。
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/eval_xl.py`
  - 能力：XL 评测
  - 用途：评估 XL 任务/设置。
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `etflow/commons/sample.py`
  - 能力：构象采样
  - 用途：从训练模型中采样分子构象。
  - 复用状态：ready_for_review；类型：code_entry
- `generate_confs.ipynb`
  - 能力：构象生成示例 notebook
  - 用途：手动/示例式构象生成流程。
  - 复用状态：partial；类型：unknown

### reusable_assets

- `etflow/models/model.py`
  - 能力：核心模型与损失实现
  - 用途：实现 ET-Flow 主模型、损失与辅助工具，支撑构象生成训练/推理。
  - 复用状态：ready_for_review；类型：code_entry
- `etflow/networks/torchmd_net/model_dynamics.py`
  - 能力：等变几何 backbone
  - 用途：提供 TorchMD-Net 风格的等变动力学/消息传递组件，支撑分子几何建模。
  - 复用状态：partial；类型：code_entry
- `configs/qm9-base.yaml`
  - 能力：实验配置 recipes
  - 用途：定义 QM9 与 drugs 的训练/采样配置变体。
  - 复用状态：ready_for_review；类型：config

### training

- `scripts/train.py`
  - 能力：训练入口
  - 用途：启动训练流程并连接模型、数据与配置。
  - 复用状态：ready_for_review；类型：code_entry
- `etflow/schedulers/CosineAnnealingWarmRestarts.py`
  - 能力：学习率调度
  - 用途：训练时的 cosine warm restarts 调度支持。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态存量分析，未执行代码、未安装依赖、未跑测试。
- 冻结清单未见原始数据文件与 checkpoints，不能据此证明可复现。
- torchmd_net 子树可能是第三方或改写代码，但未做内容级核验。
- 配置文件显示 QM9 与 drugs 流程，但数据下载源和预处理产物未被验证。
- Notebook 仅按路径存在，未检查其运行状态或嵌入输出。

## 仍未知

- 实际训练超参数、数据下载地址和预处理细节未知。
- 是否存在仓库外发布的 checkpoints 或数据未纳入冻结清单未知。
- torchmd_net 子树的确切来源与许可证边界未知。
- 各评测脚本的运行结果与指标值在当前环境下未知。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
