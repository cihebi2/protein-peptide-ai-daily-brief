# chaitjo/geometric-rna-design

- **仓库：** [https://github.com/chaitjo/geometric-rna-design](https://github.com/chaitjo/geometric-rna-design)
- **固定 commit：** `2453b18778a1981ac25f314790e5395f1e9ab218`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 34

## 仓库摘要

这是一个以 gRNAde 为中心的 3D RNA inverse design 仓库：包含项目自有的训练、推理、评估与数据处理代码，同时捆绑了若干第三方子树和多份数据/分割工件；静态审查未见可直接验证的运行、测试或复现证据，也未发现明确的模型权重 checkpoint。

## 可复用模块与资源

### checkpoints

- `data/das_split.pt`
  - 能力：split_artifact
  - 用途：DAS 数据集切分缓存/序列化分割工件，不是模型权重
  - 复用状态：partial；类型：model_weight
- `data/structsim_v2_split.pt`
  - 能力：split_artifact
  - 用途：structsim_v2 数据集切分缓存/序列化分割工件，不是模型权重
  - 复用状态：partial；类型：model_weight

### datasets

- `data/RFAM_families_27062023.csv`
  - 能力：source_table
  - 用途：RNA family/source table，供筛选或注释使用
  - 复用状态：ready_for_review；类型：unknown
- `data/nrlist_3.306_4.0A.csv`
  - 能力：source_table
  - 用途：non-redundant 结构列表/筛选表
  - 复用状态：ready_for_review；类型：unknown
- `data/rnasolo-main-table.csv`
  - 能力：source_table
  - 用途：RNA SOLO 主表/元数据表
  - 复用状态：ready_for_review；类型：unknown
- `projects/openknot_benchmark/metadata_7a.csv`
  - 能力：benchmark_metadata
  - 用途：openknot benchmark 元数据
  - 复用状态：ready_for_review；类型：unknown
- `projects/openknot_benchmark/metadata_7b.csv`
  - 能力：benchmark_metadata
  - 用途：openknot benchmark 元数据
  - 复用状态：ready_for_review；类型：unknown
- `projects/rna_polymerase_ribozyme/fitness_landscape_constraints/5TU_fitness_landscape.csv`
  - 能力：fitness_landscape
  - 用途：ribozyme fitness landscape 约束表
  - 复用状态：ready_for_review；类型：unknown
- `projects/rna_polymerase_ribozyme/fitness_landscape_constraints/combinability_array.npy`
  - 能力：fitness_landscape_array
  - 用途：组合可行性数组
  - 复用状态：ready_for_review；类型：unknown
- `projects/rna_polymerase_ribozyme/fitness_landscape_constraints/max_fitness_array.npy`
  - 能力：fitness_landscape_array
  - 用途：最大 fitness 参考数组
  - 复用状态：ready_for_review；类型：unknown

### evaluation

- `src/evaluator.py`
  - 能力：evaluation_module
  - 用途：评估/打分逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `src/openknot_score.py`
  - 能力：openknot_score
  - 用途：openknot 指标/评分实现
  - 复用状态：ready_for_review；类型：code_entry
- `projects/openknot_benchmark/README.md`
  - 能力：benchmark_protocol
  - 用途：benchmark 流程与结果说明
  - 复用状态：partial；类型：unknown
- `projects/openknot_benchmark/publication_figures.ipynb`
  - 能力：analysis_notebook
  - 用途：评估结果可视化与出图
  - 复用状态：partial；类型：unknown
- `projects/rna_polymerase_ribozyme/calculate_fitness.ipynb`
  - 能力：fitness_analysis_notebook
  - 用途：适应度计算与后处理分析
  - 复用状态：partial；类型：unknown
- `projects/rna_polymerase_ribozyme/publication_figures.ipynb`
  - 能力：publication_notebook
  - 用途：论文图表与结果整理
  - 复用状态：partial；类型：unknown

### inference

- `design.py`
  - 能力：design_entrypoint
  - 用途：序列设计/推理入口，按文件名推断而未执行验证
  - 复用状态：partial；类型：code_entry
- `main.py`
  - 能力：cli_entrypoint
  - 用途：顶层 CLI/任务分发入口，可能覆盖设计与推理流程
  - 复用状态：partial；类型：code_entry
- `configs/design.yaml`
  - 能力：design_config
  - 用途：设计/推理模式配置
  - 复用状态：ready_for_review；类型：config
- `tools/rhofold/model/rna_fm/pretrained.py`
  - 能力：pretrained_weight_reference
  - 用途：预训练权重名称/来源映射参考；不是序列化 checkpoint 文件
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `src/models.py`
  - 能力：core_model
  - 用途：核心 RNA inverse design 模型组装与调度
  - 复用状态：ready_for_review；类型：code_entry
- `src/layers.py`
  - 能力：neural_layers
  - 用途：通用神经网络层与模块封装
  - 复用状态：ready_for_review；类型：code_entry
- `src/constants.py`
  - 能力：constants
  - 用途：全局常量与配置键
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/featurizer.py`
  - 能力：featurization
  - 用途：序列/结构特征构造
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/data_utils.py`
  - 能力：data_utils
  - 用途：数据预处理与通用工具
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/clustering_utils.py`
  - 能力：clustering_utils
  - 用途：聚类/划分辅助逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/sec_struct_utils.py`
  - 能力：sec_struct_utils
  - 用途：secondary structure 处理工具
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/viz_utlils.py`
  - 能力：viz_utils
  - 用途：可视化与绘图辅助
  - 复用状态：ready_for_review；类型：code_entry
- `tools/rhofold/model/e2eformer.py`
  - 能力：vendored_backbone
  - 用途：vendored RNA backbone/structure 模块实现
  - 复用状态：partial；类型：code_entry
- `tools/ribonanzanet/network.py`
  - 能力：vendored_scoring_network
  - 用途：vendored scoring network 实现
  - 复用状态：partial；类型：code_entry
- `tools/ribonanzanet_sec_struct/network.py`
  - 能力：vendored_sec_struct_network
  - 用途：vendored secondary-structure network 实现
  - 复用状态：partial；类型：code_entry

### training

- `src/trainer.py`
  - 能力：trainer_module
  - 用途：训练循环与优化流程的辅助模块；未见独立训练入口文件
  - 复用状态：ready_for_review；类型：code_entry
- `configs/default.yaml`
  - 能力：training_config
  - 用途：默认训练/实验配置
  - 复用状态：ready_for_review；类型：config
- `configs/sweep.yaml`
  - 能力：sweep_config
  - 用途：超参数 sweep 配置
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做静态审查，未执行仓库代码、训练、测试或评估。
- 缺少依赖安装与运行日志，无法验证 `main.py`/`design.py`/notebook 的实际可复现性。
- 未发现明确的、可直接使用的模型权重 checkpoint；现有 `.pt` 主要像数据切分工件。
- `tools/ViennaRNA-2.6.4.tar.gz` 的内部许可与来源未在本次静态盘点中核实。

## 仍未知

- `data/RFAM_families_27062023.csv`、`data/nrlist_3.306_4.0A.csv`、`data/rnasolo-main-table.csv` 的原始来源与再分发许可未在清单中明确。
- `tools/rhofold/model/rna_fm/pretrained.py` 只是权重引用/定位逻辑，实际预训练权重文件未被跟踪。
- `src/trainer.py` 是否可独立作为训练入口、以及 `main.py` 的模式分发逻辑，均未通过执行验证。
- `projects/*` 下大量 CSV/PDB/PDF/IPynb 更像实验产物或分析素材，是否可作为通用数据资产需额外确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
