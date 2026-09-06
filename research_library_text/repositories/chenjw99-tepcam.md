# Chenjw99/TEPCAM

- **仓库：** [https://github.com/Chenjw99/TEPCAM](https://github.com/Chenjw99/TEPCAM)
- **固定 commit：** `a9d8426c0f38d09a33a09e190c0cad1e19d532da`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 11

## 仓库摘要

冻结快照显示该仓库包含TEPCAM模型代码、训练入口、三份CSV数据和一个测试checkpoint；但未发现LICENSE，且仅做静态审查，无法验证可复现性或实际运行效果。

## 可复用模块与资源

### checkpoints

- `ckpts/tepcam_test.pt`
  - 能力：model_checkpoint
  - 用途：测试时加载的权重文件/检查点
  - 复用状态：blocked；类型：model_weight

### datasets

- `Data/ImmuneCODE.csv`
  - 能力：bundled_csv_dataset
  - 用途：随仓库打包的数据资源，供模型训练或测试流水线读取
  - 复用状态：blocked；类型：unknown
- `Data/STCRdab_meta.csv`
  - 能力：bundled_csv_dataset
  - 用途：随仓库打包的数据资源，供模型训练或测试流水线读取
  - 复用状态：blocked；类型：unknown
- `Data/TEP-merge.csv`
  - 能力：bundled_csv_dataset
  - 用途：随仓库打包的数据资源，供模型训练或测试流水线读取
  - 复用状态：blocked；类型：unknown

### evaluation

- `scripts/test.py`
  - 能力：test_or_evaluation_harness
  - 用途：测试/评估脚本候选；冻结库存未单列evaluation能力，仅能从文件名判断
  - 复用状态：unknown；类型：code_entry

### inference

- `scripts/model/TEPCAM.py`
  - 能力：model_forward_pass
  - 用途：可支撑推理阶段的前向计算，但未发现独立推理入口
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `scripts/model/TEPCAM.py`
  - 能力：model_architecture
  - 用途：TEPCAM核心模型定义，可作为架构参考或代码复用起点
  - 复用状态：blocked；类型：code_entry
- `scripts/data/process.py`
  - 能力：data_loader
  - 用途：CSV数据预处理与加载逻辑，可作为数据管线参考
  - 复用状态：blocked；类型：code_entry
- `scripts/utils/funcs.py`
  - 能力：utility_functions
  - 用途：辅助函数集合，可能支撑训练/评估流程
  - 复用状态：unknown；类型：code_entry

### training

- `scripts/train.py`
  - 能力：training_entrypoint
  - 用途：模型训练主入口，按文件名和冻结库存标记执行训练流程
  - 复用状态：blocked；类型：code_entry
- `scripts/data/process.py`
  - 能力：training_preprocessing
  - 用途：训练前数据处理/编码/划分支持
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码、未安装依赖、未运行测试
- 未验证scripts/test.py究竟是评估、推理还是其他测试脚本
- checkpoint仅凭路径存在，未验证其来源、训练配置与对应指标
- CSV内容与许可条款未展开核验
- 仓库未提供明确LICENSE，直接复用边界不清楚

## 仍未知

- scripts/test.py是否实际承担evaluation或inference职责
- Data/*.csv是否为原始数据、清洗后数据还是合并中间产物
- ckpts/tepcam_test.pt是否与论文最终结果一致
- requirements.txt与env.yaml中的第三方依赖是否包含额外许可约束

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
