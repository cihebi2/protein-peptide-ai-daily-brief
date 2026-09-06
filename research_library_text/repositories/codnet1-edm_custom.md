# codnet1/edm_custom

- **仓库：** [https://github.com/codnet1/edm_custom](https://github.com/codnet1/edm_custom)
- **固定 commit：** `93e7086144623c733fdb121cc5a5bd35d5a1ed86`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 27

## 仓库摘要

该仓库是 CoDNet/EDM_Custom 的受控扩散分子生成实现，包含模型结构、GEOM/QM9 数据加载、训练与评估配置，但未见许可证、checkpoint 或可验证推理入口，故复用边界受限。

## 可复用模块与资源

### datasets

- `midi/datasets/qm9_dataset.py`
  - 能力：dataset loader: QM9
  - 用途：QM9 读取与预处理
  - 复用状态：blocked；类型：code_entry
- `midi/datasets/geom_dataset.py`
  - 能力：dataset loader: GEOM
  - 用途：GEOM 读取与预处理
  - 复用状态：blocked；类型：code_entry
- `midi/datasets/geom_preprocessing.py`
  - 能力：dataset preprocessing: GEOM
  - 用途：GEOM 预处理脚本
  - 复用状态：blocked；类型：code_entry
- `midi/datasets/adaptive_loader.py`
  - 能力：dataset utility: adaptive loader
  - 用途：自适应加载/采样
  - 复用状态：blocked；类型：code_entry
- `midi/datasets/dataset_utils.py`
  - 能力：dataset utility: shared helpers
  - 用途：数据集通用辅助函数
  - 复用状态：blocked；类型：code_entry
- `configs/dataset/qm9.yaml`
  - 能力：dataset recipe: QM9
  - 用途：QM9 数据集参数与选择
  - 复用状态：blocked；类型：config
- `configs/dataset/geom.yaml`
  - 能力：dataset recipe: GEOM
  - 用途：GEOM 数据集参数与选择
  - 复用状态：blocked；类型：config

### evaluation

- `midi/metrics/molecular_metrics.py`
  - 能力：evaluation metric: molecular metrics
  - 用途：分子有效性/性质等指标
  - 复用状态：blocked；类型：code_entry
- `midi/metrics/metrics_utils.py`
  - 能力：evaluation utility: metrics helpers
  - 用途：评估指标辅助函数
  - 复用状态：blocked；类型：code_entry
- `midi/analysis/baselines_evaluation.py`
  - 能力：evaluation workflow: baseline comparison
  - 用途：与基线方法对比
  - 复用状态：blocked；类型：code_entry
- `midi/analysis/rdkit_functions.py`
  - 能力：evaluation utility: RDKit helpers
  - 用途：化学性质与结构辅助计算
  - 复用状态：blocked；类型：code_entry
- `midi/analysis/visualization.py`
  - 能力：evaluation utility: visualization
  - 用途：结果可视化与展示
  - 复用状态：blocked；类型：code_entry

### inference

- `sbdd-controlled-diffusion.ipynb`
  - 能力：notebook: controlled diffusion demo
  - 用途：交互式分子生成/采样演示
  - 复用状态：unknown；类型：unknown
- `sbdd-diffusion.ipynb`
  - 能力：notebook: diffusion demo
  - 用途：扩散实验与可视化演示
  - 复用状态：unknown；类型：unknown

### reusable_assets

- `controlnet/conditioned_diffusion_model.py`
  - 能力：code module: controlled diffusion core model
  - 用途：受控分子生成主模型
  - 复用状态：blocked；类型：code_entry
- `controlnet/model.py`
  - 能力：code module: control branch model
  - 用途：控制条件分支网络
  - 复用状态：blocked；类型：code_entry
- `controlnet/zero_conv.py`
  - 能力：code module: zero-init convolution adapter
  - 用途：控制注入与条件适配
  - 复用状态：blocked；类型：code_entry
- `midi/diffusion_model.py`
  - 能力：code module: diffusion orchestration
  - 用途：扩散训练与采样主流程
  - 复用状态：blocked；类型：code_entry
- `midi/diffusion/noise_model.py`
  - 能力：code module: noise process model
  - 用途：噪声调度与扩散过程建模
  - 复用状态：blocked；类型：code_entry
- `midi/models/layers.py`
  - 能力：code module: network layers
  - 用途：模型基础层与复用组件
  - 复用状态：blocked；类型：code_entry
- `midi/models/transformer_model.py`
  - 能力：code module: transformer backbone
  - 用途：Transformer 编码/注意力 backbone
  - 复用状态：blocked；类型：code_entry

### training

- `configs/config.yaml`
  - 能力：training config: root defaults
  - 用途：全局运行与实验默认值
  - 复用状态：blocked；类型：config
- `configs/general/general_default.yaml`
  - 能力：training config: general defaults
  - 用途：通用超参与运行设置
  - 复用状态：blocked；类型：config
- `configs/model/discrete.yaml`
  - 能力：training config: discrete model
  - 用途：离散扩散模型超参
  - 复用状态：blocked；类型：config
- `configs/train/train_default.yaml`
  - 能力：training config: default train recipe
  - 用途：优化器、batch、epoch 等训练默认项
  - 复用状态：blocked；类型：config
- `midi/metrics/train_metrics.py`
  - 能力：training utility: train-time metrics
  - 用途：训练过程指标记录
  - 复用状态：blocked；类型：code_entry
- `configs/experiment/debug.yaml`
  - 能力：training config: debug experiment
  - 用途：调试/小规模实验模板
  - 复用状态：blocked；类型：config

## 使用限制

- 仅做静态分析，未运行代码、测试或下载依赖。
- 仓库未见 LICENSE，代码与配置的直接复用受限。
- 未见 checkpoint 或 bundled data，无法从清单证明可复现训练/推理。
- 未发现独立 training entrypoint 或 inference CLI。

## 仍未知

- 两个 notebook 的实际角色（训练、采样还是可视化）未逐个读取。
- GEOM/QM9 的外部下载来源、数据许可证和预处理产物不在冻结清单里。
- configs/experiment 其余变体的具体参数差异未逐一核验。
- 是否存在未跟踪的大文件、缓存或权重无法仅凭当前清单确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
