# A4Bio/MeToken

- **仓库：** [https://github.com/A4Bio/MeToken](https://github.com/A4Bio/MeToken)
- **固定 commit：** `226c94d4e1d7b33c0ee9993b0c036a417942e1ad`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 11

## 仓库摘要

该仓库是 MeToken 的静态实现清单，覆盖 PTM 预测的模型、数据加载、特征工程、推理与示例数据；未见训练入口、正式评测脚本或检查点，复用时需补齐权重与实验流程。

## 可复用模块与资源

### datasets

- `examples/Q16613.pdb`
  - 能力：示例结构输入
  - 用途：快速演示或单结构推理输入
  - 复用状态：partial；类型：unknown

### evaluation

- `quick_test.ipynb`
  - 能力：快速自检
  - 用途：用于快速检查模型或输入输出，不是正式基准评测
  - 复用状态：partial；类型：unknown

### inference

- `inference.py`
  - 能力：推理脚本
  - 用途：从配置和输入文件执行预测
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/metoken_model.py`
  - 能力：模型架构
  - 用途：定义 MeToken 的主要网络结构与前向计算
  - 复用状态：ready_for_review；类型：code_entry
- `model_interface.py`
  - 能力：模型接口封装
  - 用途：对外暴露模型调用接口，便于训练或推理脚本接入
  - 复用状态：ready_for_review；类型：code_entry
- `src/datasets/ptm_dataset.py`
  - 能力：数据集读取
  - 用途：读取并组织 PTM 预测所需样本
  - 复用状态：ready_for_review；类型：code_entry
- `src/datasets/featurizer.py`
  - 能力：特征工程
  - 用途：把输入序列/结构转换为模型特征
  - 复用状态：ready_for_review；类型：code_entry
- `inference.py`
  - 能力：推理入口
  - 用途：执行单样本或批量预测流程
  - 复用状态：ready_for_review；类型：code_entry
- `configs/MeToken.yaml`
  - 能力：配置 recipe
  - 用途：保存模型与推理的参数配置
  - 复用状态：partial；类型：config
- `src/metoken_module.py`
  - 能力：辅助模块
  - 用途：模型内部辅助组件/模块封装
  - 复用状态：partial；类型：code_entry
- `environment.yml`
  - 能力：运行环境规范
  - 用途：定义 Conda 依赖环境
  - 复用状态：partial；类型：config

## 使用限制

- 仅做静态清单审查，未运行代码、未安装依赖、未验证输出。
- 冻结清单未见训练入口或训练模块，无法判断训练流程、数据切分和超参。
- 未见 checkpoints/权重文件，不能确认可直接推理的模型状态。
- 未见正式评测脚本或指标汇报，`quick_test.ipynb` 只能视为快速自检痕迹。
- `examples/Q16613.pdb` 的来源与许可未被独立证明。

## 仍未知

- PTM 数据集的具体来源、规模和划分方式未在冻结清单中得到确认。
- `src/metoken_module.py` 与 `src/design_utils.py` 的具体职责仅能从文件名推断，未读内容。
- 是否存在外部下载器、预处理产物或其他未跟踪的模型权重未被确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
