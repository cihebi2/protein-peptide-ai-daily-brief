# ajy112/EMPP

- **仓库：** [https://github.com/ajy112/EMPP](https://github.com/ajy112/EMPP)
- **固定 commit：** `a33f8538c0010631895a68a09fb0d5dea0a834ca`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 14

## 仓库摘要

冻结清单显示该仓库主要由 `nets/` 中的模型定义、`datasets/` 中的 QM9/GEOM 加载器和 `scripts/train/qm9/equiformer/` 的训练脚本构成；未见独立 inference/eval/checkpoint 资产，且未发现 LICENSE。

## 可复用模块与资源

### datasets

- `datasets/qm9.py`
  - 能力：qm9_loader
  - 用途：QM9 数据读取/预处理加载器
  - 复用状态：blocked；类型：code_entry
- `datasets/GEOM.py`
  - 能力：geom_loader
  - 用途：GEOM 数据读取/预处理加载器
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `nets/graph_attention_transformer.py`
  - 能力：core_model_block
  - 用途：图注意力/等变表示学习模型模块之一
  - 复用状态：blocked；类型：code_entry
- `nets/dp_attention_transformer.py`
  - 能力：core_model_block
  - 用途：注意力式模型模块之一
  - 复用状态：blocked；类型：code_entry
- `nets/global_reverse_model.py`
  - 能力：core_model_block
  - 用途：全局反向建模模块
  - 复用状态：blocked；类型：code_entry
- `nets/testmodel.py`
  - 能力：core_model_block
  - 用途：测试/对照模型定义
  - 复用状态：blocked；类型：code_entry
- `optim_factory.py`
  - 能力：shared_training_support
  - 用途：优化器/训练配置工厂
  - 复用状态：blocked；类型：code_entry
- `utils.py`
  - 能力：shared_training_support
  - 用途：通用工具函数
  - 复用状态：blocked；类型：code_entry
- `logger.py`
  - 能力：shared_training_support
  - 用途：日志记录工具
  - 复用状态：blocked；类型：code_entry

### training

- `main_qm9.py`
  - 能力：training_entrypoint_candidate
  - 用途：QM9 主实验/训练入口候选
  - 复用状态：blocked；类型：code_entry
- `main_geom.py`
  - 能力：training_entrypoint_candidate
  - 用途：GEOM 主实验/训练入口候选
  - 复用状态：blocked；类型：code_entry
- `engine.py`
  - 能力：training_loop_support
  - 用途：通用训练/验证循环支撑模块
  - 复用状态：blocked；类型：code_entry
- `engine_geom.py`
  - 能力：training_loop_support
  - 用途：GEOM 任务相关训练循环支撑模块
  - 复用状态：blocked；类型：code_entry
- `scripts/train/qm9/equiformer/target@0.sh`
  - 能力：training_script_family
  - 用途：QM9 上 Equiformer 训练启动脚本家族（target@0..11，含 dist 版本）
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未运行代码、脚本或测试。
- 冻结清单未发现 LICENSE，直接复用边界不明确。
- 未安装依赖，无法验证训练/加载/导入是否可执行。
- 未发现 tracked 的模型权重或 checkpoint 文件，无法确认可复现实验产物。

## 仍未知

- `main_qm9.py`、`main_geom.py` 与 `engine.py`、`engine_geom.py` 是否构成正式入口仍需读源码或运行确认。
- `datasets/qm9.py`、`datasets/GEOM.py` 是否包含下载逻辑或仅为纯 loader，静态清单无法确认。
- `.ipynb_checkpoints/` 和 `__pycache__/` 中是否存在额外可用内容不确定，当前不按可复用资产处理。
- 是否存在未跟踪的大文件权重、外部下载依赖或第三方 vendored 代码，当前冻结清单无法证明。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
