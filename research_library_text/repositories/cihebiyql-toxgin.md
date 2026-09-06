# cihebiyql/toxgin

- **仓库：** [https://github.com/cihebiyql/toxgin](https://github.com/cihebiyql/toxgin)
- **固定 commit：** `f2b7e958e1e9ec183ed18b02816bef4e643bd00f`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 10

## 仓库摘要

仓库包含 peptide toxicity 的训练与推理流水线，但仅能做静态审查；未见显式评测脚本、检查点或许可证文件，数据来源与结构也只能从文件名推断。

## 可复用模块与资源

### datasets

- `train_sequence.csv`
  - 能力：training dataset
  - 用途：训练用序列数据输入
  - 复用状态：blocked；类型：unknown
- `test_sequence.csv`
  - 能力：test dataset
  - 用途：留出测试/评估用序列数据输入
  - 复用状态：blocked；类型：unknown
- `predict.csv`
  - 能力：inference input
  - 用途：推理/批量预测输入文件
  - 复用状态：blocked；类型：unknown
- `aaindex1.csv`
  - 能力：auxiliary feature table
  - 用途：预处理阶段引用的辅助特征表
  - 复用状态：unknown；类型：unknown

### inference

- `predict.py`
  - 能力：inference entrypoint
  - 用途：预测主入口
  - 复用状态：blocked；类型：code_entry
- `predict_preprocess.py`
  - 能力：inference preprocessing
  - 用途：推理前的数据整理与特征构建
  - 复用状态：blocked；类型：code_entry
- `predict.ipynb`
  - 能力：interactive inference notebook
  - 用途：Notebook 形式的预测流程说明或演示
  - 复用状态：blocked；类型：unknown
- `predict_preprocess.ipynb`
  - 能力：interactive preprocessing notebook
  - 用途：Notebook 形式的推理预处理流程说明或演示
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `preprocess.py`
  - 能力：shared preprocessing
  - 用途：训练与推理共用的数据加载/特征预处理逻辑
  - 复用状态：blocked；类型：code_entry

### training

- `train.py`
  - 能力：training entrypoint
  - 用途：模型训练主入口
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未执行仓库代码。
- 未安装依赖，无法验证训练或推理可运行性。
- 未运行测试，且未见 tests/CI 证据。
- 仓库未追踪许可证文件，直接复用受限。
- 未见显式 evaluation 脚本或 metric 报告。
- 未见 checkpoint/权重文件，无法确认模型是否随仓库分发。
- large blobs 可能为 promisor-only，部分数据/结构内容无法确认。

## 仍未知

- `train.py` 的具体模型结构、损失函数与超参数未知。
- `preprocess.py` 的完整特征工程与输入校验逻辑未知。
- `predict.py` 的输出格式、阈值与后处理策略未知。
- `train_structures/` 与 `test_structures/` 仅见 README，实际结构数据是否存在未知。
- `train_sequence.csv`、`test_sequence.csv`、`predict.csv` 的来源与许可未知。
- 是否存在未拉取的大文件或隐藏检查点未知。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
