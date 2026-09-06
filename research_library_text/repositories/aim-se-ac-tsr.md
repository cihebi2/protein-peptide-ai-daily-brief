# AIM-SE/AC-TSR

- **仓库：** [https://github.com/AIM-SE/AC-TSR](https://github.com/AIM-SE/AC-TSR)
- **固定 commit：** `ced695e5de5eec177691ba79da80aa56dd297328`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 14

## 仓库摘要

该仓库是 AC-TSR 论文对应的代码仓库，主体为 RecBole 及其多种 sequential recommender / attention calibration 变体、训练配置和评估工具；冻结清单未发现 LICENSE、checkpoint 或可验证的运行/复现实证。

## 可复用模块与资源

### datasets

- `recbole/dataset_example/ml-100k/ml-100k.inter`
  - 能力：example_benchmark_data
  - 用途：示例/烟雾测试数据集目录，包含 MovieLens 100K 的 .inter/.item/.kg/.link/.user 文件。
  - 复用状态：blocked；类型：unknown

### evaluation

- `recbole/evaluator/metrics.py`
  - 能力：ranking_metrics
  - 用途：排序指标实现。
  - 复用状态：blocked；类型：code_entry
- `recbole/evaluator/evaluator.py`
  - 能力：evaluation_driver
  - 用途：评估流程调度。
  - 复用状态：blocked；类型：code_entry
- `recbole/evaluator/collector.py`
  - 能力：result_collection
  - 用途：评估结果收集与聚合。
  - 复用状态：blocked；类型：code_entry

### inference

- `recbole/quick_start/quick_start.py`
  - 能力：quick_start_inference_helper
  - 用途：通用快速启动封装，可用于离线加载与推理式实验流程；冻结清单未见独立服务化推理入口。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `recbole/model/sequential_recommender/acsasrec.py`
  - 能力：attention_calibrated_sequential_recommendation
  - 用途：AC-SASRec 变体实现，属于论文主线方法候选。
  - 复用状态：blocked；类型：code_entry
- `recbole/model/sequential_recommender/acbert4rec.py`
  - 能力：attention_calibrated_sequential_recommendation
  - 用途：AC-BERT4Rec 变体实现，用于 transformer-based sequential recommendation 的校准实验。
  - 复用状态：blocked；类型：code_entry
- `recbole/model/sequential_recommender/acssept.py`
  - 能力：attention_calibrated_sequential_recommendation
  - 用途：AC-SSEPT 变体实现，用于序列推荐模型改造。
  - 复用状态：blocked；类型：code_entry
- `recbole/model/sequential_recommender/actisasrec.py`
  - 能力：attention_calibrated_sequential_recommendation
  - 用途：AC-TiSASRec 变体实现，用于时间感知序列推荐校准。
  - 复用状态：blocked；类型：code_entry

### training

- `run_recbole.py`
  - 能力：training_entrypoint
  - 用途：主运行脚本，连接配置、数据、模型与 Trainer。
  - 复用状态：blocked；类型：code_entry
- `recbole/trainer/trainer.py`
  - 能力：training_orchestration
  - 用途：通用训练循环、优化与实验控制。
  - 复用状态：blocked；类型：code_entry
- `recbole/trainer/hyper_tuning.py`
  - 能力：hyperparameter_tuning
  - 用途：超参数搜索/调参流程。
  - 复用状态：blocked；类型：code_entry
- `scripts/run_AC-SAS.sh`
  - 能力：launcher_script
  - 用途：AC-SAS 相关实验启动脚本。
  - 复用状态：blocked；类型：code_entry
- `config/amazon-beauty.yaml`
  - 能力：experiment_config_recipes
  - 用途：训练配置集，覆盖 amazon-beauty / amazon-sports-outdoors / amazon-toys-games / yelp / config_t 等 YAML 配方。
  - 复用状态：blocked；类型：config

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- 冻结清单未包含任何 checkpoint，因此无法验证已训练权重或推理产物。
- 路径存在不等于可复现；仅凭静态文件无法证明训练/评估已成功执行。
- 仓库中大量 recbole/ 目录更像框架代码，是否为上游 vendored 版本及其许可证未被核验。

## 仍未知

- AC-* 变体与上游 RecBole 的具体差异未从静态清单中核实。
- ml-100k 示例数据的来源、分发许可与是否为最终实验数据未核实。
- 未找到独立推理/部署入口；quick_start 仅能视为共享辅助入口。
- README 未提供可替代 LICENSE 的明确授权边界。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
