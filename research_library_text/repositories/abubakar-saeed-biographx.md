# Abubakar-Saeed/BioGraphX

- **仓库：** [https://github.com/Abubakar-Saeed/BioGraphX](https://github.com/Abubakar-Saeed/BioGraphX)
- **固定 commit：** `f8a6c32bd4e74ad275e56553c870ca841c34951a`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 10

## 仓库摘要

仓库包含 BioGraphX 的核心物理化学图编码代码、ESM embeddings 辅助脚本、独立训练/推理/验证入口，以及 5 个 fold 的模型权重；未见 bundled dataset。代码许可证为 MIT，但权重与任何外部数据未见单独许可证边界，因此整体只能做静态可复用性判断。

## 可复用模块与资源

### checkpoints

- `model-weights/model_fold_0.pth`
  - 能力：fold 0 model weights
  - 用途：保存的训练参数，可能用于单折推理或集成
  - 复用状态：partial；类型：model_weight
- `model-weights/model_fold_1.pth`
  - 能力：fold 1 model weights
  - 用途：保存的训练参数，可能用于单折推理或集成
  - 复用状态：partial；类型：model_weight
- `model-weights/model_fold_2.pth`
  - 能力：fold 2 model weights
  - 用途：保存的训练参数，可能用于单折推理或集成
  - 复用状态：partial；类型：model_weight
- `model-weights/model_fold_3.pth`
  - 能力：fold 3 model weights
  - 用途：保存的训练参数，可能用于单折推理或集成
  - 复用状态：partial；类型：model_weight
- `model-weights/model_fold_4.pth`
  - 能力：fold 4 model weights
  - 用途：保存的训练参数，可能用于单折推理或集成
  - 复用状态：partial；类型：model_weight

### evaluation

- `BioGraphX-Encoding/Structure Validation/validate.py`
  - 能力：验证/评估脚本
  - 用途：执行结构验证或结果检查的静态评估入口
  - 复用状态：partial；类型：code_entry

### inference

- `inference.py`
  - 能力：预测推理入口
  - 用途：基于已保存权重执行预测/打分的脚本入口
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `BioGraphX-Encoding/src/biographx/pipeline.py`
  - 能力：核心物理化学图编码管线
  - 用途：组织图构建、预处理、物化属性与特征映射，构成核心编码链路
  - 复用状态：ready_for_review；类型：code_entry
- `esm_embeddings.py`
  - 能力：ESM 序列表示辅助脚本
  - 用途：生成或封装 sequence embeddings，作为训练/推理输入
  - 复用状态：ready_for_review；类型：code_entry

### training

- `BioGraphX_Training_Code.py`
  - 能力：训练/五折实验入口
  - 用途：训练主脚本（按文件名判断），可用于复现实验或再训练
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态审查，未执行仓库代码。
- 依赖未安装，运行环境兼容性未验证。
- tests 未运行，指标与结果未复现。
- submodules 未初始化，外部资源可能缺失。
- 路径存在不等于可复现，权重与数据可用性仍待确认。

## 仍未知

- 未发现 bundled dataset；训练/验证数据来源不明。
- `BioGraphX_Training_Code.py`、`inference.py`、`validate.py` 的真实参数与调用约定未从文件内容确认。
- 5 个 checkpoint 的训练数据、基座模型与再分发边界未见独立说明。
- `run.py` 与 `targeting_rules.py` 的精确职责只能从文件名推断。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
