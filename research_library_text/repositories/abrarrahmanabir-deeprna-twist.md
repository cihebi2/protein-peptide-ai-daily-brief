# abrarrahmanabir/DeepRNA-Twist

- **仓库：** [https://github.com/abrarrahmanabir/DeepRNA-Twist](https://github.com/abrarrahmanabir/DeepRNA-Twist)
- **固定 commit：** `fe9df4a058cdf5c3569275a99cddf0d3d21c9308`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 6

## 仓库摘要

冻结清单显示该仓库包含模型结构、训练与推理模块、数据预处理脚本以及两份内置CSV数据，但没有看到评估脚本、checkpoint或LICENSE文件；因此只能做静态复核，直接复用代码/数据/模型都受许可证缺失限制。

## 可复用模块与资源

### datasets

- `Data/combined_full.csv`
  - 能力：内置CSV数据表
  - 用途：仓库内置数据表
  - 复用状态：blocked；类型：unknown
- `Data/combined_maintorsion.csv`
  - 能力：内置CSV数据表
  - 用途：仓库内置数据表
  - 复用状态：blocked；类型：unknown

### inference

- `inference.py`
  - 能力：推理模块
  - 用途：模型预测/推断流程
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `model.py`
  - 能力：模型结构
  - 用途：定义RNA torsion angle 预测网络结构
  - 复用状态：blocked；类型：code_entry
- `data_preprocessing.py`
  - 能力：数据加载/预处理
  - 用途：读取并整理训练数据
  - 复用状态：blocked；类型：code_entry

### training

- `training.py`
  - 能力：训练模块
  - 用途：模型训练流程
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审计，未读取源码内容或运行任何代码
- 依赖未安装，无法验证训练/推理入口
- 未见tests/CI，无法验证行为或数值结果
- 未见checkpoint，推理是否依赖外部权重未知
- 缺少LICENSE，代码/数据/模型直接复用受限

## 仍未知

- Data/combined_full.csv 与 Data/combined_maintorsion.csv 的字段、来源和授权未知
- training.py 的超参数、损失函数与是否为实际训练入口未知
- inference.py 是否加载外部checkpoint/预训练权重未知
- model.py 的具体网络结构细节未知
- main.py、loss_functions.py、torsioncode.py、utils.py 在冻结清单中存在，但未被单独归类，具体职责未知

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
