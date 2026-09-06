# hysonlab/directed_evolution

- **仓库：** [https://github.com/hysonlab/directed_evolution](https://github.com/hysonlab/directed_evolution)
- **固定 commit：** `0f2845a50b33e0629ce776b37381829a53873448`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 22

## 仓库摘要

仓库以 GPL-3.0 代码实现蛋白 directed evolution 的预处理、训练与搜索；冻结清单显示 8 个数据集、训练/离散搜索入口和空 checkpoint 目录，但未见独立评估实现或可验证权重。

## 可复用模块与资源

### checkpoints

- `exps/checkpoints/.gitkeep`
  - 能力：checkpoint_placeholder
  - 用途：权重目录占位；未见实际 checkpoint 文件
  - 复用状态：blocked；类型：unknown

### datasets

- `preprocessed_data/AAV/AAV.csv`
  - 能力：protein_fitness_dataset
  - 用途：AAV 监督数据；配套 reference sequence 用于起始序列定义
  - 复用状态：unknown；类型：unknown
- `preprocessed_data/AMIE/AMIE.csv`
  - 能力：protein_fitness_dataset
  - 用途：AMIE 监督数据；配套 reference sequence 用于起始序列定义
  - 复用状态：unknown；类型：unknown
- `preprocessed_data/E4B/E4B.csv`
  - 能力：protein_fitness_dataset
  - 用途：E4B 监督数据；配套 reference sequence 用于起始序列定义
  - 复用状态：unknown；类型：unknown
- `preprocessed_data/LGK/LGK.csv`
  - 能力：protein_fitness_dataset
  - 用途：LGK 监督数据；配套 reference sequence 用于起始序列定义
  - 复用状态：unknown；类型：unknown
- `preprocessed_data/Pab1/Pab1.csv`
  - 能力：protein_fitness_dataset
  - 用途：Pab1 监督数据；配套 reference sequence 用于起始序列定义
  - 复用状态：unknown；类型：unknown
- `preprocessed_data/TEM/TEM.csv`
  - 能力：protein_fitness_dataset
  - 用途：TEM 监督数据；配套 reference sequence 用于起始序列定义
  - 复用状态：unknown；类型：unknown
- `preprocessed_data/UBE2I/UBE2I.csv`
  - 能力：protein_fitness_dataset
  - 用途：UBE2I 监督数据；配套 reference sequence 用于起始序列定义
  - 复用状态：unknown；类型：unknown
- `preprocessed_data/avGFP/avGFP.csv`
  - 能力：protein_fitness_dataset
  - 用途：avGFP 监督数据；配套 reference sequence 用于起始序列定义
  - 复用状态：unknown；类型：unknown

### evaluation

- `exps/results/.gitkeep`
  - 能力：evaluation_artifact_placeholder
  - 用途：结果目录占位；未见独立评估脚本或指标实现
  - 复用状态：blocked；类型：unknown

### inference

- `de/directed_evolution.py`
  - 能力：search_inference
  - 用途：离散 directed evolution 迭代与候选排序流程
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/run_discrete_de.py`
  - 能力：search_inference
  - 用途：命令行运行封装
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `scripts/preprocess/preprocess_AAV.py`
  - 能力：data_loader
  - 用途：AAV 预处理；同目录 8 个蛋白数据预处理脚本可生成 preprocessed_data/*
  - 复用状态：ready_for_review；类型：code_entry
- `de/predictors/attention/decoder.py`
  - 能力：model_architecture
  - 用途：attention decoder 模型主体
  - 复用状态：ready_for_review；类型：code_entry
- `de/samplers/models/esm.py`
  - 能力：model_architecture
  - 用途：ESM-based sampler/representation wrapper
  - 复用状态：ready_for_review；类型：code_entry
- `de/predictors/oracle.py`
  - 能力：oracle
  - 用途：fitness/score oracle 封装
  - 复用状态：ready_for_review；类型：code_entry
- `de/common/io_utils.py`
  - 能力：utility
  - 用途：I/O 与序列化辅助函数
  - 复用状态：ready_for_review；类型：code_entry
- `de/common/utils.py`
  - 能力：utility
  - 用途：通用工具函数
  - 复用状态：ready_for_review；类型：code_entry
- `de/dataio/proteins.py`
  - 能力：protein_io
  - 用途：蛋白序列与表型数据读写
  - 复用状态：ready_for_review；类型：code_entry
- `de/samplers/maskers/base.py`
  - 能力：masking_strategy
  - 用途：随机/重要性/基类 masking 策略家族
  - 复用状态：ready_for_review；类型：code_entry

### training

- `scripts/train.sh`
  - 能力：training_entrypoint
  - 用途：训练启动 shell
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/train_decoder.py`
  - 能力：training_module
  - 用途：decoder 训练主脚本
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅基于 frozen inventory 静态审查，未执行代码、未安装依赖、未跑测试。
- `exps/checkpoints/.gitkeep` 只是目录占位，不构成可用模型权重。
- tracked 数据文件未见单独许可文本，代码许可不能自动外推到 data/model artifacts。
- 无法验证 `scripts/train.sh` 与 `scripts/run_discrete_de.py` 的真实运行结果。

## 仍未知

- `preprocessed_data/*` 的上游原始数据来源与授权未明。
- 是否存在未跟踪的 checkpoint 或外部下载资源未知。
- 是否有独立 evaluation 指标实现或实验配置未纳入 tracked_paths 未知。
- `de/samplers/models/esm.py` 依赖的 ESM 权重/版本无法从静态清单确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
