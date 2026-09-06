# mansoor181/epiformer

- **仓库：** [https://github.com/mansoor181/epiformer](https://github.com/mansoor181/epiformer)
- **固定 commit：** `f420745e28adf759ccdab327d06459da9a9382fe`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 13

## 仓库摘要

仓库包含 EpiFormer 的模型、数据预处理、训练、推理、评估与两份 checkpoint 权重；静态清单未见 bundled raw data，也未发现 LICENSE，因而只能做文件级盘点，不能证明可复现或已执行。

## 可复用模块与资源

### checkpoints

- `checkpoints/epiformer-epitope-group/epiformer_best.pt`
  - 能力：model_weight
  - 用途：epitope-group 版本最佳权重。
  - 复用状态：blocked；类型：model_weight
- `checkpoints/epiformer-epitope-ratio/epiformer_best.pt`
  - 能力：model_weight
  - 用途：epitope-ratio 版本最佳权重。
  - 复用状态：blocked；类型：model_weight
- `CHECKPOINTS.md`
  - 能力：checkpoint_catalog
  - 用途：记录 checkpoint 目录、命名与对应示意图，便于定位权重；不等于权重本体。
  - 复用状态：blocked；类型：checkpoint_adjacent

### datasets

- `data/data_splits.py`
  - 能力：dataset_split_and_reindex_pipeline
  - 用途：抗体/抗原复杂物切分、修正与重编号流程；仓库未见 bundled raw data。
  - 复用状态：blocked；类型：code_entry
- `data/embed_esm2.py`
  - 能力：feature_precompute_inputs
  - 用途：序列 embedding、Antiberty/ESM/PSSM 等输入特征预计算；用于构造模型输入。
  - 复用状态：blocked；类型：code_entry

### evaluation

- `evaluate.py`
  - 能力：evaluation_entrypoint
  - 用途：离线评估入口。
  - 复用状态：blocked；类型：code_entry

### inference

- `inference.py`
  - 能力：inference_entrypoint
  - 用途：推理入口。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `model/epiformer.py`
  - 能力：model_architecture
  - 用途：EpiFormer 主体架构，实现抗原-抗体交互建模与 epitope 预测。
  - 复用状态：blocked；类型：code_entry
- `conf/model/model.yaml`
  - 能力：model_config
  - 用途：模型结构与超参配置；另有 `conf/model/evoformer.yaml`。
  - 复用状态：blocked；类型：config
- `trainer.py`
  - 能力：training_orchestration
  - 用途：训练循环与批量运行入口；配套训练配置和 shell 脚本。
  - 复用状态：blocked；类型：code_entry
- `inference.py`
  - 能力：inference_pipeline
  - 用途：推理入口；与 `data/generate_pssm.py` 配合生成输入特征并输出预测。
  - 复用状态：blocked；类型：code_entry
- `evaluate.py`
  - 能力：evaluation_metrics
  - 用途：离线评估入口；`model/metric.py` 提供指标实现。
  - 复用状态：blocked；类型：code_entry

### training

- `trainer.py`
  - 能力：training_entrypoint
  - 用途：训练入口与多 seed / sweep 运行组织。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态盘点，未执行仓库代码。
- 依赖未安装，无法验证导入与运行时行为。
- 测试未运行，也未见 CI 证据。
- submodules 未初始化，外部依赖内容可能缺失。
- large blobs over 5MiB may be promisor-only，checkpoint 内容未验证。
- path presence is not reproduction evidence。

## 仍未知

- 原始训练/验证/测试数据的具体来源与许可未在静态清单中明确。
- `epiformer_best.pt` 的训练轮次、评估集与最佳判据未被执行验证。
- 各脚本的命令行参数与默认值未逐文件读取，无法确认完整运行路径。
- 指标定义、阈值与报告数值只能依据文件名推断，未做运行复核。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
