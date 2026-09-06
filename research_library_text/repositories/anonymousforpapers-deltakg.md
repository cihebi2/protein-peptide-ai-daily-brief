# AnonymousForPapers/DeltaKG

- **仓库：** [https://github.com/AnonymousForPapers/DeltaKG](https://github.com/AnonymousForPapers/DeltaKG)
- **固定 commit：** `8bdd709c717d4b573fb2a97106ba29446d90c16b`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 23

## 仓库摘要

这是一个静态代码仓，核心围绕 MEND 及其 ft/enn/efk 变体、KG editing 训练器、FEVER/NQ/Wiki/ZSRE/KGC 数据处理器，以及 CaliNet/K-Adapter/KE/KGEditor 基线入口；可见 YAML 和 shell 脚本覆盖 FB15k237 与 WN18RR 的 add/edit 实验，但未发现 bundled data、checkpoint 或 LICENSE。

## 可复用模块与资源

### datasets

- `models/MEND/data_classes/fever.py`
  - 能力：FEVER 数据处理
  - 用途：FEVER 样本读取/编码
  - 复用状态：blocked；类型：code_entry
- `models/MEND/data_classes/nq.py`
  - 能力：Natural Questions 数据处理
  - 用途：NQ 样本读取/编码
  - 复用状态：blocked；类型：code_entry
- `models/MEND/data_classes/wiki.py`
  - 能力：Wiki 数据处理
  - 用途：Wiki 相关样本读取/编码
  - 复用状态：blocked；类型：code_entry
- `models/MEND/data_classes/zsre.py`
  - 能力：ZSRE 数据处理
  - 用途：ZSRE 编辑样本读取/编码
  - 复用状态：blocked；类型：code_entry
- `models/MEND/data_classes/kgc.py`
  - 能力：KGC / KG-BERT 数据处理
  - 用途：知识图谱补全与编辑任务的数据样本构造
  - 复用状态：blocked；类型：code_entry
- `src/data/data_module.py`
  - 能力：共享数据抽象层
  - 用途：统一封装外部下载数据与 batch 组织
  - 复用状态：blocked；类型：code_entry

### evaluation

- `models/MEND/trainer.py`
  - 能力：验证集评估流程
  - 用途：验证集指标聚合与结果记录
  - 复用状态：blocked；类型：code_entry
- `models/MEND/oracle.py`
  - 能力：结果排序/评测辅助
  - 用途：为评测提供 oracle 式结果选择
  - 复用状态：blocked；类型：code_entry
- `src/models/trainer.py`
  - 能力：通用 evaluation loop
  - 用途：通用训练/验证/评估封装
  - 复用状态：blocked；类型：code_entry

### inference

- `models/MEND/run.py`
  - 能力：MEND 运行/推理入口
  - 用途：编辑结果运行与汇总
  - 复用状态：blocked；类型：code_entry
- `models/MEND/oracle.py`
  - 能力：oracle 辅助打分
  - 用途：候选结果选择与打分辅助
  - 复用状态：blocked；类型：code_entry
- `models/KGEditor/run.py`
  - 能力：基线推理入口
  - 用途：KGEditor 对比方法的运行入口
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `models/MEND/algs/mend.py`
  - 能力：MEND 核心编辑算法
  - 用途：实现知识图谱嵌入/模型参数编辑的主算法，并与 ft/enn/efk 变体协同
  - 复用状态：blocked；类型：code_entry
- `models/MEND/trainer.py`
  - 能力：训练与损失/Hook 组织
  - 用途：训练循环、hook、loss 与可编辑模型接口的组织
  - 复用状态：blocked；类型：code_entry
- `models/MEND/data_classes/kgc.py`
  - 能力：知识图谱编辑数据管线
  - 用途：FB15k237/WN18RR 等 KG editing / completion 任务的数据读取与批处理
  - 复用状态：blocked；类型：code_entry
- `models/MEND/data_classes/fever.py`
  - 能力：文本任务数据处理
  - 用途：FEVER、NQ、Wiki、ZSRE 等文本任务样本读取与格式化
  - 复用状态：blocked；类型：code_entry
- `models/MEND/config/config.yaml`
  - 能力：实验配置与启动脚本
  - 用途：算法/模型/实验配置，覆盖多种 backbone 与实验类型；并配套 FB15k237/WN18RR 的 add/edit 任务脚本
  - 复用状态：blocked；类型：config
- `models/CaliNet/run.py`
  - 能力：基线方法入口
  - 用途：CaliNet、K-Adapter、KE、KGEditor 的对比实验入口
  - 复用状态：blocked；类型：code_entry
- `src/models/modeling_bert.py`
  - 能力：通用 BERT/优化器底层模块
  - 用途：底层 BERT/优化器实现，支撑模型构建与训练
  - 复用状态：unknown；类型：code_entry

### training

- `models/MEND/trainer.py`
  - 能力：MEND 训练主循环
  - 用途：训练与验证流程
  - 复用状态：blocked；类型：code_entry
- `src/models/trainer.py`
  - 能力：通用训练器封装
  - 用途：通用训练/验证的二次封装
  - 复用状态：blocked；类型：code_entry
- `scripts/MEND/MEND_FB15k237_add.sh`
  - 能力：任务启动脚本
  - 用途：MEND 在 FB15k237/WN18RR add/edit 任务上的启动
  - 复用状态：blocked；类型：code_entry
- `run.sh`
  - 能力：仓库级批量运行脚本
  - 用途：统一串联多个实验命令
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未运行代码或测试
- 未发现 bundled data
- 未发现 tracked checkpoint 文件
- 未发现 LICENSE/NOTICE，直接复用受限
- 依赖未安装，外部下载数据/模型未核验
- submodule 未初始化，外部内容可能缺失

## 仍未知

- `src/models/modeling_bert.py` 与 `src/models/optimization.py` 的来源是否为 vendored third-party 未确认
- `models/MEND/run.py`、`models/MEND/oracle.py` 的实际推理/评测行为未执行验证
- 训练脚本是否自动下载数据或模型、以及下载源许可未核实

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
