# roucairolmilo/drugsynthmc

- **仓库：** [https://github.com/roucairolmilo/drugsynthmc](https://github.com/roucairolmilo/drugsynthmc)
- **固定 commit：** `3d17d1b93f39da1d54712f421f615d8d1f0d8170`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 16

## 仓库摘要

仓库是 DrugSynthMC 的静态冻结快照，包含多种分子生成/搜索算法、SMILES 神经模型与 n-gram 先验，以及若干生成结果；未见训练入口或许可证，因此仅能做受限静态复核。

## 可复用模块与资源

### checkpoints

- `Neural/SMILES/saved_model.pb`
  - 能力：tensorflow_savedmodel_smiles
  - 用途：TensorFlow SavedModel 权重/变量，似为 SMILES 生成模型 checkpoint。
  - 复用状态：blocked；类型：model_weight
- `Neural/SMILESexplicit/saved_model.pb`
  - 能力：tensorflow_savedmodel_smilesexplicit
  - 用途：另一套 TensorFlow SavedModel checkpoint。
  - 复用状态：blocked；类型：model_weight
- `Neural/SMILESexplicit_shortcuts/saved_model.pb`
  - 能力：tensorflow_savedmodel_smilesexplicit_shortcuts
  - 用途：带 shortcuts 变体的 TensorFlow SavedModel checkpoint。
  - 复用状态：blocked；类型：model_weight

### datasets

- `ngrams/ngrams.json`
  - 能力：ngram_priors_general
  - 用途：通用 n-gram 先验表，供生成/搜索时作为统计先验。
  - 复用状态：blocked；类型：config
- `ngrams/fda_ngrams_1.json`
  - 能力：ngram_priors_fda
  - 用途：FDA 相关 n-gram 先验及其 shortcuts/cycles 变体。
  - 复用状态：blocked；类型：config
- `ngrams/zinc_ngrams_1.json`
  - 能力：ngram_priors_zinc
  - 用途：ZINC 相关 n-gram 先验及其 shortcuts 变体。
  - 复用状态：blocked；类型：config

### evaluation

- `results/SMILES generated/NMCS/enforced.txt`
  - 能力：nmcs_outputs
  - 用途：不同约束/先验设置下的 NMCS 输出文本与 HDF5 记录。
  - 复用状态：blocked；类型：unknown
- `results/SMILES generated/PUCT/enforced.txt`
  - 能力：puct_outputs
  - 用途：PUCT 输出文本。
  - 复用状态：blocked；类型：unknown
- `results/SMILES generated/Sampling/enforced.txt`
  - 能力：sampling_outputs
  - 用途：Sampling 输出文本与 neural1K 结果。
  - 复用状态：blocked；类型：unknown

### inference

- `src/main.rs`
  - 能力：generation_inference_entrypoint
  - 用途：推理/生成入口，调度各类搜索策略与模型。
  - 复用状态：blocked；类型：unknown
- `src/tools/NNreader.rs`
  - 能力：neural_model_loading
  - 用途：读取神经 SMILES 模型并服务于推理。
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `src/methods/BFS.rs`
  - 能力：core_search_methods
  - 用途：实现 BFS、UCT、GRAVE、PUCT、NMCS、NMCSparallel、lazyNMCS 与 CSGUCT 等核心分子生成搜索策略。
  - 复用状态：blocked；类型：unknown
- `src/models/SMILESgen.rs`
  - 能力：smiles_model_wrapper
  - 用途：SMILES 生成模型封装与模块组织，配合神经网络推理。
  - 复用状态：blocked；类型：unknown
- `src/tools/NNreader.rs`
  - 能力：utility_and_io_modules
  - 用途：NNreader、calc 与 resultSaver 等辅助模块，支持模型读取、计算与结果保存。
  - 复用状态：blocked；类型：unknown
- `src/main.rs`
  - 能力：program_entrypoint
  - 用途：程序入口，组织生成与搜索流程。
  - 复用状态：blocked；类型：unknown
- `Cargo.toml`
  - 能力：build_manifest
  - 用途：Rust 依赖声明与构建配置。
  - 复用状态：blocked；类型：config

## 使用限制

- 仅做静态审阅，未执行代码、测试或依赖安装。
- 仓库未见 LICENSE，直接复用受限。
- TensorFlow 权重与 n-gram 先验的上游来源和许可未能从冻结清单确认。
- results/SMILES generated/ 只能证明存在输出文件，不能证明评测已复现。

## 仍未知

- 未发现明确的 training_entrypoint 或 training_module，训练流程无法确认。
- Neural/ 下的 SavedModel 是自训、导入还是第三方附带，无法确认。
- ngrams/ 的构建语料与预处理流程无法确认。
- 各方法的定量指标、基线和复现设置无法仅据文件清单确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
