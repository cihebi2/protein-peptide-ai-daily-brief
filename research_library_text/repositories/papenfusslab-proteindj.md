# PapenfussLab/proteindj

- **仓库：** [https://github.com/PapenfussLab/proteindj](https://github.com/PapenfussLab/proteindj)
- **固定 commit：** `b61cb0680d5e39df47c35b30454f31361460f277`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 26

## 仓库摘要

仓库是 ProteinDJ 的蛋白设计管线与评估套件，静态清单显示大量 .pt 资产、Nextflow 模块和容器定义；仅能确认 MIT 代码许可，数据/模型边界未解。

## 可复用模块与资源

### checkpoints

- `benchmarkdata/1www_trka_adj.pt`
  - 能力：benchmark_feature_cache
  - 用途：目标相关的序列化张量/特征缓存
  - 复用状态：blocked；类型：model_weight
- `benchmarkdata/5o45_pd-l1_ss.pt`
  - 能力：benchmark_feature_cache
  - 用途：目标相关的序列化张量/特征缓存
  - 复用状态：blocked；类型：model_weight
- `binderscaffolds/scaffolds_100_EHEEHE/EHEEHE_ems_00001_adj.pt`
  - 能力：scaffold_feature_cache
  - 用途：scaffold 相关的序列化张量/特征缓存
  - 复用状态：blocked；类型：model_weight
- `binderscaffolds/scaffolds_100_HEEHE/HEEHE_lc_00007_ss.pt`
  - 能力：scaffold_feature_cache
  - 用途：scaffold 相关的序列化张量/特征缓存
  - 复用状态：blocked；类型：model_weight
- `binderscaffolds/scaffolds_100_HHH/HHH_bc_00001_adj.pt`
  - 能力：scaffold_feature_cache
  - 用途：scaffold 相关的序列化张量/特征缓存
  - 复用状态：blocked；类型：model_weight
- `binderscaffolds/scaffolds_100_HHHH/HHHH_bc_00001_ss.pt`
  - 能力：scaffold_feature_cache
  - 用途：scaffold 相关的序列化张量/特征缓存
  - 复用状态：blocked；类型：model_weight

### datasets

- `benchmarkdata/1www_trka.pdb`
  - 能力：benchmark_targets
  - 用途：目标结构样例/基准输入
  - 复用状态：blocked；类型：unknown
- `benchmarkdata/5o45_pd-l1_uncropped.pdb`
  - 能力：benchmark_targets
  - 用途：未裁剪目标结构样例
  - 复用状态：blocked；类型：unknown
- `binderscaffolds/scaffolds_EHEEHE.tar.gz`
  - 能力：scaffold_library
  - 用途：scaffold 库压缩包
  - 复用状态：blocked；类型：unknown
- `lib/pdl1_msa.a3m`
  - 能力：sequence_example
  - 用途：MSA 示例输入
  - 复用状态：blocked；类型：unknown
- `lib/examplebinder.pdb`
  - 能力：example_structure
  - 用途：示例 binder 结构
  - 复用状态：blocked；类型：unknown

### evaluation

- `scripts/analyse_best_designs.py`
  - 能力：design_ranking
  - 用途：对候选设计做终选分析与排序
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/rank_designs.py`
  - 能力：score_ranking
  - 用途：按分数/指标对设计结果排序
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/generate_success_metrics.py`
  - 能力：metric_generation
  - 用途：生成成功率或成功标准相关指标
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/filter_af2.py`
  - 能力：filtering
  - 用途：基于 AF2 结果做过滤
  - 复用状态：ready_for_review；类型：code_entry
- `bindsweeper/bindsweeper/success_rate_analyzer.py`
  - 能力：success_analysis
  - 用途：分析 sweep 成功率
  - 复用状态：ready_for_review；类型：code_entry
- `bindsweeper/tests/test_success_rate_analyzer.py`
  - 能力：validation_tests
  - 用途：静态验证成功率分析逻辑
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `scripts/generate_contigs.py`
  - 能力：contig_generation
  - 用途：生成 contig/片段约束
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/generate_mode_schemas.py`
  - 能力：mode_schema_generation
  - 用途：生成 mode 参数 schema
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/prep_boltz_yaml.py`
  - 能力：input_prep
  - 用途：准备 Boltz 输入 YAML
  - 复用状态：ready_for_review；类型：code_entry
- `modules/rfdiffusion.nf`
  - 能力：design_inference_wrapper
  - 用途：RFDiffusion 推断/生成流程封装
  - 复用状态：ready_for_review；类型：unknown
- `modules/boltz.nf`
  - 能力：structure_prediction_wrapper
  - 用途：Boltz 推断/结构预测流程封装
  - 复用状态：ready_for_review；类型：unknown

### reusable_assets

- `main.nf`
  - 能力：pipeline_orchestration
  - 用途：Nextflow 主入口，串联设计、筛选、分析与发布步骤
  - 复用状态：ready_for_review；类型：unknown
- `apptainer/af2.def`
  - 能力：container_recipes
  - 用途：为 AF2、BindCraft、Boltz2、dl_binder_design、FAMPNN、PyRosetta、RFDiffusion 提供容器构建定义
  - 复用状态：ready_for_review；类型：unknown
- `lib/RFDiffusionParams.groovy`
  - 能力：shared_helpers
  - 用途：共享参数封装与工具函数
  - 复用状态：ready_for_review；类型：unknown
- `bindsweeper/bindsweeper/main.py`
  - 能力：sweep_tooling
  - 用途：参数 sweep、验证与成功率统计的 Python 工具入口
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审计，未执行仓库代码或测试。
- 依赖未安装，Nextflow/Apptainer/外部工具链未验证。
- 大量 .pt 仅见路径，无法确认是权重、缓存还是特征张量。
- 数据/模型/容器的独立许可边界未完全明确。

## 仍未知

- benchmarkdata/ 与 binderscaffolds/ 资产的真实来源、生成方式与再分发许可。
- scripts/download_models.sh 可能拉取的外部模型/权重来源与许可。
- apptainer/*.def 是否夹带第三方软件、镜像或脚本的额外限制。
- 仓库未见 training_entrypoint/training_module；若有训练流程，可能不在冻结清单内。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
