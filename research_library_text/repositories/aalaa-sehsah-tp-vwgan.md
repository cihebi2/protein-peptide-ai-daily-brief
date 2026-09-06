# aalaa-sehsah/tp-vwgan

- **仓库：** [https://github.com/aalaa-sehsah/tp-vwgan](https://github.com/aalaa-sehsah/tp-vwgan)
- **固定 commit：** `ff95310a16960c0bc2448e6e233189bb10a42faf`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 7

## 仓库摘要

该仓库是一个面向蛋白三级结构生成的静态代码仓库，已识别模型定义、训练入口、数据下载/预处理脚本和依赖清单；未见冻结的数据集、checkpoint、显式评估或推理资产，且仅能做路径级审查，复现未验证。

## 可复用模块与资源

### reusable_assets

- `0-install-requirements.sh`
  - 能力：environment_setup
  - 用途：安装/初始化运行环境（仅路径级推断）
  - 复用状态：partial；类型：code_entry
- `1-download-database.sh`
  - 能力：data_loader
  - 用途：下载外部数据库或原始输入数据（仅路径级推断）
  - 复用状态：partial；类型：code_entry
- `2-create-datasets.sh`
  - 能力：dataset_preparation
  - 用途：构建或整理训练数据集的脚本（仅路径级推断）
  - 复用状态：partial；类型：code_entry
- `3-train-model.sh`
  - 能力：training_wrapper
  - 用途：封装训练命令的脚本（仅路径级推断）
  - 复用状态：partial；类型：code_entry
- `TP-VWGAN/models.py`
  - 能力：model_architecture
  - 用途：定义生成模型结构
  - 复用状态：ready_for_review；类型：code_entry
- `TP-VWGAN/requirements.txt`
  - 能力：dependencies
  - 用途：列出 Python 依赖清单
  - 复用状态：ready_for_review；类型：unknown

### training

- `TP-VWGAN/train.py`
  - 能力：training_entrypoint
  - 用途：训练主程序与训练逻辑
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态路径审查，未执行代码、未安装依赖、未运行测试。
- 未见冻结的 bundled data、checkpoint 或评估结果，无法验证端到端复现。
- 外部数据库下载脚本存在，但数据源的完整性与许可未核验。
- `.gitmodules` 存在但子模块未初始化，关联外部内容无法确认。

## 仍未知

- `TP-VWGAN/readme.md`、`0-install-requirements.sh`、`2-create-datasets.sh`、`3-train-model.sh` 仅有路径级证据，具体步骤未核验。
- `pdb-database/` 与 `pdb-dataset/` 仅见目录名，未证实包含实际数据还是占位目录。
- 未发现独立 inference / evaluation / checkpoint 资产，但不能排除未纳入路径或大文件。
- `TP-VWGAN/requirements.txt` 仅给出依赖名，传递依赖的许可证边界未知。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
