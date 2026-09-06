# amir-hassan25/Temporal-Hypergraph-Contrastive-Learning

- **仓库：** [https://github.com/amir-hassan25/Temporal-Hypergraph-Contrastive-Learning](https://github.com/amir-hassan25/Temporal-Hypergraph-Contrastive-Learning)
- **固定 commit：** `81a844c0a110d33defa0d44efdf31ab5b60247a6`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 10

## 仓库摘要

该仓库是论文相关的时序超图对比学习代码库，静态可见数据预处理、超图/图编码器、核心模型与评估模块；未见冻结训练入口、推理入口或检查点，且没有明确 LICENSE。

## 可复用模块与资源

### datasets

- `data.zip`
  - 能力：bundled data archive
  - 用途：静态打包数据；内容、来源与许可未展开
  - 复用状态：blocked；类型：unknown

### evaluation

- `src/utils/eval.py`
  - 能力：evaluation
  - 用途：评估与指标计算
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `src/models/model.py`
  - 能力：core model
  - 用途：核心时序超图对比学习模型定义/组合
  - 复用状态：blocked；类型：code_entry
- `src/models/model_cheshire.py`
  - 能力：model variant
  - 用途：另一个核心模型变体实现
  - 复用状态：blocked；类型：code_entry
- `src/models/graph_models/unigat.py`
  - 能力：graph encoder backbone
  - 用途：图编码器骨干；从文件名看为 GAT 风格实现
  - 复用状态：blocked；类型：code_entry
- `src/models/graph_models/unigcn.py`
  - 能力：graph encoder backbone
  - 用途：图编码器骨干；从文件名看为 GCN 风格实现
  - 复用状态：blocked；类型：code_entry
- `src/models/graph_models/unisage.py`
  - 能力：graph encoder backbone
  - 用途：图编码器骨干；从文件名看为 SAGE 风格实现
  - 复用状态：blocked；类型：code_entry
- `src/utils/hypergraph.py`
  - 能力：hypergraph utilities
  - 用途：超图结构构建与相关算子工具
  - 复用状态：blocked；类型：code_entry
- `src/utils/positional_encoding.py`
  - 能力：temporal/positional encoding
  - 用途：位置/时间编码工具
  - 复用状态：blocked；类型：code_entry
- `src/utils/data_prep.py`
  - 能力：data loader / preprocessing
  - 用途：数据读取、清洗、切分或预处理管线
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅静态审计，未安装依赖、未运行代码，不能证明可复现。
- 冻结清单中未见 training_entrypoint、inference 或 checkpoint 资产。
- `data.zip` 已追踪但未展开，无法确认内容、来源与许可。
- 仓库未提供明确 LICENSE，代码/数据/模型的复用边界受限。

## 仍未知

- `src/main.py` 虽在 tracked_paths 中，但未进入 training_entrypoint 资产清单，角色不明。
- `data.zip` 是项目自带数据、第三方打包数据还是示例数据，冻结清单无法判定。
- `requirements.txt` 仅说明依赖声明，不代表依赖已安装或代码已执行。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
