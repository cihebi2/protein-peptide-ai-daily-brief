# shadow1229/WatGNN

- **仓库：** [https://github.com/shadow1229/WatGNN](https://github.com/shadow1229/WatGNN)
- **固定 commit：** `63e46e66163251da89e1f322c9c11c19d53a7208`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 12

## 仓库摘要

该仓库围绕WatGNN水位点预测提供模型代码、数据划分、预计算预测与单个checkpoint；但未见LICENSE或可复现训练入口，直接复用受限。

## 可复用模块与资源

### checkpoints

- `watgnn/network/epoch_00150.dict`
  - 能力：model_checkpoint
  - 用途：单个训练轮次的参数快照，可用于载入推理
  - 复用状态：blocked；类型：unknown

### datasets

- `watgnn/Dataset/WatGNN set/train.txt`
  - 能力：water_position_benchmark_split
  - 用途：训练/验证/测试划分清单
  - 复用状态：unknown；类型：unknown
- `watgnn/Dataset/protein-compound set/pdbbind_clean.txt`
  - 能力：protein_compound_benchmark_lists
  - 用途：PDBBind 相关清单与排除列表
  - 复用状态：unknown；类型：unknown
- `watgnn/Dataset/single protein set/single_protein_set.txt`
  - 能力：single_protein_benchmark_list
  - 用途：单蛋白测试集清单
  - 复用状态：unknown；类型：unknown
- `watgnn/Precalculated_data/protein_compound_set/ref/1adl_protein.pdb`
  - 能力：reference_structures_and_precomputed_inputs
  - 用途：复现/对照用 protein-water 参考结构与输入预处理产物
  - 复用状态：blocked；类型：unknown

### evaluation

- `watgnn/watgnn_evaluation.py`
  - 能力：evaluation_scripts_and_metrics
  - 用途：RMSD、benchmark 统计与评测辅助
  - 复用状态：blocked；类型：code_entry
- `watgnn/Precalculated_data/single_protein_set/WatGNN/performance/1byi_A.dat`
  - 能力：evaluation_outputs_and_plots
  - 用途：已生成的性能汇总、时间统计与图表
  - 复用状态：blocked；类型：unknown

### inference

- `watgnn/Precalculated_data/protein_compound_set/WatGNN/1adl_pred.pdb`
  - 能力：water_position_prediction_outputs
  - 用途：WatGNN 预测结果的静态输出文件
  - 复用状态：blocked；类型：unknown
- `watgnn/network/epoch_00150.dict`
  - 能力：runtime_checkpoint_for_inference
  - 用途：推理时加载的模型权重/参数文件
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `watgnn/watgnn.py`
  - 能力：model_architecture
  - 用途：SE(3)-GNN 水位点预测主模型、特征构造与网络定义
  - 复用状态：blocked；类型：code_entry
- `watgnn/watgnn_input.py`
  - 能力：preprocessing_and_input
  - 用途：输入解析、预处理与运行配置
  - 复用状态：blocked；类型：code_entry
- `watgnn/watgnn_visualization.py`
  - 能力：visualization
  - 用途：结果可视化与论文图示生成
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态盘点，未运行代码或测试。
- 冻结清单里没有明确的 training entrypoint 或 training module。
- `pyproject.toml` 仅显示依赖元数据，未证明依赖已安装。
- 大量 `.pdb`/`.dat`/`.png` 更像预计算输入与结果，静态存在不代表可重现。
- 缺少 LICENSE，直接复用代码受限。

## 仍未知

- `watgnn.py` 是否同时包含训练与推理逻辑，静态清单不足以确认。
- `network/epoch_00150.dict` 的训练来源、超参数和数据切分未在冻结元数据中明确。
- `watgnn/Dataset/*` 与预计算结构的原始授权链路未明。
- 预计算 baseline 输出（3D-RISM、GalaxyWater-CNN、FoldX 等）是否全部由本仓库生成，静态无法证明。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
