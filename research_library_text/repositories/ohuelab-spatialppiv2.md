# ohuelab/spatialppiv2

- **仓库：** [https://github.com/ohuelab/spatialppiv2](https://github.com/ohuelab/spatialppiv2)
- **固定 commit：** `67c60793f89036241de0d9dd9fc83535de6d1b9f`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 13

## 仓库摘要

仓库静态清单显示：SpatialPPIv2 主要提供图神经网络 PPI 预测实现、数据构造脚本、推理入口、默认配置和三个 checkpoint；未见独立训练/评估入口，只有 demo FASTA/PDB 与 notebook 示例。代码许可证为 Apache-2.0，但权重与示例数据的再分发边界未单独声明。

## 可复用模块与资源

### checkpoints

- `checkpoint/ProtT5.ckpt`
  - 能力：模型权重（model_weight）
  - 用途：ProtT5 路线的预训练/已训练权重文件
  - 复用状态：partial；类型：model_weight
- `checkpoint/SpatialPPIv2_ESM.ckpt`
  - 能力：模型权重（model_weight）
  - 用途：ESM 路线的 SpatialPPIv2 权重文件
  - 复用状态：partial；类型：model_weight
- `checkpoint/SpatialPPIv2_ProtT5.ckpt`
  - 能力：模型权重（model_weight）
  - 用途：ProtT5 路线的 SpatialPPIv2 权重文件
  - 复用状态：partial；类型：model_weight

### datasets

- `demo/D3INY1.fasta`
  - 能力：示例序列输入
  - 用途：Notebook/演示流程中的蛋白序列示例，不是可验证的正式训练集
  - 复用状态：partial；类型：unknown
- `demo/P33895-P40460-gt.pdb`
  - 能力：示例结构与复合物对照
  - 用途：示例复合物、单体结构与 ground-truth 对照，不是可验证的正式评测集
  - 复用状态：partial；类型：unknown

### inference

- `inference.py`
  - 能力：推理入口（code_entry）
  - 用途：加载配置与 checkpoint 执行 PPI 预测推理
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `main.py`
  - 能力：主入口脚本（code_entry）
  - 用途：仓库主入口；静态清单未确认其是训练、推理还是示例调度
  - 复用状态：unknown；类型：code_entry
- `utils/model.py`
  - 能力：模型主体实现（code_entry）
  - 用途：定义 SpatialPPIv2 的核心图神经网络结构
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/dataset_generator.py`
  - 能力：数据构造与读取（code_entry）
  - 用途：从外部序列/结构数据构建样本并提供数据读取逻辑
  - 复用状态：partial；类型：code_entry
- `scripts/calculate_embedding.py`
  - 能力：嵌入计算辅助脚本（code_entry）
  - 用途：生成蛋白语言模型 embedding 供后续预测流程使用
  - 复用状态：partial；类型：code_entry
- `config/default.yaml`
  - 能力：配置（config）
  - 用途：默认运行参数与模型/数据配置
  - 复用状态：ready_for_review；类型：config
- `env/Dockerfile`
  - 能力：环境容器定义（config）
  - 用途：复现运行环境的容器化 recipe
  - 复用状态：partial；类型：unknown
- `demo/SpatialPPIv2_Colab_Example.ipynb`
  - 能力：示例 notebook（code_entry）
  - 用途：演示推理与结果可视化流程
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态清单审阅，未执行代码、未安装依赖、未运行测试。
- 未发现明确的 training_entrypoint 或 evaluation harness，训练与评测闭环无法确认。
- checkpoint 和 demo 数据的独立许可/再分发边界未在静态元数据中单独标注。
- `main.py`、notebook 与辅助脚本的具体职责仅能从文件名/路径推断，不能当作执行证据。

## 仍未知

- `main.py` 的真实职责（训练、推理或示例调度）未从冻结证据中确认。
- `checkpoint/ProtT5.ckpt` 的来源与许可证边界不明，可能需要单独核对。
- demo FASTA/PDB 只是示例输入/对照，是否对应论文正式数据集无法从清单确认。
- 仓库是否能在当前环境稳定复现论文结果，静态审阅无法证明。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
