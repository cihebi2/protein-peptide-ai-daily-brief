# AI45Lab/ActorAttack

- **仓库：** [https://github.com/AI45Lab/ActorAttack](https://github.com/AI45Lab/ActorAttack)
- **固定 commit：** `3149db7f60f84d7e70075b5a3d75f84b196f5184`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 15

## 仓库摘要

该仓库静态上像一个面向 LLM 安全红队/攻击的流水线：包含数据 CSV、攻击与判分提示词、LoRA/QLoRA 微调脚本和编排模块；但未见 LICENSE、未跟踪到 checkpoint，也未执行代码，因此只能做路径级清点，不能证明可复现。

## 可复用模块与资源

### datasets

- `data/circuit_breaker_train.csv`
  - 能力：训练数据集
  - 用途：静态库存显示为训练用 CSV，可能用于攻击或过滤器相关样本
  - 复用状态：blocked；类型：unknown
- `data/harmbench.csv`
  - 能力：基准/评测数据集
  - 用途：静态库存显示为基准或参考 CSV，可能用于攻击输入、评测或对照
  - 复用状态：blocked；类型：unknown

### evaluation

- `judge.py`
  - 能力：判分/裁决
  - 用途：对攻击输出做自动判定或评分
  - 复用状态：blocked；类型：code_entry
- `prompts/attack_step_judge.txt`
  - 能力：判分提示词
  - 用途：定义攻击步骤或结果的裁决规则
  - 复用状态：blocked；类型：unknown
- `prompts/5_json_format.txt`
  - 能力：结构化输出格式
  - 用途：约束评测或中间结果输出为 JSON
  - 复用状态：blocked；类型：unknown

### inference

- `preattack.py`
  - 能力：攻击前推理/准备
  - 用途：在正式攻击前做样本准备或候选生成
  - 复用状态：blocked；类型：code_entry
- `inattack.py`
  - 能力：攻击时推理
  - 用途：执行攻击阶段的输入构造与模型调用
  - 复用状态：blocked；类型：code_entry
- `main.py`
  - 能力：顶层流程编排
  - 用途：串联攻击、判定与输出流程
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `prompts/1_extract.txt`
  - 能力：攻击提示模板集合
  - 用途：覆盖抽取、network/actor 建模、queries 生成、JSON 格式化、攻击改写、步骤判定和安全回复模板
  - 复用状态：blocked；类型：unknown
- `config.py`
  - 能力：运行配置
  - 用途：保存攻击流程与训练/推理所需配置常量
  - 复用状态：blocked；类型：config
- `utils.py`
  - 能力：通用工具函数
  - 用途：提供各脚本共享的辅助逻辑
  - 复用状态：blocked；类型：code_entry

### training

- `construct_dataset.py`
  - 能力：数据构造与整理
  - 用途：构造或清洗训练/评测所需数据
  - 复用状态：blocked；类型：code_entry
- `ft/llama3_8b_instruct_qlora.py`
  - 能力：LoRA/QLoRA 微调
  - 用途：对 Llama3 8B Instruct 做参数高效微调
  - 复用状态：blocked；类型：code_entry
- `ft/lora_train.sh`
  - 能力：训练启动脚本
  - 用途：启动 LoRA 训练流程
  - 复用状态：blocked；类型：code_entry
- `ft/lora_merge.sh`
  - 能力：权重合并脚本
  - 用途：合并 LoRA 适配器到基础模型
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态库存清点，未安装依赖、未运行代码、未执行测试。
- tracked 清单中未见 checkpoint/权重文件，不能证明可直接复现。
- CSV 数据的来源、许可和是否为第三方镜像，无法仅凭路径确认。
- README 仅提供声明性线索，不能替代运行证据。
- 外部基础模型权重及下载脚本未在冻结清单中得到验证。

## 仍未知

- data/harmbench.csv 的具体来源和许可边界未知。
- main.py、preattack.py、inattack.py 与 judge.py 的实际调用链只能从文件名推断。
- ft/llama3_8b_instruct_qlora.py 依赖的基础模型与训练超参是否完整未知。
- prompts/*.txt 的具体语义和覆盖范围只能按文件名判断。
- paper/ 目录中的图片是否对应论文最终结果，静态上无法核实。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
