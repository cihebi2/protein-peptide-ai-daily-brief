# Bamrock/DeepTrace

- **仓库：** [https://github.com/Bamrock/DeepTrace](https://github.com/Bamrock/DeepTrace)
- **固定 commit：** `cb4ce3be2175eaca5b5d2d9ed51e695691509ae9`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 16

## 仓库摘要

该仓库是论文配套代码与数据镜像：包含预训练、微调、预测脚本，少量文本/TSV 数据，以及一套 vendored 的 transformers 代码；未发现 LICENSE 或 checkpoint，因此只能做静态、保守的复用边界判断。

## 可复用模块与资源

### datasets

- `data/pretrain_data/train.txt`
  - 能力：pretraining dataset
  - 用途：预训练训练集文本
  - 复用状态：blocked；类型：unknown
- `data/pretrain_data/test.txt`
  - 能力：pretraining dataset
  - 用途：预训练留出/测试文本
  - 复用状态：blocked；类型：unknown
- `data/fine_tune_data/train.txt`
  - 能力：fine-tuning dataset
  - 用途：微调训练集文本
  - 复用状态：blocked；类型：unknown
- `data/fine_tune_data/dev.txt`
  - 能力：fine-tuning dataset
  - 用途：微调验证集文本
  - 复用状态：blocked；类型：unknown
- `data/prediction_data/pred.tsv`
  - 能力：inference dataset
  - 用途：批量预测输入表
  - 复用状态：blocked；类型：unknown

### evaluation

- `transformers/data/metrics/squad_metrics.py`
  - 能力：evaluation_metrics
  - 用途：SQuAD 风格评测指标实现
  - 复用状态：blocked；类型：code_entry

### inference

- `prediction.py`
  - 能力：inference_entrypoint
  - 用途：批量预测入口
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `transformers/modeling_encoder_decoder.py`
  - 能力：model_architecture
  - 用途：encoder-decoder 主结构，支撑训练/推断复用
  - 复用状态：blocked；类型：code_entry
- `transformers/utils_encoder_decoder.py`
  - 能力：model_architecture
  - 用途：encoder-decoder 辅助工具
  - 复用状态：blocked；类型：code_entry
- `transformers/dnabert-config/bert-config-1/config.json`
  - 能力：tokenizer/config bundle
  - 用途：DNA BERT 配置与 tokenizer 资产；目录中有 1-6 六套同构 bundle
  - 复用状态：blocked；类型：config
- `transformers/data/processors/glue.py`
  - 能力：data_loader
  - 用途：通用 GLUE 数据处理器
  - 复用状态：blocked；类型：code_entry
- `transformers/data/processors/squad.py`
  - 能力：data_loader
  - 用途：通用 SQuAD 数据处理器
  - 复用状态：blocked；类型：code_entry
- `transformers/data/processors/xnli.py`
  - 能力：data_loader
  - 用途：通用 XNLI 数据处理器
  - 复用状态：blocked；类型：code_entry

### training

- `pretrain.py`
  - 能力：training_entrypoint
  - 用途：预训练入口
  - 复用状态：blocked；类型：code_entry
- `fine_tuning.py`
  - 能力：training_entrypoint
  - 用途：微调入口
  - 复用状态：blocked；类型：code_entry
- `transformers/commands/train.py`
  - 能力：training_module
  - 用途：通用训练 CLI/命令模块
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未安装依赖、未运行训练/推断/评测。
- 仓库级 LICENSE 未发现，代码/数据/模型配置的直接复用均不能默认放行。
- 未发现可验证的模型权重或 checkpoint。
- `transformers/` 目录看起来是 vendored 依赖，但上游版本和改动范围未核验。

## 仍未知

- `data/pretrain_data/test.txt` 更像测试或留出集，但其确切用途未从静态清单确认。
- `transformers/dnabert-config/bert-config-*` 是否来自外部分发版或仓库自生成未核验。
- `fine_tuning.py` 与 `prediction.py` 的精确 I/O 协议未核验。
- bundled 数据的来源、标注规范与许可未能从冻结清单确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
