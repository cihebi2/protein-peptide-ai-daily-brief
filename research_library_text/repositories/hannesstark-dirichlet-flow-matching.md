# HannesStark/dirichlet-flow-matching

- **仓库：** [https://github.com/HannesStark/dirichlet-flow-matching](https://github.com/HannesStark/dirichlet-flow-matching)
- **固定 commit：** `6f360612da8f69ecf4860c075f74ed52b37ce64b`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 30

## 仓库摘要

该仓库是 MIT 许可的 DNA 序列设计研究代码，含模型、Lightning 模块、训练脚本和若干数据/评测辅助文件；冻结清单未见数据集或 checkpoint，且未执行代码，因此只能做静态可复用资产盘点。

## 可复用模块与资源

### datasets

- `utils/dataset.py`
  - 能力：data_loader
  - 用途：通用数据读取与预处理；冻结清单中未见原始数据文件
  - 复用状态：partial；类型：code_entry
- `utils/promoter_dataset.py`
  - 能力：data_loader
  - 用途：promoter 数据集封装；看起来依赖外部数据源
  - 复用状态：partial；类型：code_entry

### evaluation

- `lightning_modules/cls_module.py`
  - 能力：metric_or_validation
  - 用途：分类任务的 validation/metric 钩子
  - 复用状态：partial；类型：code_entry
- `utils/sei.py`
  - 能力：benchmark_helper
  - 用途：SEI 基准/打分辅助
  - 复用状态：partial；类型：code_entry
- `utils/selene_utils.py`
  - 能力：benchmark_helper
  - 用途：Selene 基准/打分辅助
  - 复用状态：partial；类型：code_entry
- `utils/visualize.py`
  - 能力：result_visualization
  - 用途：结果可视化与人工检查
  - 复用状态：partial；类型：code_entry

### inference

- `lightning_modules/dna_module.py`
  - 能力：sampling_support
  - 用途：DNA 生成/采样相关的训练到推理桥接逻辑；未见独立推理脚本
  - 复用状态：partial；类型：code_entry
- `lightning_modules/promoter_module.py`
  - 能力：sampling_support
  - 用途：promoter 相关推理/验证桥接逻辑；未见独立推理脚本
  - 复用状态：partial；类型：code_entry
- `utils/flow_utils.py`
  - 能力：sampling_support
  - 用途：flow 轨迹/采样辅助
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `model/dna_models.py`
  - 能力：model_architecture
  - 用途：DNA 序列生成/建模的核心网络定义
  - 复用状态：ready_for_review；类型：code_entry
- `model/msa_transformer.py`
  - 能力：model_architecture
  - 用途：MSA Transformer 相关编码器/骨干模块
  - 复用状态：ready_for_review；类型：code_entry
- `model/promoter_model.py`
  - 能力：model_architecture
  - 用途：promoter 任务的模型定义
  - 复用状态：ready_for_review；类型：code_entry
- `lightning_modules/general_module.py`
  - 能力：training
  - 用途：共享 PyTorch Lightning 训练/验证骨架
  - 复用状态：ready_for_review；类型：code_entry
- `lightning_modules/dna_module.py`
  - 能力：training
  - 用途：DNA 实验的 Lightning 训练与验证逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `lightning_modules/promoter_module.py`
  - 能力：training
  - 用途：promoter 实验的 Lightning 训练与验证逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `lightning_modules/cls_module.py`
  - 能力：training
  - 用途：分类器训练/验证逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `train_dna.py`
  - 能力：training
  - 用途：DNA 训练入口脚本
  - 复用状态：ready_for_review；类型：code_entry
- `train_promo.py`
  - 能力：training
  - 用途：promoter 训练入口脚本
  - 复用状态：ready_for_review；类型：code_entry
- `train_classifier.py`
  - 能力：training
  - 用途：分类器训练入口脚本
  - 复用状态：ready_for_review；类型：code_entry
- `model/dna_models.py`
  - 能力：inference
  - 用途：推理/采样时的 DNA 模型前向骨干；未见独立推理 CLI
  - 复用状态：partial；类型：code_entry
- `model/promoter_model.py`
  - 能力：inference
  - 用途：promoter 推理时的模型骨干；未见独立推理 CLI
  - 复用状态：partial；类型：code_entry
- `utils/flow_utils.py`
  - 能力：inference
  - 用途：flow matching 相关计算/采样辅助；更像支撑推理而非已验证入口
  - 复用状态：partial；类型：code_entry
- `utils/esm.py`
  - 能力：inference
  - 用途：ESM 相关表示/嵌入辅助，可能支撑推理
  - 复用状态：partial；类型：code_entry
- `lightning_modules/cls_module.py`
  - 能力：evaluation
  - 用途：分类器的 validation/metric 逻辑，可能用于评测
  - 复用状态：partial；类型：code_entry
- `utils/sei.py`
  - 能力：evaluation
  - 用途：SEI 相关评测/打分辅助
  - 复用状态：partial；类型：code_entry
- `utils/selene_utils.py`
  - 能力：evaluation
  - 用途：Selene 相关评测辅助
  - 复用状态：partial；类型：code_entry
- `utils/visualize.py`
  - 能力：evaluation
  - 用途：结果可视化/检查辅助
  - 复用状态：partial；类型：code_entry

### training

- `train_dna.py`
  - 能力：training_entrypoint
  - 用途：DNA 训练入口
  - 复用状态：ready_for_review；类型：code_entry
- `train_promo.py`
  - 能力：training_entrypoint
  - 用途：promoter 训练入口
  - 复用状态：ready_for_review；类型：code_entry
- `train_classifier.py`
  - 能力：training_entrypoint
  - 用途：分类器训练入口
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态盘点，未执行代码、测试或训练。
- 未安装依赖，无法验证导入、下载或运行路径。
- 冻结清单中未见 bundled 数据集或 checkpoint。
- 路径存在不等于功能可复现。
- 仓库可能依赖外部预训练模型或数据源，但未被当前清单证明。

## 仍未知

- `utils/esm.py` 是否依赖外部 ESM 权重或下载流程未核验。
- 训练脚本是否会自动下载外部数据集未核验。
- README 的具体命令行、实验配置和数据说明未随本次静态清单提供。
- 是否存在未暴露的 large/promisor-only 资源无法确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
