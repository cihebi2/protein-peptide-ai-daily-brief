# syc2017/kcdta

- **仓库：** [https://github.com/syc2017/kcdta](https://github.com/syc2017/kcdta)
- **固定 commit：** `3a611517a11f54882087e5f5aa63c866ca44761b`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 7

## 仓库摘要

仓库是一个面向 DTA 预测的 CNN 代码库，含训练模块、测试脚本与 DAVIS/KIBA 数据文件；未发现 LICENSE 或 checkpoint，且仅做静态审查。

## 可复用模块与资源

### datasets

- `KCDTA/data/davis/Y`
  - 能力：DAVIS dataset bundle
  - 用途：包含 Y、ligands_can.txt、proteins.txt 以及 train/test folds 的数据包。
  - 复用状态：unknown；类型：unknown
- `KCDTA/data/kiba/Y`
  - 能力：KIBA dataset bundle
  - 用途：包含 Y、ligands_can.txt、proteins.txt 以及 train/test folds 的数据包。
  - 复用状态：unknown；类型：unknown

### evaluation

- `KCDTA/test.py`
  - 能力：evaluation
  - 用途：测试/评估脚本；仅凭静态路径确认其存在，未执行。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `KCDTA/models/cnn.py`
  - 能力：model_architecture
  - 用途：CNN 模型定义，用于 drug-target affinity prediction 的前向结构。
  - 复用状态：blocked；类型：code_entry
- `KCDTA/create_davis_kiba.py`
  - 能力：dataset_preparation
  - 用途：数据整理/划分构造辅助脚本，可能用于 DAVIS/KIBA 数据预处理。
  - 复用状态：blocked；类型：code_entry
- `KCDTA/utils.py`
  - 能力：helper_library
  - 用途：共享工具函数模块；静态清单未细分其职责。
  - 复用状态：blocked；类型：code_entry

### training

- `KCDTA/training.py`
  - 能力：training
  - 用途：训练与参数更新逻辑的静态入口。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未运行代码、未验证训练或测试结果。
- 仓库未见 checkpoint/权重文件，无法判断是否存在可直接复现的已训练模型。
- 未发现 LICENSE/NOTICE，代码直接复用受限。
- 数据集文件存在，但 DAVIS/KIBA 的来源、分发协议与可再分发边界未从冻结清单确认。

## 仍未知

- test.py 是否同时承担 inference 入口，静态清单未确认。
- training.py 是完整 CLI 入口还是仅训练辅助模块，未从清单进一步验证。
- DAVIS/KIBA 是否为上游原始副本、清洗版或二次分发副本，未确认。
- 是否存在未被当前静态清单覆盖的大型模型文件或外部依赖，未确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
