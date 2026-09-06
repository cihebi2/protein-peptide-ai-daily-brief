# goldriver0/libre

- **仓库：** [https://github.com/goldriver0/libre](https://github.com/goldriver0/libre)
- **固定 commit：** `e9151a85bab2d05b67b953bc55a74c780aa2bf24`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 9

## 仓库摘要

该仓库是 LiBRe 的静态参考实现，包含模型结构、特征预处理、训练/评估脚本、示例训练/测试 CSV 和一个 `models/model.pt` 权重；冻结清单未见 LICENSE 或独立推理入口，因此只能做资产盘点，不能据此认定可复用授权或复现结果。

## 可复用模块与资源

### checkpoints

- `models/model.pt`
  - 能力：model_weight
  - 用途：冻结的模型权重文件，可用于加载后推理或继续训练。
  - 复用状态：blocked；类型：model_weight

### datasets

- `data/train/train_example.csv`
  - 能力：training_data
  - 用途：训练示例样本。
  - 复用状态：blocked；类型：unknown
- `data/test/test_example.csv`
  - 能力：test_data
  - 用途：测试示例样本。
  - 复用状态：blocked；类型：unknown

### evaluation

- `src/evaluate.py`
  - 能力：evaluation_entrypoint
  - 用途：离线评估脚本，用于验证或指标计算。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `src/models/libre.py`
  - 能力：model_architecture
  - 用途：定义 LiBRe 主模型结构，供训练与预测复用。
  - 复用状态：blocked；类型：code_entry
- `data/ligand_featurizer.py`
  - 能力：data_loader
  - 用途：配体特征化与预处理。
  - 复用状态：blocked；类型：code_entry
- `data/residue_embeddings.py`
  - 能力：data_loader
  - 用途：残基嵌入生成与预处理。
  - 复用状态：blocked；类型：code_entry
- `src/utils.py`
  - 能力：utility
  - 用途：训练/评估通用辅助函数。
  - 复用状态：blocked；类型：code_entry

### training

- `src/train.py`
  - 能力：training_entrypoint
  - 用途：训练入口，组织数据读取、优化与保存。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态分析，未执行仓库代码。
- 未安装依赖，无法验证训练、评估或推理行为。
- 未发现独立 inference 入口；推理流程是否封装在训练脚本中无法确认。
- 仅见 `train_example.csv` 与 `test_example.csv` 示例数据，不能证明完整数据集规模、划分或授权。
- 仓库未检出 LICENSE，代码、数据与权重的可再分发边界均未被授权文本明确覆盖。
- `.ipynb_checkpoints` 与 `.pyc` 路径同时存在，是否为重复/过期副本无法静态确认。

## 仍未知

- `models/model.pt` 是否由当前 `src/train.py` 与 `src/models/libre.py` 生成无法验证。
- 训练超参数、随机种子、数据预处理细节与实际指标未能从冻结证据中确认。
- `data/train/train_example.csv` 与 `data/test/test_example.csv` 是否仅为演示样本而非正式评测集尚不明确。
- `src/.ipynb_checkpoints/*` 与 `src/models/.ipynb_checkpoints/*` 是否与主文件一致或仅为自动保存副本无法判断。
- 仓库中未见 config_recipe，运行时参数来源不明。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
