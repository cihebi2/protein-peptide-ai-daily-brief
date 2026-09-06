# AlexColagrande/HO-FNO

- **仓库：** [https://github.com/AlexColagrande/HO-FNO](https://github.com/AlexColagrande/HO-FNO)
- **固定 commit：** `3fadeccf875e974e038338bea02c0d6761cb170a`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 19

## 仓库摘要

该仓库是 HO-FNO 的静态代码实现，包含 FNO/HO-FNO 模型、谱卷积层、若干 PDE 基准驱动脚本，以及 polynomial_poisson 的合成数据生成与训练/评估脚本；未发现 LICENSE、未见已跟踪检查点，且所有结论均受限于仅做静态清点，不能证明实际运行或复现。

## 可复用模块与资源

### datasets

- `polynomial_poisson/create_dataset_polynomial_source_poisson_p2.py`
  - 能力：dataset_generation
  - 用途：生成 polynomial_source_poisson 的合成 Poisson 数据
  - 复用状态：blocked；类型：code_entry
- `polynomial_poisson/generated/polynomial_source_poisson_p1/metadata.json`
  - 能力：dataset_metadata
  - 用途：记录 p1 合成数据集元数据与生成参数
  - 复用状态：blocked；类型：config
- `polynomial_poisson/generated/polynomial_source_poisson_p2/metadata.json`
  - 能力：dataset_metadata
  - 用途：记录 p2 合成数据集元数据与生成参数
  - 复用状态：blocked；类型：config
- `polynomial_poisson/generated/polynomial_source_poisson_p3/metadata.json`
  - 能力：dataset_metadata
  - 用途：记录 p3 合成数据集元数据与生成参数
  - 复用状态：blocked；类型：config
- `polynomial_poisson/generated/polynomial_source_poisson_p5/metadata.json`
  - 能力：dataset_metadata
  - 用途：记录 p5 合成数据集元数据与生成参数
  - 复用状态：blocked；类型：config

### evaluation

- `utils/testloss.py`
  - 能力：evaluation_helper
  - 用途：测试损失/评估指标辅助
  - 复用状态：blocked；类型：code_entry
- `assets/standard_benchmarks_table.png`
  - 能力：evaluation_artifact
  - 用途：标准基准结果展示图/静态评测产物
  - 复用状态：blocked；类型：unknown
- `assets/efficiency_analysis.png`
  - 能力：evaluation_artifact
  - 用途：效率分析图/静态评测产物
  - 复用状态：blocked；类型：unknown

### inference

- `hofno_airfoil.py`
  - 能力：inference_entrypoint
  - 用途：Airfoil 任务的推理/基准驱动脚本；静态上不能区分是否同时承担训练或评估
  - 复用状态：blocked；类型：code_entry
- `hofno_pipe.py`
  - 能力：inference_entrypoint
  - 用途：Pipe 任务的推理/基准驱动脚本；静态上不能区分是否同时承担训练或评估
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `models/FNO.py`
  - 能力：model_architecture
  - 用途：基础 FNO 模型骨架与频域建模组件
  - 复用状态：blocked；类型：code_entry
- `models/HO_FNO.py`
  - 能力：model_architecture
  - 用途：HO-FNO 主模型实现
  - 复用状态：blocked；类型：code_entry
- `models/HO_FNO_pipe.py`
  - 能力：model_architecture
  - 用途：面向 pipe 任务的 HO-FNO 变体
  - 复用状态：blocked；类型：code_entry
- `layers/spectral_convs.py`
  - 能力：model_architecture
  - 用途：谱卷积算子模块，供模型主体调用
  - 复用状态：blocked；类型：code_entry
- `utils/normalizer.py`
  - 能力：utility
  - 用途：归一化/反归一化辅助
  - 复用状态：blocked；类型：code_entry
- `utils/utilities.py`
  - 能力：utility
  - 用途：通用辅助函数
  - 复用状态：blocked；类型：code_entry

### training

- `polynomial_poisson/train_and_eval_models.py`
  - 能力：training_module
  - 用途：polynomial_poisson 任务的训练与评估主流程
  - 复用状态：blocked；类型：code_entry
- `polynomial_poisson/run_all_experiments.sh`
  - 能力：training_entrypoint
  - 用途：批量启动 polynomial_poisson 实验
  - 复用状态：blocked；类型：code_entry
- `scripts/HO-FNO_Airfoil.sh`
  - 能力：training_entrypoint
  - 用途：Airfoil 基准实验启动脚本；同类脚本还包括 scripts/HO-FNO_Darcy.sh、scripts/HO-FNO_NS.sh、scripts/HO-FNO_Pipe.sh
  - 复用状态：blocked；类型：code_entry

## 使用限制

- not_executed_static_analysis_only
- dependencies_not_installed
- repository_code_not_executed
- tests_not_run
- submodules_not_initialized
- large_blobs_over_5MiB_may_be_promisor_only
- path_presence_is_not_reproduction_evidence

## 仍未知

- 未执行任何脚本，`hofno_*.py` 与 `scripts/HO-FNO_*.sh` 的实际角色只能按文件名和路径推断，无法确认是否分别对应训练、推理或评估。
- `polynomial_poisson/generated/*/metadata.json` 只证明元数据存在，未见对应原始样本、分割文件或完整数据包。
- 仓库没有 tracked checkpoint；但由于浅克隆与 promisor-only 大 blob 限制，不能排除外部或未取回的权重文件。
- 未核验第三方依赖的许可证兼容性；`requirements.txt` 仅列出依赖，不代表整体可再分发。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
