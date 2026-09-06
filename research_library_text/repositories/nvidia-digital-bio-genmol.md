# NVIDIA-Digital-Bio/genmol

- **仓库：** [https://github.com/NVIDIA-Digital-Bio/genmol](https://github.com/NVIDIA-Digital-Bio/genmol)
- **固定 commit：** `add09fc83b7255bd09c797e527c0f4b51f5fb7c1`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 19

## 仓库摘要

仓库实现了 GenMol 的训练、预处理、采样与 lead/PMO 评测流水线；当前未发现仓库级许可证与可核验 checkpoint，直接复用受限。

## 可复用模块与资源

### datasets

- `data/fragments.csv`
  - 能力：bundled_training_data
  - 用途：分子 fragments 数据，显然用于预处理/训练输入构建。
  - 复用状态：blocked；类型：unknown
- `scripts/exps/pmo/vocab/drd2.csv`
  - 能力：evaluation_benchmark_tables
  - 用途：PMO 评测任务词表/目标表集合，包含 drd2、qed、rediscovery、similarity、scaffold 等 CSV。
  - 复用状态：blocked；类型：unknown
- `scripts/exps/lead/docking/actives.csv`
  - 能力：docking_benchmark_inputs
  - 用途：lead docking 评测输入集合，包含 actives.csv 与多个 receptor PDBQT 文件。
  - 复用状态：blocked；类型：unknown

### evaluation

- `scripts/exps/lead/eval.py`
  - 能力：evaluation_entrypoint
  - 用途：lead 任务评测。
  - 复用状态：blocked；类型：code_entry
- `scripts/exps/pmo/eval.py`
  - 能力：evaluation_entrypoint
  - 用途：PMO 任务评测。
  - 复用状态：blocked；类型：code_entry
- `scripts/exps/lead/docking/docking.py`
  - 能力：docking_helper
  - 用途：lead docking 评测辅助逻辑。
  - 复用状态：blocked；类型：code_entry

### inference

- `src/genmol/sampler.py`
  - 能力：sampling_helper
  - 用途：模型采样与生成辅助。
  - 复用状态：blocked；类型：code_entry
- `scripts/exps/denovo/run.py`
  - 能力：task_runner
  - 用途：de novo 生成/运行入口，可能承接推理式候选生成流程。
  - 复用状态：blocked；类型：code_entry
- `scripts/exps/frag/run.py`
  - 能力：task_runner
  - 用途：fragment 场景运行入口，可能承接推理式生成流程。
  - 复用状态：blocked；类型：code_entry
- `scripts/exps/pmo/main/genmol/run.py`
  - 能力：task_runner
  - 用途：PMO 场景下 GenMol 任务运行入口，偏生成/优化执行。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `src/genmol/model.py`
  - 能力：model_architecture
  - 用途：GenMol 核心分子生成模型定义；是方法主体的代码入口。
  - 复用状态：blocked；类型：code_entry
- `scripts/train.py`
  - 能力：training_entrypoint
  - 用途：训练主入口与训练模块；用于启动模型训练流程。
  - 复用状态：blocked；类型：code_entry
- `scripts/preprocess_data.py`
  - 能力：data_preprocessing
  - 用途：训练前数据预处理/装载。
  - 复用状态：blocked；类型：code_entry
- `configs/base.yaml`
  - 能力：configuration_recipe
  - 用途：基础实验与训练配置。
  - 复用状态：blocked；类型：config
- `scripts/exps/lead/eval.py`
  - 能力：evaluation_pipeline
  - 用途：lead 场景评测入口，配合 docking 资源做候选评分/评估。
  - 复用状态：blocked；类型：code_entry
- `scripts/exps/pmo/eval.py`
  - 能力：evaluation_pipeline
  - 用途：PMO 场景评测入口，覆盖优化任务的结果评估。
  - 复用状态：blocked；类型：code_entry
- `src/genmol/sampler.py`
  - 能力：inference_or_sampling_helper
  - 用途：采样/生成辅助模块；静态路径存在，但未见独立 inference CLI 被冻结清单单列。
  - 复用状态：blocked；类型：code_entry

### training

- `scripts/train.py`
  - 能力：training_entrypoint
  - 用途：主训练脚本。
  - 复用状态：blocked；类型：code_entry
- `configs/base.yaml`
  - 能力：training_recipe
  - 用途：训练超参与实验默认配置。
  - 复用状态：blocked；类型：config

## 使用限制

- 仅做静态清单审查，未执行代码。
- 依赖未安装，无法验证运行时行为。
- 测试未运行。
- 未初始化子模块。
- 存在大文件与 promisor-only 风险，部分 blob 可能不完整。
- 路径存在不等于可复现或可复用。

## 仍未知

- 未能从冻结清单确认 `src/genmol/sampler.py` 与各 `scripts/exps/*/run.py` 的实际调用链，只能按路径名判断其可能承担生成/推理流程。
- `data/fragments.csv` 与 `data/len.pk` 的生成来源、清洗逻辑和可再分发性未被静态证实。
- 仓库中有多个第三方许可子文件，但它们是否覆盖全部 vendored 组件与二进制依赖（例如 `qvina02`）仍需逐文件核验。
- 冻结清单未显示任何明确的 model checkpoint 文件；若权重通过外部下载获得，则不在本次静态盘点内。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
