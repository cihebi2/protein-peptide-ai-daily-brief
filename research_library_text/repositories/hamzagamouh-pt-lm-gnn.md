# hamzagamouh/pt-lm-gnn

- **仓库：** [https://github.com/hamzagamouh/pt-lm-gnn](https://github.com/hamzagamouh/pt-lm-gnn)
- **固定 commit：** `c14565de4eb2ab5350e81af2e697e3aff4a67355`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 14

## 仓库摘要

静态清点显示该仓库围绕蛋白-配体结合残基预测，提供 BioLiP 结构下载、结构信息/embedding 生成、训练、推理和结果表汇总；未见 bundled data、checkpoint 或 LICENSE，因此只能给出受限复用边界判断。

## 可复用模块与资源

### evaluation

- `scripts/create_result_tables.py`
  - 能力：result_reporting
  - 用途：artifact_kind=code_entry；结果表生成/汇总脚本；仅能从文件名判断其与评测相关，未能静态证实其为正式 benchmark 流程。
  - 复用状态：blocked；类型：code_entry

### inference

- `scripts/inference.py`
  - 能力：inference
  - 用途：artifact_kind=code_entry；推理主脚本，执行已训练模型的结合残基预测。
  - 复用状态：blocked；类型：code_entry
- `scripts/inference.sh`
  - 能力：inference_wrapper
  - 用途：artifact_kind=code_entry；推理命令封装/批处理入口。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `scripts/download_biolip_structures.pl`
  - 能力：data_acquisition
  - 用途：artifact_kind=code_entry；下载 BioLiP 相关结构数据的获取脚本，不是内置数据集本身。
  - 复用状态：blocked；类型：unknown
- `requirements.txt`
  - 能力：dependencies
  - 用途：artifact_kind=config；Python 依赖清单，用于环境重建与依赖安装参考。
  - 复用状态：blocked；类型：unknown
- `embs_requirements.txt`
  - 能力：dependencies
  - 用途：artifact_kind=config；embedding 相关依赖清单，服务特征生成/环境复现。
  - 复用状态：blocked；类型：unknown
- `graph_attention/attention_visualization.py`
  - 能力：visualization
  - 用途：artifact_kind=code_entry；attention 可视化脚本，属于训练后解释/展示辅助。
  - 复用状态：blocked；类型：code_entry
- `graph_attention/attention_viz.ipynb`
  - 能力：visualization
  - 用途：artifact_kind=code_entry；attention 可视化 notebook，属于演示/分析辅助资产。
  - 复用状态：blocked；类型：unknown

### training

- `scripts/train_model.py`
  - 能力：training_entrypoint/model_architecture
  - 用途：artifact_kind=code_entry；训练主入口并承载模型结构定义，冻结清单同时标记为 training_entrypoint 与 model_architecture。
  - 复用状态：blocked；类型：code_entry
- `scripts/preprocessing_datasets.py`
  - 能力：data_loader
  - 用途：artifact_kind=code_entry；训练前数据预处理/装载脚本，冻结清单标记为 data_loader。
  - 复用状态：blocked；类型：code_entry
- `scripts/compute_embeddings.py`
  - 能力：feature_generation
  - 用途：artifact_kind=code_entry；生成 embeddings 的辅助脚本，服务训练特征构造。
  - 复用状态：blocked；类型：code_entry
- `scripts/create_dataset_embeddings.py`
  - 能力：feature_generation
  - 用途：artifact_kind=code_entry；批量生成数据集级 embeddings 的辅助脚本。
  - 复用状态：blocked；类型：code_entry
- `scripts/get_structural_information.py`
  - 能力：structure_feature_extraction
  - 用途：artifact_kind=code_entry；提取结构信息，供训练特征构建使用。
  - 复用状态：blocked；类型：code_entry
- `scripts/manual_corrections.py`
  - 能力：data_curation
  - 用途：artifact_kind=code_entry；手动修正/清洗辅助脚本，属于训练数据准备链路。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态分析；未安装依赖、未运行代码、未跑测试。
- tracked 文件存在不代表可复现执行或结果可重现。
- 仓库清单中未见 bundled data 与 checkpoint；`.pdb`/`.pse` 更像结构/可视化文件而非模型权重。
- 没有独立的 LICENSE 文件，代码直用边界不清。

## 仍未知

- 外部 BioLiP/结构数据的具体来源与上游许可未在仓库内确认。
- `scripts/create_result_tables.py` 是否对应正式评测流程，静态清单无法证实。
- `scripts/1a2b.pdb` 与 `graph_attention/*.pse` 的实际用途需内容级核验。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
