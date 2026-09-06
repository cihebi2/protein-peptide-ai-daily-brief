# ak422/DDAffinity

- **仓库：** [https://github.com/ak422/DDAffinity](https://github.com/ak422/DDAffinity)
- **固定 commit：** `2055bc50f9a4d2920dfcb00635ecef886f927a84`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 20

## 仓库摘要

仓库提供了 DDAffinity 的结构化训练、推断与测试配置，以及 SKEMPI v2 相关的数据准备和 ProteinMPNN 风格模型代码；但当前冻结快照未包含可复核的实际 checkpoint 或运行结果。

## 可复用模块与资源

### checkpoints

- `trained_models/README.md`
  - 能力：checkpoint reference only
  - 用途：仅提示已训练模型存放位置或获取方式；未见实际权重文件
  - 复用状态：blocked；类型：unknown

### datasets

- `data/get_skempi_v2.sh`
  - 能力：SKEMPI v2 download script
  - 用途：下载或准备外部 SKEMPI v2 相关数据；仓库未见打包原始数据
  - 复用状态：partial；类型：code_entry
- `rde/datasets/skempi_parallel.py`
  - 能力：parallel SKEMPI dataset loader
  - 用途：并行读取/组织 SKEMPI 变体样本供训练或验证
  - 复用状态：partial；类型：code_entry
- `rde/utils/data_skempi_mpnn.py`
  - 能力：MPNN data formatting utility
  - 用途：把 SKEMPI/PDB 样本整理为 ProteinMPNN 风格输入
  - 复用状态：partial；类型：code_entry
- `configs/common/data_train_chain.yml`
  - 能力：train split config
  - 用途：训练数据链路/拆分配置
  - 复用状态：partial；类型：config
- `configs/common/data_val_chain.yml`
  - 能力：validation split config
  - 用途：验证数据链路/拆分配置
  - 复用状态：partial；类型：config

### evaluation

- `test_DDAffinity.py`
  - 能力：test harness
  - 用途：仓库级测试/验证脚本
  - 复用状态：ready_for_review；类型：code_entry
- `rde/linear/calibrate.py`
  - 能力：calibration utility
  - 用途：预测分数校准或后处理评估
  - 复用状态：partial；类型：code_entry
- `rde/linear/entropy.py`
  - 能力：entropy analysis utility
  - 用途：不确定性/熵分析辅助评估
  - 复用状态：partial；类型：code_entry

### inference

- `configs/inference/blind_testing.yml`
  - 能力：blind testing config
  - 用途：盲测/外部测试推断配置
  - 复用状态：partial；类型：config
- `configs/inference/case_study_1.yml`
  - 能力：case study config
  - 用途：案例推断配置
  - 复用状态：partial；类型：config
- `configs/inference/case_study_2.yml`
  - 能力：case study config
  - 用途：第二组案例推断配置
  - 复用状态：partial；类型：config
- `case_study.py`
  - 能力：case study runner
  - 用途：案例分析或推断脚本入口
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `rde/models/protein_mpnn_network_2.py`
  - 能力：model architecture
  - 用途：核心蛋白结构建模与ΔΔG/亲和力变化预测网络
  - 复用状态：partial；类型：code_entry
- `rde/modules/common/geometry.py`
  - 能力：shared geometry utilities
  - 用途：几何/坐标变换/结构表示相关基础函数
  - 复用状态：partial；类型：code_entry
- `rde/modules/common/layers.py`
  - 能力：shared neural layers
  - 用途：通用神经网络层封装，供模型与训练代码复用
  - 复用状态：partial；类型：code_entry
- `rde/modules/common/topology.py`
  - 能力：topology helpers
  - 用途：结构拓扑/邻接关系辅助逻辑
  - 复用状态：partial；类型：code_entry

### training

- `train_DDAffinity.py`
  - 能力：training entrypoint
  - 用途：顶层训练入口，调度 DDAffinity 训练流程
  - 复用状态：partial；类型：code_entry
- `rde/utils/train_mpnn.py`
  - 能力：training loop helper
  - 用途：训练循环、优化与日志相关辅助逻辑
  - 复用状态：partial；类型：code_entry
- `configs/train/mpnn_ddg.yml`
  - 能力：training recipe
  - 用途：训练超参数与任务配置
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅静态路径证据，未执行代码或测试
- 依赖未安装，无法验证运行时行为
- 未见实际 checkpoint 文件，不能证明可复现训练
- 仓库内容可能引用外部数据，数据许可与可用性未核实

## 仍未知

- configs/inference/*.yml 的具体参数和执行顺序未读到文件内容
- data/get_skempi_v2.sh 目标下载源与条款未核实
- trained_models/README.md 是否指向公开权重尚未确认

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
