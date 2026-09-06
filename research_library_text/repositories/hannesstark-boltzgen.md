# HannesStark/boltzgen

- **仓库：** [https://github.com/HannesStark/boltzgen](https://github.com/HannesStark/boltzgen)
- **固定 commit：** `a3149cf18eeb58648d1abbb27539bd73f746cdda`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 12

## 仓库摘要

这是一个面向 binder design 的静态代码库：MIT 代码许可已见，训练、推理、验证与数据处理模块齐全，但未见 checkpoint；示例数据与 split 资源存在来源/许可未明的边界。

## 可复用模块与资源

### datasets

- `example/small_molecule_from_file_and_smiles/4g37.pdb`
  - 能力：示例输入结构与任务参数
  - 用途：作为 small-molecule 示例输入和演示任务的静态样例。
  - 复用状态：partial；类型：unknown
- `src/boltzgen/resources/splits/validation_ids_boltz2_all.txt`
  - 能力：验证切分与评估索引
  - 用途：定义验证集与评估子集的索引清单，而不是原始训练语料。
  - 复用状态：partial；类型：unknown

### evaluation

- `src/boltzgen/model/validation/validator.py`
  - 能力：验证与评分框架
  - 用途：执行 design、refolding、rcsb 等验证检查，并结合指标归一化资源。
  - 复用状态：ready_for_review；类型：code_entry
- `tests/test_residue_constraints.py`
  - 能力：约束逻辑回归测试
  - 用途：检查 inverse folding 与 residue constraint 掩码的一致性。
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `src/boltzgen/task/predict/predict.py`
  - 能力：推理入口与结果写出
  - 用途：组织推理流程、加载模型与写出预测结果。
  - 复用状态：ready_for_review；类型：code_entry
- `src/boltzgen/task/predict/data_from_yaml.py`
  - 能力：推理输入适配
  - 用途：把 YAML、generated 结果、ligand 与 protein-binder 规格转换为推理输入。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/boltzgen/data/data.py`
  - 能力：数据解析与预处理管线
  - 用途：将 mmCIF/PDB/A3M 解析为模型输入，并支持过滤、裁剪、特征化与写回结构文件。
  - 复用状态：ready_for_review；类型：code_entry
- `src/boltzgen/model/models/boltz.py`
  - 能力：主干模型与几何更新层
  - 用途：提供核心表示学习主干，包含 Pairformer 与 triangular attention 一类的结构更新模块。
  - 复用状态：ready_for_review；类型：code_entry
- `src/boltzgen/model/modules/diffusion.py`
  - 能力：扩散式生成与条件化模块
  - 用途：支持候选 binder 生成、条件控制，以及 inverse folding、affinity、confidence 等辅助头。
  - 复用状态：ready_for_review；类型：code_entry
- `src/boltzgen/model/optim/ema.py`
  - 能力：训练稳定化与优化辅助
  - 用途：提供 EMA 与学习率调度等训练稳定化组件。
  - 复用状态：ready_for_review；类型：code_entry

### training

- `src/boltzgen/task/train/train.py`
  - 能力：训练入口
  - 用途：驱动训练流程、数据装载与优化步骤。
  - 复用状态：ready_for_review；类型：code_entry
- `src/boltzgen/resources/config/train/boltzgen.yaml`
  - 能力：训练配置 recipes
  - 用途：提供默认训练配置及变体，包括 small、no_distillation 和 inverse_folding 方案。
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做冻结清单静态审阅，未执行代码、测试、训练或推理。
- 未安装依赖，无法验证入口在当前环境中的可运行性。
- 示例结构、split 清单与资源文件的来源和数据许可未在冻结清单中得到证明。
- 未发现 checkpoint 文件，无法评价实际发布权重或可直接复现的模型产物。

## 仍未知

- example/* 文件是否来自外部 PDB/CCD 数据以及是否允许再分发，未能确认。
- 训练语料与预训练权重的具体来源和版本未在冻结清单中直接证明。
- 验证脚本与指标资源的实际执行结果未被验证。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
