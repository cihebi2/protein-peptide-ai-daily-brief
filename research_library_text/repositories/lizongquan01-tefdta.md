# lizongquan01/TEFDTA

- **仓库：** [https://github.com/lizongquan01/TEFDTA](https://github.com/lizongquan01/TEFDTA)
- **固定 commit：** `d0b38f68e847e8f95942de83cd32026e775a99bb`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 18

## 仓库摘要

仓库看起来是 TEFDTA 的静态实现与数据包，包含模型、预处理、训练/测试和指标脚本，以及 Davis/KIBA 和共价数据 CSV；未发现 LICENSE、checkpoint 或独立推理入口，仅完成静态清点，未验证可运行性。

## 可复用模块与资源

### datasets

- `data/Davis/Davis_train.csv`
  - 能力：Davis train split
  - 用途：Davis 基准训练划分
  - 复用状态：unknown；类型：unknown
- `data/Davis/Davis_test.csv`
  - 能力：Davis test split
  - 用途：Davis 基准测试划分
  - 复用状态：unknown；类型：unknown
- `data/Davis/Davis_cold.csv`
  - 能力：Davis cold split
  - 用途：Davis 冷启动/冷划分评测数据
  - 复用状态：unknown；类型：unknown
- `data/KIBA/KIBA_train.csv`
  - 能力：KIBA train split
  - 用途：KIBA 基准训练划分
  - 复用状态：unknown；类型：unknown
- `data/KIBA/KIBA_test.csv`
  - 能力：KIBA test split
  - 用途：KIBA 基准测试划分
  - 复用状态：unknown；类型：unknown
- `data/KIBA/KIBA_cold.csv`
  - 能力：KIBA cold split
  - 用途：KIBA 冷启动/冷划分评测数据
  - 复用状态：unknown；类型：unknown
- `data/CovalentData/Carbonyl/Carbonyl_1.csv`
  - 能力：Covalent carbonyl subset
  - 用途：共价结合场景的子集数据
  - 复用状态：unknown；类型：unknown
- `data/CovalentData/Halohydrocarbon/Halohydrocarbon_1.csv`
  - 能力：Covalent halohydrocarbon subset
  - 用途：共价结合场景的子集数据
  - 复用状态：unknown；类型：unknown
- `data/CovalentData/Michael_Acceptor/Michael_Acceptor_1.csv`
  - 能力：Covalent Michael acceptor subset
  - 用途：共价结合场景的子集数据
  - 复用状态：unknown；类型：unknown
- `data/CovalentData/Nitrile/Nitrile_1.csv`
  - 能力：Covalent nitrile subset
  - 用途：共价结合场景的子集数据
  - 复用状态：unknown；类型：unknown
- `data/CovalentData/Phosphonate/Phosphonate_1.csv`
  - 能力：Covalent phosphonate subset
  - 用途：共价结合场景的子集数据
  - 复用状态：unknown；类型：unknown
- `data/CovalentData/Urea-carbonyl/Urea_carbonyl_1.csv`
  - 能力：Covalent urea-carbonyl subset
  - 用途：共价结合场景的子集数据
  - 复用状态：unknown；类型：unknown

### evaluation

- `metrics.py`
  - 能力：metrics_implementation
  - 用途：评估指标实现
  - 复用状态：blocked；类型：code_entry

### inference

- `model.py`
  - 能力：prediction_core
  - 用途：模型前向推理核心；未见独立 inference 脚本
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `main.py`
  - 能力：top_level_orchestration
  - 用途：顶层程序入口候选，用于串联数据处理、训练与测试流程
  - 复用状态：blocked；类型：code_entry
- `process_data.py`
  - 能力：data_preprocessing
  - 用途：数据读取、清洗与特征预处理辅助模块
  - 复用状态：blocked；类型：code_entry
- `model.py`
  - 能力：model_definition
  - 用途：TEFDTA 的模型结构定义，供训练或下游推理复用
  - 复用状态：blocked；类型：code_entry

### training

- `train_and_test.py`
  - 能力：training_and_testing_pipeline
  - 用途：训练、验证与测试流程；静态清单显示其同时承担训练模块和测试/检查用途
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清点，未执行仓库代码
- 依赖未安装，无法验证训练、推理与评估结果
- 未发现 checkpoint，无法确认可恢复权重
- 未发现独立推理入口，复现链路不完整

## 仍未知

- process_data.py 与 main.py 的实际运行顺序、参数和副作用未验证
- Davis/KIBA/CovalentData 的来源、样本规模与许可未从静态清单确认
- train_and_test.py 是否覆盖全部论文设定的实验协议未知
- metrics.py 的具体指标集合是否与论文完全一致未知

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
