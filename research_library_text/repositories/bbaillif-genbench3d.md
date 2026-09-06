# bbaillif/genbench3d

- **仓库：** [https://github.com/bbaillif/genbench3d](https://github.com/bbaillif/genbench3d)
- **固定 commit：** `0926bc6614509aa10ccf6f69da0405d4be6af6b3`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 15

## 仓库摘要

仓库主要提供结构基础 3D 分子生成的基准与评测套件：包含数据加载/预处理、口袋与蛋白结构处理、几何分析、2D/3D/活性与口袋指标、基准脚本和少量示例数据；静态清单未见独立训练入口或模型检查点。

## 可复用模块与资源

### datasets

- `test_set/ligand_filenames.txt`
  - 能力：benchmark_dataset
  - 用途：结构基准测试集索引；与同目录 receptor / ligand / pocket 文件共同构成 `test_set/*` 三元组
  - 复用状态：partial；类型：unknown
- `examples/pocket2mol_generated_2z3h.sdf`
  - 能力：example_generated_sample
  - 用途：示例生成分子文件，用于展示输出格式或可视化
  - 复用状态：partial；类型：unknown

### evaluation

- `benchmark.py`
  - 能力：benchmark_runner
  - 用途：基准运行、汇总与对比；配套 `benchmark_baselines.py`、`benchmark_mols.py`、`structure_based_benchmark.py`、`sb_benchmark_mols.py`
  - 复用状态：partial；类型：code_entry
- `genbench3d/metrics/graph/validity2d.py`
  - 能力：graph_metrics
  - 用途：2D validity、uniqueness、novelty、diversity、性质与 ring proportion 评估
  - 复用状态：ready_for_review；类型：code_entry
- `genbench3d/metrics/conf3d/validity3d.py`
  - 能力：conf3d_metrics
  - 用途：3D 构象 validity、uniqueness、diversity、novelty、strain、SPE 与能量/搜索相关评估
  - 复用状态：ready_for_review；类型：code_entry
- `genbench3d/metrics/activity/vina_scorer.py`
  - 能力：activity_scoring
  - 用途：Vina / GOLD / Glide / IFP similarity 等活性与对接打分包装
  - 复用状态：partial；类型：code_entry
- `genbench3d/metrics/pocket/steric_clash.py`
  - 能力：pocket_metrics
  - 用途：口袋中心距离与 steric clash 评估
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `genbench3d/sbgenbench3d.py`
  - 能力：generation_or_benchmark_entrypoint
  - 用途：结构基础生成/基准流程入口候选
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `config/default.yaml`
  - 能力：config_recipe
  - 用途：默认运行参数、路径与基准配置
  - 复用状态：ready_for_review；类型：config
- `genbench3d/data/source/cross_docked.py`
  - 能力：data_loader
  - 用途：CrossDocked 等结构-配体来源适配；同类 loader 还包括 `pdbbind.py`、`csd_drug.py`、`sdf_source.py`、`mol_list_source.py`
  - 复用状态：partial；类型：code_entry
- `genbench3d/data/preprocessing/conf_generator.py`
  - 能力：preprocessing
  - 用途：构象生成与分子标准化前处理；配套 `mol_standardizer.py`
  - 复用状态：ready_for_review；类型：code_entry
- `genbench3d/data/structure/pocket.py`
  - 能力：structure_handling
  - 用途：pocket / protein / docking 结构表示与处理；同类实现含 `protein.py`、`vina_protein.py`、`glide_protein.py`
  - 复用状态：partial；类型：code_entry
- `genbench3d/geometry/geometry_extractor.py`
  - 能力：geometry
  - 用途：几何特征提取、clash 检测、参考几何与分布估计
  - 复用状态：ready_for_review；类型：code_entry
- `genbench3d/sb_model.py`
  - 能力：model_architecture
  - 用途：结构基础生成/评分相关核心模型定义；配套 `genbench3d.py`、`sbgenbench3d.py` 与 `conf_ensemble/*`
  - 复用状态：partial；类型：code_entry
- `genbench3d/sbgenbench3d.py`
  - 能力：inference
  - 用途：结构基础生成/评测流程的命令层入口候选
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清单审查，未安装依赖、未运行代码、未执行测试。
- 仓库内未见任何显式 checkpoint 文件或权重文件。
- `activity` 相关评估依赖外部打分/对接工具，静态清单不足以确认可执行性与授权条件。
- `test_set/` 与 `examples/` 的来源与再许可状态无法仅凭路径确认。

## 仍未知

- `genbench3d/sb_model.py` 是否包含可独立训练的实现，静态清单不足以确认。
- `genbench3d/sbgenbench3d.py` 与 `genbench3d/genbench3d.py` 更偏入口封装还是实际推理逻辑，未执行无法判定。
- `test_set/` 中样本是否完全来自第三方公开数据源、以及是否需要附加许可，当前不可确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
