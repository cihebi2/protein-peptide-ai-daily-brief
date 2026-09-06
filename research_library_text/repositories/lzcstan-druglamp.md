# Lzcstan/DrugLAMP

- **仓库：** [https://github.com/Lzcstan/DrugLAMP](https://github.com/Lzcstan/DrugLAMP)
- **固定 commit：** `d4f124bd276a20aec0d24676d79f13bd1939b219`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 17

## 仓库摘要

仓库是 DrugLAMP 论文的静态代码与数据快照，包含多版本模型、数据划分、训练脚本和配置，但未见 LICENSE 或 checkpoint。

## 可复用模块与资源

### datasets

- `datasets/bindingdb/full.csv`
  - 能力：BindingDB bundled benchmark
  - 用途：full.csv 与 cluster 划分（source_train/target_train/target_test）
  - 复用状态：unknown；类型：unknown
- `datasets/biosnap/full.csv`
  - 能力：BioSNAP bundled benchmark
  - 用途：full.csv、random 划分与 cluster 划分
  - 复用状态：unknown；类型：unknown
- `datasets/human/full.csv`
  - 能力：Human bundled benchmark
  - 用途：full.csv、random 划分与 cold 划分
  - 复用状态：unknown；类型：unknown
- `datasets/kinase/full.csv`
  - 能力：Kinase bundled benchmark/raw text
  - 用途：full.csv、random 划分，以及 kinase_train_original.txt / kinase_test.txt
  - 复用状态：unknown；类型：unknown

### evaluation

- `trainer.py`
  - 能力：评估逻辑可能内嵌于训练流程
  - 用途：验证/测试与指标计算可能在该训练脚本内；未见独立 evaluation 模块
  - 复用状态：unknown；类型：code_entry

### inference

- `main.py`
  - 能力：顶层运行入口
  - 用途：统一入口；静态上可能分发训练/推理/评估，但未执行无法确认
  - 复用状态：unknown；类型：code_entry

### reusable_assets

- `model/DrugLAMP.py`
  - 能力：DrugLAMP 主模型
  - 用途：主干 DTI 预测网络实现
  - 复用状态：blocked；类型：code_entry
- `model/DrugLAMP2C2P.py`
  - 能力：DrugLAMP2C2P 变体
  - 用途：对照/替代模型实现
  - 复用状态：blocked；类型：code_entry
- `model/DrugLAMPwoLLM.py`
  - 能力：DrugLAMPwoLLM 消融
  - 用途：去除 LLM 分支的消融版本
  - 复用状态：blocked；类型：code_entry
- `model/PGCA/guided_cross_attention_model.py`
  - 能力：PGCA/PMMA 注意力子模块
  - 用途：guided cross-attention 与 paired multi-model attention 核心组件
  - 复用状态：blocked；类型：code_entry
- `model/basic_model.py`
  - 能力：共享模型基础组件
  - 用途：基础层、跨模态与自监督辅助模块
  - 复用状态：blocked；类型：code_entry
- `handler/dataset.py`
  - 能力：数据读取/样本构建
  - 用途：读取 CSV/TXT 并构建训练/验证/测试样本
  - 复用状态：blocked；类型：code_entry
- `configs/DrugLAMP.yaml`
  - 能力：实验配置
  - 用途：模型超参与实验设置；还包含 DrugLAMP2C2P.yaml、DrugLAMPwoLLM.yaml、default_config.py、30_layers_params.txt
  - 复用状态：blocked；类型：config
- `scheduler/cosine_annealing_warmup.py`
  - 能力：学习率调度器
  - 用途：warmup + cosine annealing 学习率调度
  - 复用状态：blocked；类型：code_entry

### training

- `trainer.py`
  - 能力：训练循环
  - 用途：训练、验证与结果记录的主流程
  - 复用状态：blocked；类型：code_entry
- `scripts/bindingdb/cluster/DrugLAMP.sh`
  - 能力：批量启动脚本
  - 用途：按数据集/划分启动实验；可见 bindingdb、biosnap、human、kinase 的多个 shell 启动脚本
  - 复用状态：blocked；类型：code_entry
- `env/drug_lamp.yml`
  - 能力：运行环境定义
  - 用途：conda/pip 依赖环境定义
  - 复用状态：blocked；类型：config

## 使用限制

- 仅做静态审查，未执行代码、训练或测试
- dependencies_not_installed
- repository_code_not_executed
- tests_not_run
- 未发现 checkpoint 文件
- 未发现独立 LICENSE 文件

## 仍未知

- main.py 与 trainer.py 的实际训练/推理/评估分支无法在静态路径层面完全确认
- datasets/kinase 的原始来源与许可未核实
- 各 bundled CSV/TXT 是否可依法外部再分发无法从快照直接证明

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
