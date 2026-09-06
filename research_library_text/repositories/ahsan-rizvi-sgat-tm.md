# ahsan-rizvi/SGAT-TM

- **仓库：** [https://github.com/ahsan-rizvi/SGAT-TM](https://github.com/ahsan-rizvi/SGAT-TM)
- **固定 commit：** `39594b33ef4c7a6da93828d3177ef69b2607ae16`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 10

## 仓库摘要

该冻结仓库主要暴露出 SGAT-TM 的模型实现与数据读取骨架，包含少量静态数据工件；未发现许可证、checkpoint、显式训练/评估/推理清单，整体仅能做静态复用审计。

## 可复用模块与资源

### datasets

- `data/lncRNA_idx.csv`
  - 能力：identifier_index
  - 用途：lncRNA 索引表
  - 复用状态：blocked；类型：unknown
- `data/miRNA_idx.csv`
  - 能力：identifier_index
  - 用途：miRNA 索引表
  - 复用状态：blocked；类型：unknown
- `data/lncRNA_feature.pkl`
  - 能力：feature_cache
  - 用途：lncRNA 特征缓存/静态工件
  - 复用状态：blocked；类型：unknown
- `data/miRNA_feature.pkl`
  - 能力：feature_cache
  - 用途：miRNA 特征缓存/静态工件
  - 复用状态：blocked；类型：unknown
- `data/splits.pkl`
  - 能力：data_split
  - 用途：数据划分工件
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `code/model.py`
  - 能力：model_architecture
  - 用途：SGAT-TM 核心网络定义
  - 复用状态：blocked；类型：code_entry
- `code/dataset.py`
  - 能力：data_loader
  - 用途：数据读取/样本构造逻辑
  - 复用状态：blocked；类型：code_entry
- `code/layer.py`
  - 能力：support_module
  - 用途：辅助层实现（仅静态路径可见，内容未展开）
  - 复用状态：blocked；类型：code_entry
- `code/funcs.py`
  - 能力：support_module
  - 用途：辅助函数/工具逻辑（仅静态路径可见，内容未展开）
  - 复用状态：blocked；类型：code_entry

### training

- `code/main.py`
  - 能力：training_orchestration
  - 用途：顶层实验/训练流程入口候选；仅凭文件名与路径判断，未展开代码确认
  - 复用状态：unknown；类型：code_entry

## 使用限制

- 仅做静态清单审计，未运行代码、未安装依赖、未执行测试。
- code/main.py、code/funcs.py、code/layer.py 的具体职责未展开。
- data/*.pkl 的具体内容未验证，未将其当作 checkpoint。

## 仍未知

- code/main.py 是否为训练入口或其他顶层流程未确认。
- data/lncRNA_feature.pkl、data/miRNA_feature.pkl、data/splits.pkl 的格式与来源未确认。
- requirements.txt 所列依赖是否可安装、是否与当前环境兼容未验证。
- README.md 内容未逐项核对。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
