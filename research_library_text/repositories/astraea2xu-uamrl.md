# astraea2xu/uamrl

- **仓库：** [https://github.com/astraea2xu/uamrl](https://github.com/astraea2xu/uamrl)
- **固定 commit：** `4e4a6528d3965d03e7f17db7aa3b36b5885e2d8f`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 6

## 仓库摘要

冻结仓库主要包含 UAMRL 的模型定义、训练模块以及少量预处理/工具脚本；未见 bundled dataset、evaluation、inference 或 checkpoint 文件，且冻结清单中没有 LICENSE，因此复用边界目前不完整。

## 可复用模块与资源

### reusable_assets

- `code/models/UAMRL.py`
  - 能力：model_architecture
  - 用途：UAMRL 主模型定义，用于 drug-target affinity prediction 的多粒度不确定性感知多模态表示学习。
  - 复用状态：blocked；类型：code_entry
- `code/create_drug_graph.py`
  - 能力：data_preprocessing
  - 用途：按文件名可见的药物图构建辅助脚本，用于生成图输入或相关预处理结果。
  - 复用状态：blocked；类型：code_entry
- `code/create_target_distance_matrix.py`
  - 能力：data_preprocessing
  - 用途：按文件名可见的靶标距离矩阵构建辅助脚本，用于生成模型所需输入特征。
  - 复用状态：blocked；类型：code_entry
- `code/util/graphUtil.py`
  - 能力：utility
  - 用途：图相关辅助函数，支撑图数据处理与特征操作。
  - 复用状态：blocked；类型：code_entry
- `code/util/util.py`
  - 能力：utility
  - 用途：通用辅助函数，供训练与预处理流程复用。
  - 复用状态：blocked；类型：code_entry

### training

- `code/training.py`
  - 能力：training_module
  - 用途：训练流程与参数更新组织模块。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，仓库代码未执行、测试未跑、依赖未安装。
- 冻结清单未见 bundled dataset、checkpoint、evaluation 或独立 inference 脚本。
- 未发现 LICENSE，代码/数据/模型的独立复用边界都未被明确授权。
- 部分预处理用途仅可由文件名推断，具体 I/O 与外部依赖仍未知。

## 仍未知

- README 是否说明外部数据集下载位置、数据格式和预处理输入。
- code/training.py 是否内置验证/测试循环或其他评估逻辑。
- 是否存在未跟踪的大文件权重或数据缓存。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
