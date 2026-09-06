# yongchand/reliable-ba

- **仓库：** [https://github.com/yongchand/reliable-ba](https://github.com/yongchand/reliable-ba)
- **固定 commit：** `fec924ff7c9fd439415ff0c8baa8a3bda34d240b`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 14

## 仓库摘要

仓库主要提供 protein-ligand binding affinity prediction 的训练/推理实现、示例脚本和数据分割清单；已见 MIT 代码许可，但未见 checkpoint 或独立数据许可，复现仅能做静态判断。

## 可复用模块与资源

### datasets

- `data/train_pdbs.csv`
  - 能力：training_split_manifest
  - 用途：训练集 PDB ID / 样本索引清单，不是 checkpoint。artifact_kind: unknown
  - 复用状态：partial；类型：unknown
- `data/validation_pdbs.csv`
  - 能力：validation_split_manifest
  - 用途：验证集 PDB ID / 样本索引清单。artifact_kind: unknown
  - 复用状态：partial；类型：unknown
- `data/test_pdbs.csv`
  - 能力：test_split_manifest
  - 用途：测试集 PDB ID / 样本索引清单。artifact_kind: unknown
  - 复用状态：partial；类型：unknown
- `examples/sample_data.csv`
  - 能力：example_input_data
  - 用途：示例输入样例，供 examples 脚本演示。artifact_kind: unknown
  - 复用状态：partial；类型：unknown

### evaluation

- `src/analyze_uncertainty.py`
  - 能力：uncertainty_analysis
  - 用途：不确定性/可靠性分析模块，可作为评估辅助，但未见独立 benchmark 入口。artifact_kind: code_entry
  - 复用状态：partial；类型：code_entry

### inference

- `src/inference_drug_discovery.py`
  - 能力：inference_pipeline
  - 用途：推理与打分流程主模块。artifact_kind: code_entry
  - 复用状态：ready_for_review；类型：code_entry
- `examples/generate_embeddings.py`
  - 能力：embedding_generation
  - 用途：生成 embedding 的示例推理脚本。artifact_kind: code_entry
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/drug_models_emb.py`
  - 能力：model_architecture
  - 用途：核心模型结构与融合逻辑实现；按文件名与仓库上下文看，应为亲和力预测主模型代码。artifact_kind: code_entry
  - 复用状态：ready_for_review；类型：code_entry
- `src/drug_dataset_emb.py`
  - 能力：dataset_helpers
  - 用途：训练/推理的数据集封装、样本组织与读取辅助代码。artifact_kind: code_entry
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils.py`
  - 能力：shared_utilities
  - 用途：通用辅助函数，可能被训练和推理流程复用。artifact_kind: code_entry
  - 复用状态：ready_for_review；类型：code_entry
- `requirements.txt`
  - 能力：environment_recipe
  - 用途：Python 依赖声明，用于重建运行环境边界。artifact_kind: config
  - 复用状态：ready_for_review；类型：unknown
- `examples/generate_sample_data.py`
  - 能力：example_data_generation
  - 用途：示例数据生成脚本，适合作为文档化演示资产。artifact_kind: code_entry
  - 复用状态：ready_for_review；类型：code_entry
- `examples/run_example.sh`
  - 能力：example_runner
  - 用途：示例执行封装脚本，便于复现仓库演示流程。artifact_kind: code_entry
  - 复用状态：ready_for_review；类型：code_entry

### training

- `src/train_drug_discovery_emb.py`
  - 能力：model_training
  - 用途：训练亲和力/可靠性相关模型的静态训练模块。artifact_kind: code_entry
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码、未安装依赖、未跑测试。
- 冻结清单中未见 checkpoint 或模型权重文件，无法证明可直接推理复现。
- 数据 CSV 的来源、构造过程与独立许可未建立。
- 未见独立 evaluation/benchmark 入口；`src/analyze_uncertainty.py` 只能算评估相关线索。

## 仍未知

- `data/train_pdbs.csv` 等是否仅为 PDB ID 列表，还是还包含额外特征列。
- `main.py` 与 `examples/run_example.sh` 的实际调用链未在静态证据中确认。
- `requirements.txt` 是否完整覆盖运行时依赖与版本约束。
- 是否存在未跟踪的外部发布 checkpoint 或数据副本，冻结清单无法确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
