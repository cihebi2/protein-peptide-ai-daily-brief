# Cpillar/ConsAMPHemo

- **仓库：** [https://github.com/Cpillar/ConsAMPHemo](https://github.com/Cpillar/ConsAMPHemo)
- **固定 commit：** `950fb333d2126f79dda94a673e85ae1965d50d11`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 11

## 仓库摘要

仓库主要提供 `model/train.py` / `model/evaluate.py` 的训练评估流程，配套 3 组分类数据切分（S1/S2/S3）和回归数据 `Hemo_regression.csv`，并跟踪若干已序列化模型产物；未发现显式 LICENSE，因此代码、数据和模型都不能默认视为可直接复用。

## 可复用模块与资源

### checkpoints

- `Dataset/S1/model/S1.pth.pl`
  - 能力：S1 模型产物
  - 用途：位于 S1 目录下的序列化模型/检查点文件；可作为该任务的已保存模型产物候选。
  - 复用状态：blocked；类型：unknown
- `Dataset/S2/model/S2.pl`
  - 能力：S2 模型产物
  - 用途：位于 S2 目录下的序列化模型/检查点文件；可作为该任务的已保存模型产物候选。
  - 复用状态：blocked；类型：unknown
- `Dataset/S3/model/S3.pth.pl`
  - 能力：S3 模型产物
  - 用途：位于 S3 目录下的序列化模型/检查点文件；可作为该任务的已保存模型产物候选。
  - 复用状态：blocked；类型：unknown
- `Dataset/regression/model/XGB_model_Hemo.joblib`
  - 能力：回归模型产物
  - 用途：joblib 序列化的回归模型文件；可作为回归任务的已保存模型产物候选。
  - 复用状态：blocked；类型：unknown

### datasets

- `Dataset/S1/S_1.csv`
  - 能力：S1 分类数据
  - 用途：S1 分类任务的数据包；同目录可见 train/test 切分，说明该任务有独立训练与测试划分。
  - 复用状态：blocked；类型：unknown
- `Dataset/S2/S_2.csv`
  - 能力：S2 分类数据
  - 用途：S2 分类任务的数据包；同目录可见 train/test 切分。
  - 复用状态：blocked；类型：unknown
- `Dataset/S3/S_3.csv`
  - 能力：S3 分类数据
  - 用途：S3 分类任务的数据包；同目录可见 train/test 切分。
  - 复用状态：blocked；类型：unknown
- `Dataset/regression/Hemo_regression.csv`
  - 能力：回归数据
  - 用途：回归任务的数据表；仓库还跟踪 `Dataset/regression/regression.xlsx`，但其角色未明。
  - 复用状态：blocked；类型：unknown

### evaluation

- `model/evaluate.py`
  - 能力：评估入口
  - 用途：主要评估脚本；从命名看用于读取已训练模型并输出性能结果，但静态未执行，未能确认是否同时承担 inference。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `requirements.txt`
  - 能力：Python dependency specification
  - 用途：列出训练/评估所需依赖，便于重建环境；静态未安装验证。
  - 复用状态：blocked；类型：unknown

### training

- `model/train.py`
  - 能力：训练入口
  - 用途：主要训练脚本；从仓库结构看，配合 S1/S2/S3 与 regression 数据生成模型产物，但静态盘点未执行，具体算法、超参和输出流程未证实。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态盘点，未执行代码、未安装依赖、未运行测试。
- 路径存在不等于可复现；训练产物和数据切分无法仅凭静态清单证明生成过程。
- 仓库未见显式 LICENSE，直接复用需要单独做许可/权利确认。

## 仍未知

- `Dataset/regression/regression.xlsx` 的角色不明，可能是源表或派生表。
- `Dataset/*/model/*` 的 `.pth.pl` / `.pl` / `.joblib` 文件是否为最终 checkpoint、外部导入模型或中间产物，静态上无法确认。
- 未发现独立 `inference` 脚本；推理是否被 `model/evaluate.py` 间接承载不明。
- 各 CSV 的上游来源、清洗规则和是否来自外部公开数据集都不明。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
