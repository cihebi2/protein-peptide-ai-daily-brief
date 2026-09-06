# alibaba/graph-gpt

- **仓库：** [https://github.com/alibaba/graph-gpt](https://github.com/alibaba/graph-gpt)
- **固定 commit：** `69e007169b7a177d32bb43f7a2af68567fc58539`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 15

## 仓库摘要

该仓库是 GraphGPT 的静态代码底座，覆盖图 tokenization、预训练/微调、配置驱动训练与基础评测；未见已跟踪 checkpoint，数据与外部许可边界仍需单独核实。

## 可复用模块与资源

### datasets

- `data/Custom/spice_circuit/vocab512`
  - 能力：spice_circuit 本地词表/元素表
  - 用途：spice_circuit 任务的本地词表与元素集合；更像派生资源而非原始语料
  - 复用状态：partial；类型：tokenizer
- `data/OGB/ogbg_molpcba/vocab`
  - 能力：OGB 任务 vocab 资源
  - 用途：OGB 图任务的本地词表资源；不等同于完整数据集包
  - 复用状态：partial；类型：tokenizer
- `data/OGB/chembl29/RELEASE_v1.txt`
  - 能力：数据版本标记
  - 用途：外部数据发布版本锁定/追踪；不是模型权重
  - 复用状态：unknown；类型：unknown

### evaluation

- `src/utils/metrics_utils.py`
  - 能力：指标计算
  - 用途：验证/评测指标定义与汇总
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `src/utils/generation_utils.py`
  - 能力：generation / inference helper
  - 用途：生成调用与推断辅助；当前未见独立服务化入口
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `src/data/tokenizer/core.py`
  - 能力：graph tokenization 与序列化
  - 用途：图结构编码、Eulerian/packing/padding/masking、词表构建与任务前处理
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/graphgpt/modeling_graphgpt.py`
  - 能力：GraphGPT 模型定义
  - 用途：pretrain/finetune 模型与配置实现
  - 复用状态：ready_for_review；类型：code_entry
- `src/training/pipeline.py`
  - 能力：训练编排
  - 用途：pre-training 与 fine-tuning 的 mode/pipeline 封装
  - 复用状态：ready_for_review；类型：code_entry
- `configs/config.yaml`
  - 能力：配置模板
  - 用途：模型/分词/训练/生成 YAML；覆盖 node/edge/graph benchmarks
  - 复用状态：ready_for_review；类型：config
- `examples/ds_config2.json`
  - 能力：distributed training configs
  - 用途：DeepSpeed runtime/bf16/pretraining 模板
  - 复用状态：partial；类型：config
- `src/utils/metrics_utils.py`
  - 能力：metrics/evaluation helper
  - 用途：任务指标/评估统计
  - 复用状态：ready_for_review；类型：code_entry
- `configs/generation/base.yaml`
  - 能力：generation / inference config
  - 用途：生成超参数模板；未见独立推理 CLI/serving 入口
  - 复用状态：partial；类型：config

### training

- `src/data/tokenizer/strategies/task_prep/pretrain.py`
  - 能力：预训练任务准备
  - 用途：构造 pretrain 样本与任务前处理
  - 复用状态：ready_for_review；类型：code_entry
- `examples/train_pretrain.py`
  - 能力：训练入口与模式切换
  - 用途：预训练/监督训练入口脚本
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils/training_utils.py`
  - 能力：训练支撑工具
  - 用途：训练过程中的辅助逻辑与运行支撑
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单审查，未安装依赖、未运行代码、未跑测试/训练/推理
- 未发现任何 tracked checkpoint/权重文件，无法据此判断模型参数可直接复用
- data/ 下多为 vocab/版本标记类辅助资源，原始训练数据来源与权利链条未核实
- README 与配置文件只能证明存在声明或模板，不构成端到端复现证据

## 仍未知

- `data/Custom/spice_circuit/*` 与 `data/OGB/*` 的生成来源、派生流程与授权边界不明
- `examples/ds_config2*.json` 更像 DeepSpeed 运行模板，但是否与特定实验一一对应无法从静态清单确认
- 是否存在仓库外下载的完整数据集/权重，当前清单无法证明

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
