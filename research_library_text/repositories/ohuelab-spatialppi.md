# ohuelab/spatialppi

- **仓库：** [https://github.com/ohuelab/spatialppi](https://github.com/ohuelab/spatialppi)
- **固定 commit：** `28249dfd884f80a8f3aa2a9d53ea568096c0935f`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 18

## 仓库摘要

仓库是 SpatialPPI 的静态代码包：有训练/测试与结构处理脚本，内置三份 JSON 数据，未见 checkpoint；代码许可为 Apache-2.0，但数据许可未分离确认。

## 可复用模块与资源

### datasets

- `data/dataset1200.json`
  - 能力：bundled_dataset
  - 用途：Bundled JSON dataset shard for model training or benchmarking.
  - 复用状态：unknown；类型：config
- `data/dataset_append_1142.json`
  - 能力：bundled_dataset
  - 用途：Bundled JSON dataset extension or companion shard.
  - 复用状态：unknown；类型：config
- `data/example_dataset.json`
  - 能力：demo_dataset
  - 用途：Small example dataset for usage demonstration or smoke tests.
  - 复用状态：unknown；类型：config

### evaluation

- `test.py`
  - 能力：evaluation_entrypoint
  - 用途：Testing or validation driver inferred from filename only; exact runtime role is not confirmed by static inventory.
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `utils/interface.py`
  - 能力：input_interface
  - 用途：Prediction-side interface around protein pair inputs.
  - 复用状态：ready_for_review；类型：code_entry
- `utils/readPDB.py`
  - 能力：pdb_parsing
  - 用途：Parsing protein structure files for inference inputs.
  - 复用状态：ready_for_review；类型：code_entry
- `utils/encode.py`
  - 能力：feature_encoding
  - 用途：Encoding structure features at prediction time.
  - 复用状态：ready_for_review；类型：code_entry
- `utils/structure.py`
  - 能力：structure_utils
  - 用途：Structure manipulation helpers used around prediction.
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `utils/densenet3d.py`
  - 能力：model_backbone
  - 用途：3D DenseNet backbone implementation for PPI scoring.
  - 复用状态：ready_for_review；类型：code_entry
- `utils/resnet3d.py`
  - 能力：model_backbone
  - 用途：3D ResNet backbone implementation for PPI scoring.
  - 复用状态：ready_for_review；类型：code_entry
- `utils/readPDB.py`
  - 能力：feature_pipeline
  - 用途：PDB structure parsing for protein inputs.
  - 复用状态：ready_for_review；类型：code_entry
- `utils/encode.py`
  - 能力：feature_pipeline
  - 用途：Structure-to-feature encoding helpers for model input.
  - 复用状态：ready_for_review；类型：code_entry
- `utils/interface.py`
  - 能力：feature_pipeline
  - 用途：Input/interface handling around pairwise protein structures.
  - 复用状态：ready_for_review；类型：code_entry
- `utils/record.py`
  - 能力：data_management
  - 用途：Experiment/result recording helper.
  - 复用状态：ready_for_review；类型：code_entry

### training

- `train.py`
  - 能力：training_entrypoint
  - 用途：Training driver for the SpatialPPI model.
  - 复用状态：ready_for_review；类型：code_entry
- `preprocess.py`
  - 能力：data_preprocessing
  - 用途：Pretraining or training-time data preparation script.
  - 复用状态：ready_for_review；类型：code_entry
- `utils/dataset.py`
  - 能力：dataset_loader
  - 用途：Dataset abstraction and loader used by training.
  - 复用状态：ready_for_review；类型：code_entry
- `utils/augmentation.py`
  - 能力：augmentation
  - 用途：Training-time data augmentation helper.
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未执行仓库代码。
- 依赖未安装，无法验证导入链或运行路径。
- 未运行测试，也未验证 test.py 的真实语义。
- 未发现 checkpoint 文件；models/ 目录仅见占位文件。
- 路径存在不等于可复现性或可运行性。

## 仍未知

- 三份 JSON 数据的来源、标注协议与再分发权限未在冻结证据中明确。
- test.py 更偏 evaluation 还是 inference，静态证据不足以最终判定。
- densenet3d/resnet3d 的具体超参数与训练配置未从冻结清单中确认。
- 是否存在未纳入冻结清单的大型权重或外部资源，无法从静态审查确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
