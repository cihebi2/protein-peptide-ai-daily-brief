# zhc-moushang/DeepTGIN

- **仓库：** [https://github.com/zhc-moushang/DeepTGIN](https://github.com/zhc-moushang/DeepTGIN)
- **固定 commit：** `88763b00d63c9a24924f036d4ec14f8052e43f85`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 7

## 仓库摘要

该仓库的冻结清单显示：有模型实现、数据加载、评估脚本和环境配置，但未发现 LICENSE、明确的训练入口、推理入口或 checkpoint。数据文件存在却仅能从路径名判断用途；在许可与内容未确认前，不应直接复用。

## 可复用模块与资源

### datasets

- `affinity_data.csv`
  - 能力：binding_affinity_dataset
  - 用途：样本/标签表；从文件名看用于亲和力预测数据。
  - 复用状态：unknown；类型：unknown
- `data/processed/data.zip`
  - 能力：processed_data_bundle
  - 用途：处理后的数据包；内部内容未展开，可能含特征或中间数据。
  - 复用状态：unknown；类型：unknown

### evaluation

- `metrics.py`
  - 能力：evaluation_metrics
  - 用途：指标计算与结果评估。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `model.py`
  - 能力：model_architecture
  - 用途：核心模型结构定义，可作为实现参考。
  - 复用状态：blocked；类型：code_entry
- `dataset.py`
  - 能力：data_loader
  - 用途：数据读取与预处理逻辑。
  - 复用状态：blocked；类型：code_entry
- `metrics.py`
  - 能力：evaluation
  - 用途：评估指标计算。
  - 复用状态：blocked；类型：code_entry
- `environment.yaml`
  - 能力：dependencies
  - 用途：环境/依赖配置，可用于构建运行环境。
  - 复用状态：blocked；类型：config

## 使用限制

- 仅做静态审查，未执行代码、未安装依赖、未运行测试。
- 冻结清单未识别训练入口、推理入口或 checkpoint。
- data/processed/data.zip 未解包，内部内容与许可未知。
- main.py 存在于 tracked_paths，但未在冻结清单中被正式分类为训练入口。

## 仍未知

- README.md 的完整使用说明未被解析，无法确认训练流程。
- environment.yaml 中第三方包的许可证未展开核验。
- affinity_data.csv 与 data/processed/data.zip 的生成来源和再分发限制未知。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
