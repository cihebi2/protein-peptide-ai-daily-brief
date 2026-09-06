# aameliig/OmiXAI

- **仓库：** [https://github.com/aameliig/OmiXAI](https://github.com/aameliig/OmiXAI)
- **固定 commit：** `416e5a7a7845b059a09ea72c91bfb6f781d74a54`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 31

## 仓库摘要

该冻结仓库实现了 OmiXAI 的 CNN/GNN 建模、数据准备、训练/重训、解释与评估流程，并保存了若干 GraphZSAGEConv 解释/权重类 .pt 文件；但未见 LICENSE，且仅做静态清点，未执行任何代码或测试。

## 可复用模块与资源

### checkpoints

- `interpretation/GraphZSAGEConv/mean_GraphZSAGEConv_v5_lin_Deconvolution.pt`
  - 能力：GraphZSAGEConv 解释/权重快照
  - 用途：静态保存的解释结果或模型状态快照
  - 复用状态：blocked；类型：model_weight
- `interpretation/GraphZSAGEConv/mean_GraphZSAGEConv_v5_lin_GNN_explainer.pt`
  - 能力：GraphZSAGEConv 解释/权重快照
  - 用途：静态保存的解释结果或模型状态快照
  - 复用状态：blocked；类型：model_weight
- `interpretation/GraphZSAGEConv/mean_GraphZSAGEConv_v5_lin_GuidedBackprop.pt`
  - 能力：GraphZSAGEConv 解释/权重快照
  - 用途：静态保存的解释结果或模型状态快照
  - 复用状态：blocked；类型：model_weight
- `interpretation/GraphZSAGEConv/mean_GraphZSAGEConv_v5_lin_IG.pt`
  - 能力：GraphZSAGEConv 解释/权重快照
  - 用途：静态保存的解释结果或模型状态快照
  - 复用状态：blocked；类型：model_weight
- `interpretation/GraphZSAGEConv/mean_GraphZSAGEConv_v5_lin_InputXGradient.pt`
  - 能力：GraphZSAGEConv 解释/权重快照
  - 用途：静态保存的解释结果或模型状态快照
  - 复用状态：blocked；类型：model_weight
- `interpretation/GraphZSAGEConv/mean_GraphZSAGEConv_v5_lin_Saliency.pt`
  - 能力：GraphZSAGEConv 解释/权重快照
  - 用途：静态保存的解释结果或模型状态快照
  - 复用状态：blocked；类型：model_weight

### evaluation

- `scripts/eval_gnn.py`
  - 能力：GNN 评估脚本
  - 用途：GNN 结果评估与指标汇总
  - 复用状态：blocked；类型：code_entry
- `scripts/compare_old_new_ranking.py`
  - 能力：排名对比脚本
  - 用途：旧新结果或特征排名的对比分析
  - 复用状态：blocked；类型：code_entry
- `scripts/eval.slurm`
  - 能力：评估作业脚本
  - 用途：批处理环境中的评估提交脚本
  - 复用状态：blocked；类型：unknown

### inference

- `scripts/run_interpret.py`
  - 能力：解释运行脚本
  - 用途：驱动 Captum / 解释流程的运行入口
  - 复用状态：blocked；类型：code_entry
- `cnn model framework/interpretation.py`
  - 能力：解释模块
  - 用途：CNN 模型的解释/归因逻辑
  - 复用状态：blocked；类型：code_entry
- `graph model framework/interpretation.py`
  - 能力：图模型解释模块
  - 用途：GNN 模型的解释/归因逻辑
  - 复用状态：blocked；类型：code_entry
- `omixai/pipeline.py`
  - 能力：推理/流程入口
  - 用途：模型应用、推理或解释流程的统一入口
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `cnn model framework/cnn_model.py`
  - 能力：CNN 模型定义
  - 用途：CNN 架构与层定义，可作为 omics 建模模板
  - 复用状态：blocked；类型：code_entry
- `graph model framework/graph_model.py`
  - 能力：GNN 模型定义
  - 用途：GNN 架构与层定义，可作为图结构 omics 建模模板
  - 复用状态：blocked；类型：code_entry
- `omixai/models/cnn.py`
  - 能力：CNN 模型实现
  - 用途：打包后的 CNN 模型实现，可供复用或对照
  - 复用状态：blocked；类型：code_entry
- `omixai/models/gnn.py`
  - 能力：GNN 模型实现
  - 用途：打包后的 GNN 模型实现，可供复用或对照
  - 复用状态：blocked；类型：code_entry
- `cnn model framework/data_preparation.py`
  - 能力：数据预处理
  - 用途：样本整理、特征预处理或数据装配逻辑
  - 复用状态：blocked；类型：code_entry
- `omixai/data/dataset.py`
  - 能力：数据集封装
  - 用途：数据集抽象与加载封装
  - 复用状态：blocked；类型：code_entry
- `omixai/data/genome.py`
  - 能力：基因组数据辅助
  - 用途：基因组相关缓存、映射或预处理辅助
  - 复用状态：blocked；类型：code_entry
- `omixai/data/graph_dataset.py`
  - 能力：图数据集封装
  - 用途：图结构数据集构建与加载封装
  - 复用状态：blocked；类型：code_entry
- `omixai/pipeline.py`
  - 能力：流程编排
  - 用途：训练、推理或解释流程的统一编排入口
  - 复用状态：blocked；类型：code_entry
- `omixai/xai/pfi.py`
  - 能力：特征重要性工具
  - 用途：Permutation feature importance 等解释辅助
  - 复用状态：blocked；类型：code_entry

### training

- `omixai/training/train_cnn.py`
  - 能力：CNN 训练模块
  - 用途：CNN 模型训练逻辑
  - 复用状态：blocked；类型：code_entry
- `omixai/training/train_gnn.py`
  - 能力：GNN 训练模块
  - 用途：GNN 模型训练逻辑
  - 复用状态：blocked；类型：code_entry
- `omixai/training/retrain.py`
  - 能力：重训模块
  - 用途：已有模型的再训练或微调逻辑
  - 复用状态：blocked；类型：code_entry
- `cnn model framework/train_test.py`
  - 能力：传统训练/测试脚本
  - 用途：CNN 训练与测试的脚本化流程
  - 复用状态：blocked；类型：code_entry
- `graph model framework/graph_train_test.py`
  - 能力：图模型训练/测试脚本
  - 用途：GNN 训练与测试的脚本化流程
  - 复用状态：blocked；类型：code_entry
- `scripts/run_retrain.py`
  - 能力：重训启动脚本
  - 用途：调用重训流程的脚本入口
  - 复用状态：blocked；类型：code_entry
- `scripts/omixai.slurm`
  - 能力：训练作业脚本
  - 用途：批处理环境中的训练提交脚本
  - 复用状态：blocked；类型：unknown
- `scripts/retrain.slurm`
  - 能力：重训作业脚本
  - 用途：批处理环境中的重训提交脚本
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态清点，未执行代码、未安装依赖、未运行测试
- 仓库未打包 bundled data；真实数据来源与许可未被确认
- interpretation/ 下的 .pt 可能是模型快照，也可能是解释结果序列化文件，路径本身不足以判定
- weights/ 目录仅见 .gitkeep，占位符不等于实际可用权重
- 未见明确许可文本，直接复用受限

## 仍未知

- 外部数据集的具体来源、版本与许可
- 各训练/评估脚本是否能在当前冻结依赖下无改动运行
- .pt 文件是否可直接加载以及与论文结果的对应关系
- notebook 与 .npy 解释产物是否完整复现了发表图表

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
