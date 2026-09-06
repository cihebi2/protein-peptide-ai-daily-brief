# ievapudz/TemStaPro

- **仓库：** [https://github.com/ievapudz/TemStaPro](https://github.com/ievapudz/TemStaPro)
- **固定 commit：** `9f8ac693ad6db681cf0cdd135b7738a527a3cb92`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 15

## 仓库摘要

静态清单显示该仓库实现了 TemStaPro 的 protein thermostability 预测流程：以 protein language model 表征、MLP/流程代码和 45 个 .pt checkpoints 组成推理栈，并附带补充数据与 14 组回归测试；未见训练入口或运行验证。

## 可复用模块与资源

### checkpoints

- `models/mean_major_imbal-40_s1.pt`
  - 能力：模型权重/ensemble checkpoints
  - 用途：仓库内共 45 个 .pt 文件，命名覆盖 40–80 阈值与 1–5 seed，疑似 ensemble/ablation 权重。
  - 复用状态：partial；类型：model_weight

### datasets

- `data/SupplementaryMeltingTemperatureSourceData.xlsx`
  - 能力：补充源数据
  - 用途：热稳定性/熔解温度来源表，可能用于训练或整理。
  - 复用状态：partial；类型：unknown
- `data/SupplementaryTableCharacterizedC2EPs.xlsx`
  - 能力：已表征 C2EPs 表
  - 用途：已标注/已表征样本表，可能用于数据整理或 benchmark 输入。
  - 复用状态：partial；类型：unknown
- `data/SupplementaryFileC2EPsPredictions.tsv`
  - 能力：补充预测表
  - 用途：随仓库发布的预测结果/补充表，不一定是训练原始数据。
  - 复用状态：partial；类型：unknown
- `tests/data/extra_long_sequence.fasta`
  - 能力：FASTA 测试输入
  - 用途：测试长序列、多序列与替换符号等输入边界；同类 fixtures 还包括 `long_sequence.fasta`、`long_sequence_2.fasta`、`multiple_sequences.fasta`、`multiple_short_sequences.fasta`、`replaced_symbol_sequence.fasta`。
  - 复用状态：partial；类型：unknown

### evaluation

- `tests/cases/temstapro_001.sh`
  - 能力：回归测试/输出对照
  - 用途：14 个 shell case 与 14 个 .out golden files 验证 CLI 行为和边界输入。
  - 复用状态：partial；类型：code_entry

### inference

- `temstapro`
  - 能力：推理包/命令入口
  - 用途：承载序列评分/预测调用的包级入口；与 model_flow.py 和 checkpoints 共同构成推理链。
  - 复用状态：partial；类型：unknown
- `results.py`
  - 能力：结果后处理
  - 用途：可能用于汇总、格式化或导出预测结果。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `prottrans_models.py`
  - 能力：序列表示/特征提取
  - 用途：封装 protein language model 表征生成，供下游 thermostability predictor 调用。
  - 复用状态：ready_for_review；类型：code_entry
- `model_flow.py`
  - 能力：模型流程编排
  - 用途：连接表示层、预测头和推理流程。
  - 复用状态：ready_for_review；类型：code_entry
- `MLP.py`
  - 能力：MLP 预测头
  - 用途：提供多层感知机式分类/回归头。
  - 复用状态：ready_for_review；类型：code_entry
- `data_process.py`
  - 能力：数据预处理/加载
  - 用途：读取并整理 FASTA 与表格型输入。
  - 复用状态：ready_for_review；类型：code_entry
- `results.py`
  - 能力：结果整理
  - 用途：后处理或导出预测结果。
  - 复用状态：ready_for_review；类型：code_entry
- `temstapro`
  - 能力：包级入口/命名空间
  - 用途：作为推理包或命令入口的静态痕迹，可能承载序列评分调用。
  - 复用状态：partial；类型：unknown

### training

- `environment_CPU.yml`
  - 能力：训练/运行环境规格
  - 用途：CPU 依赖冻结，辅助复现训练或推理环境；仓库同时提供 environment_GPU.yml。
  - 复用状态：partial；类型：config

## 使用限制

- 仅做静态审查；未执行仓库代码、依赖安装或测试。
- clone_depth=1 且 large blobs over 5MiB may be promisor only。
- `path presence is not reproduction evidence`；不能据此证明可运行或可复现。
- 缺少已执行的 evaluation 记录，`tests/outputs/*.out` 只能说明存在 golden files。
- 未看到明确的 training entrypoint 或 config recipe，训练流程只能从文件名推断。

## 仍未知

- `temstapro` 目录/包的实际导出接口未展开，是否为 CLI 入口仍不确定。
- `data/*.xlsx` 的来源、拆分方式与标签口径未在本次静态清单中核实。
- 45 个 `.pt` 是否都为同一任务的正式发布权重、或包含中间检查点，尚不确定。
- `results.py`、`makefile` 的具体职责未读取，可能与评估/推理有关但未确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
