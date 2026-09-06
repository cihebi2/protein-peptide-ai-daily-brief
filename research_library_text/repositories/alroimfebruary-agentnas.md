# alroimfebruary/AgentNAS

- **仓库：** [https://github.com/alroimfebruary/AgentNAS](https://github.com/alroimfebruary/AgentNAS)
- **固定 commit：** `832ca1a603105bb348acced75aadf699a776d81d`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 18

## 仓库摘要

该仓库是一个 MIT 许可的 AgentNAS 代码库，静态清单显示其核心由代理编排、搜索空间语法、阶段式流程、训练/搜索、benchmark 封装、配置与测试构成；未随仓库打包数据集或 checkpoint，因此可复用的主要是源代码与实验配置，而不是已训练产物。

## 可复用模块与资源

### datasets

- `configs/blind_readmes/addnist.md`
  - 能力：外部 benchmark 任务说明/数据契约
  - 用途：记录 AddNIST、Chesseract、CIFAR100、CIFARTile、GeoClassing、Gutenberg、Language、MultNIST 等任务的实验设定与数据接口要求；未包含原始数据文件。
  - 复用状态：partial；类型：unknown
- `src/agentnas/benchmarks/cifar100.py`
  - 能力：benchmark 数据接口封装
  - 用途：定义 CIFAR100、Cosmic、DarcyFlow、DeepSEA、ECG、FSD50K、NiNapro、PSICOV、Satellite、Spherical、Simple、Unseen 等数据/任务适配层。
  - 复用状态：partial；类型：code_entry
- `scripts/prepare_explorer_data.py`
  - 能力：数据预处理与预计算管线
  - 用途：把外部数据整理为仓库预期格式，并对 FSD50K 做预计算；原始数据未随仓库分发。
  - 复用状态：partial；类型：code_entry

### evaluation

- `src/agentnas/training/metrics.py`
  - 能力：指标计算
  - 用途：计算训练/搜索过程中的评估指标。
  - 复用状态：ready_for_review；类型：code_entry
- `src/agentnas/results.py`
  - 能力：结果汇总
  - 用途：聚合、整理并输出实验结果。
  - 复用状态：ready_for_review；类型：code_entry
- `tests/test_benchmarks.py`
  - 能力：benchmark / results smoke tests
  - 用途：对 benchmark 适配与结果流程做静态测试覆盖。
  - 复用状态：partial；类型：code_entry

### inference

- `src/agentnas/cli.py`
  - 能力：命令行与 LLM 调用壳
  - 用途：静态上看用于命令行触发与 LLM 交互/调用，是运行时推断链路的外层入口。
  - 复用状态：partial；类型：code_entry
- `src/agentnas/agents/explorer.py`
  - 能力：候选生成与执行链路
  - 用途：支撑代理式候选提出、执行与多阶段串联；未见单独的 inference service 目录。
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `src/agentnas/agents/explorer.py`
  - 能力：代理编排与任务分解
  - 用途：包含 explorer、planner、executor、modularizer、task_author 等代理角色，实现 AgentNAS 的候选生成、规划与执行编排。
  - 复用状态：ready_for_review；类型：code_entry
- `src/agentnas/grammar/fixed_seeds.py`
  - 能力：搜索空间 grammar 与变异
  - 用途：提供 fixed_seeds、slots、mutator、supernet 等搜索空间定义与结构变异能力。
  - 复用状态：ready_for_review；类型：code_entry
- `src/agentnas/phases/phase1.py`
  - 能力：阶段式 NAS 流程
  - 用途：按 phase1、phase1_5_modularize、phase2、phase3、phase3_gdas 组织多阶段搜索与收敛流程。
  - 复用状态：ready_for_review；类型：code_entry
- `src/agentnas/training/config.py`
  - 能力：训练与搜索实现
  - 用途：包含 config、gdas_search、harness、worker、metrics，用于训练/搜索编排与度量。
  - 复用状态：ready_for_review；类型：config
- `src/agentnas/benchmarks/cifar100.py`
  - 能力：benchmark 与任务封装
  - 用途：封装 CIFAR100、Cosmic、DarcyFlow、DeepSEA、ECG、FSD50K、NiNapro、PSICOV、Satellite、Spherical、Simple、Unseen 等 benchmark 适配层；数据本体未随仓库分发。
  - 复用状态：partial；类型：code_entry
- `configs/default.yaml`
  - 能力：实验配置与 recipe
  - 用途：提供 default.yaml、production.yaml 以及各 benchmark 的 blind/explorer README 形式配置，支撑实验参数化复用。
  - 复用状态：ready_for_review；类型：config
- `examples/custom_task/full_custom_task.py`
  - 能力：自定义任务示例
  - 用途：提供 full_custom_task.py、make_toy_data.py、toy_task.py，作为扩展新任务的模板。
  - 复用状态：ready_for_review；类型：code_entry

### training

- `src/agentnas/training/config.py`
  - 能力：NAS 训练/搜索核心
  - 用途：封装训练配置、GDAS 搜索、harness、worker 与 metrics，是仓库的主要训练实现。
  - 复用状态：ready_for_review；类型：config
- `scripts/run_production.py`
  - 能力：生产运行编排
  - 用途：静态上看是启动 production 流程的脚本，可作为实验/训练编排入口候选。
  - 复用状态：partial；类型：code_entry
- `configs/default.yaml`
  - 能力：运行参数配置
  - 用途：定义默认与生产实验参数，供训练/搜索流程读取。
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做静态清单审查，未安装依赖、未运行代码、未执行测试。
- 未发现 tracked checkpoint 或权重文件，无法核验训练后产物与推理复现。
- 数据集本体未随仓库分发，外部数据来源与授权未在静态清单中核验。
- `scripts/run_production.py`、`src/agentnas/cli.py` 等运行入口仅见路径，不代表已验证可执行。

## 仍未知

- README 的完整使用说明与默认运行参数未逐页核实。
- 各 benchmark 的原始数据获取地址、预处理细节和许可证未从静态清单中确认。
- `src/agentnas/llm/client.py` 依赖的具体模型/provider 配置未核验。
- 仓库是否存在未跟踪的大文件或 LFS/promisor 内容无法从当前静态清单确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
