# microsoft/protein-frame-flow

- **仓库：** [https://github.com/microsoft/protein-frame-flow](https://github.com/microsoft/protein-frame-flow)
- **固定 commit：** `f50d8dbbdae827be291e9f73d732b61b195f8816`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 16

## 仓库摘要

该仓库在冻结提交中提供了 SE(3) flow matching 的蛋白 motif scaffolding / 无条件生成实现，包含训练与推理入口、几何与插值工具、OpenFold 风格依赖、评估脚本，以及若干 metadata/benchmark/target 片段资产；本次仅做静态清点，未运行代码。

## 可复用模块与资源

### datasets

- `metadata/pdb_metadata.csv`
  - 能力：pdb_metadata_and_clusters
  - 用途：PDB 元数据、样本清单与聚类/划分辅助
  - 复用状态：partial；类型：unknown
- `motif_scaffolding/benchmark.csv`
  - 能力：motif_scaffolding_benchmark
  - 用途：motif scaffolding 基准表与目标集合索引
  - 复用状态：partial；类型：unknown
- `motif_scaffolding/targets/1BCF_motif_segments.pkl`
  - 能力：motif_target_segment_caches
  - 用途：目标 motif 片段缓存/预处理结果，供 scaffolding 任务使用
  - 复用状态：partial；类型：unknown

### evaluation

- `analysis/metrics.py`
  - 能力：metric_implementation
  - 用途：评估指标实现与汇总
  - 复用状态：ready_for_review；类型：code_entry
- `motif_scaffolding/benchmark.csv`
  - 能力：benchmark_table
  - 用途：评测目标与结果对照表
  - 复用状态：partial；类型：unknown

### inference

- `experiments/inference_se3_flows.py`
  - 能力：inference_entrypoint
  - 用途：推理执行、采样与结果导出
  - 复用状态：ready_for_review；类型：code_entry
- `configs/inference_scaffolding.yaml`
  - 能力：scaffolding_inference_configs
  - 用途：motif scaffolding 推理参数与 guidance 配置
  - 复用状态：ready_for_review；类型：config

### reusable_assets

- `models/flow_model.py`
  - 能力：core_flow_model
  - 用途：核心 SE(3) flow 模型与结构生成逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `data/interpolant.py`
  - 能力：geometry_and_interpolant_utils
  - 用途：结构插值、SO(3) 与几何辅助计算
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/train_se3_flows.py`
  - 能力：training_recipe
  - 用途：训练入口与训练参数编排
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/inference_se3_flows.py`
  - 能力：inference_recipe
  - 用途：无条件与 scaffolding 推理入口
  - 复用状态：ready_for_review；类型：code_entry
- `analysis/metrics.py`
  - 能力：evaluation_metrics
  - 用途：结构与生成结果的评估指标计算
  - 复用状态：ready_for_review；类型：code_entry
- `openfold/model/model.py`
  - 能力：vendored_openfold_stack
  - 用途：OpenFold 风格模型与数据管线依赖
  - 复用状态：partial；类型：code_entry

### training

- `experiments/train_se3_flows.py`
  - 能力：training_entrypoint
  - 用途：主训练脚本，驱动 SE(3) flow matching 训练流程
  - 复用状态：ready_for_review；类型：code_entry
- `data/pdb_dataloader.py`
  - 能力：training_data_pipeline
  - 用途：训练数据读取、预处理与样本组织
  - 复用状态：ready_for_review；类型：code_entry
- `configs/model.yaml`
  - 能力：training_configs
  - 用途：模型、数据与训练超参数配置
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做静态清点，未执行代码、未安装依赖、未运行测试。
- 冻结清单中没有识别到任何 checkpoint 文件，因此无法把推理结果与特定权重绑定。
- openfold/ 树是否完整继承上游许可、以及其是否为正式 vendored 代码，仅凭路径存在无法最终证明。
- 部分 CSV/PKL 资产只证明存在，不证明其生成流程、数据来源合规性或可复现性。

## 仍未知

- metadata/pdb_metadata.csv、metadata/scope_metadata.csv 与 motif_scaffolding/targets/*.pkl 的具体来源和许可未在静态清单中明确。
- 仓库中的 openfold/ 子树是否完全对应上游发行版、以及是否存在额外补丁，静态 inventory 无法确认。
- 没有 checkpoint 资产，无法判断仓库是否依赖外部下载权重或隐藏的未跟踪模型文件。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
