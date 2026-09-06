# dchen0212/trimole_hybrid

- **仓库：** [https://github.com/dchen0212/trimole_hybrid](https://github.com/dchen0212/trimole_hybrid)
- **固定 commit：** `6ee1fb3d1272d50e850098725628c873ed63fe71`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 20

## 仓库摘要

仓库以多模态 ADMET 预测与基准复现为主，覆盖配置、训练、推理、评测和审计表；未见统一许可证、模型权重或可验证的运行复现。

## 可复用模块与资源

### datasets

- `supplementary_tables/Table_S1_TDC_ADMET22_benchmark.csv`
  - 能力：benchmark_manifest
  - 用途：22-task benchmark 清单与划分元数据。
  - 复用状态：blocked；类型：unknown
- `supplementary_tables/Table_S3_frozen_reference_snapshot.csv`
  - 能力：frozen_reference_snapshot
  - 用途：冻结参考快照，支持复现审计。
  - 复用状态：blocked；类型：unknown
- `supplementary_tables/Table_S11_split_and_source_provenance_audit.csv`
  - 能力：provenance_audit
  - 用途：记录 split 与来源 provenance 审计信息。
  - 复用状态：blocked；类型：unknown
- `supplementary_tables/Table_S13_reproducibility_manifest.csv`
  - 能力：reproducibility_manifest
  - 用途：整理复现所需的环境与流程清单。
  - 复用状态：blocked；类型：unknown

### evaluation

- `code/KPGT/scripts/evaluation.py`
  - 能力：metric_evaluation
  - 用途：指标计算与评估。
  - 复用状态：blocked；类型：code_entry
- `code/trimole_hybrid/scripts/compare_to_baselines.py`
  - 能力：baseline_comparison
  - 用途：与基线方法做结果对比。
  - 复用状态：blocked；类型：code_entry
- `code/trimole_hybrid/scripts/strict/update_scoreboard_22.py`
  - 能力：scoreboard_update
  - 用途：更新 22 任务得分板与汇总表。
  - 复用状态：blocked；类型：code_entry

### inference

- `code/trimole_ept_swap_v1/prediction_zoo_ensemble_v2.py`
  - 能力：ensemble_inference
  - 用途：推理集成与预测汇总。
  - 复用状态：blocked；类型：code_entry
- `code/trimole_hybrid/trimole_inference_ablation_all22_v1.py`
  - 能力：ablation_inference
  - 用途：22 任务消融推理与结果导出。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `code/trimole_hybrid/trimole/configs/task_configs.py`
  - 能力：config_recipe
  - 用途：定义 22 个任务及其训练/评测配置开关。
  - 复用状态：blocked；类型：config
- `code/trimole_hybrid/trimole/configs/adaptive_config.py`
  - 能力：config_recipe
  - 用途：提供自适应训练与任务切换的配置逻辑。
  - 复用状态：blocked；类型：config
- `code/trimole_hybrid/trimole/models/model.py`
  - 能力：model_architecture
  - 用途：定义多模态融合主模型。
  - 复用状态：blocked；类型：code_entry
- `code/trimole_hybrid/trimole/models/fusion_blocks.py`
  - 能力：model_architecture
  - 用途：实现融合模块与门控/拼接式特征组合。
  - 复用状态：blocked；类型：code_entry
- `code/KPGT/scripts/preprocess_pretrain_dataset.py`
  - 能力：data_loader
  - 用途：预处理预训练数据。
  - 复用状态：blocked；类型：code_entry
- `code/KPGT/scripts/preprocess_downstream_dataset.py`
  - 能力：data_loader
  - 用途：预处理下游任务数据。
  - 复用状态：blocked；类型：code_entry
- `code/trimole_hybrid/scripts/benchmark_opt/prepare_bimodal_ablation_data.py`
  - 能力：data_loader
  - 用途：准备双模态消融实验数据。
  - 复用状态：blocked；类型：code_entry

### training

- `code/KPGT/scripts/train_kpgt.py`
  - 能力：pretraining_entrypoint
  - 用途：KPGT 预训练入口。
  - 复用状态：blocked；类型：code_entry
- `code/KPGT/scripts/finetune.py`
  - 能力：finetuning_entrypoint
  - 用途：下游微调入口。
  - 复用状态：blocked；类型：code_entry
- `code/trimole_hybrid/trimole/training/trainer.py`
  - 能力：hybrid_training_loop
  - 用途：主训练循环与优化流程。
  - 复用状态：blocked；类型：code_entry
- `code/trimole_hybrid/trimole/training/trainer_transfer.py`
  - 能力：transfer_training
  - 用途：迁移学习/下游训练变体。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审计，未执行任何脚本、训练或测试。
- 未发现 tracked 的 model weights / checkpoints。
- 根目录未见统一 LICENSE，直接复用代码受限。
- `supplementary_tables` 更像分析/审计产物，不等于原始数据释放。
- KPGT 子树的上游来源与许可边界仍需单独核验。

## 仍未知

- `supplementary_tables` 中 CSV/XLSX 是原始数据、派生结果还是最终论文表格，静态清单无法完全区分。
- `code/KPGT` 是否为完整 vendored 快照、还是经过本仓库改写的 fork，未能仅凭清单确认。
- `release_artifacts` 目录是否对应未跟踪的模型文件或仅为说明文档，未验证。
- 当前冻结 commit 与论文最终提交版本是否完全一致，未运行复现无法确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
