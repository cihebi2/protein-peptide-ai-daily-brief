# aksh555/LoRA-Soups

- **仓库：** [https://github.com/aksh555/LoRA-Soups](https://github.com/aksh555/LoRA-Soups)
- **固定 commit：** `7ce7a2e6ddde687db5a15bdabbbea4516f042bf6`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 15

## 仓库摘要

该仓库是 LoRA Soups 的对应代码/数据仓库：包含 Learnable LoRA 核心实现、category/skill 训练与评测脚本，以及 few-shot、skill、test 三类数据材料；未发现 LICENSE 或 checkpoint，且未执行任何运行时验证。

## 可复用模块与资源

### datasets

- `data/few_shot_demo/math.json`
  - 能力：few-shot demo prompts
  - 用途：few-shot 示例材料，覆盖 math/qa/rc 的演示输入
  - 复用状态：blocked；类型：config
- `data/skill_datasets/alpaca_data_cleaned.json`
  - 能力：skill training corpora
  - 用途：instruction tuning 与 skill mixture 训练语料；包含 Alpaca、CodeAlpaca、MetaMath、SQuADv2、BioAlpaca 等命名分片
  - 复用状态：blocked；类型：config
- `data/test_datasets/math/test.json`
  - 能力：held-out test sets
  - 用途：math/qa/rc 与 prompt-format 的测试集
  - 复用状态：blocked；类型：config

### evaluation

- `eval_cat.sh`
  - 能力：category evaluation
  - 用途：category 任务评测封装
  - 复用状态：blocked；类型：code_entry
- `eval_skill.sh`
  - 能力：skill evaluation
  - 用途：skill 任务评测封装
  - 复用状态：blocked；类型：code_entry
- `evaluate.py`
  - 能力：metric / score computation
  - 用途：统一计算评测指标与汇总结果
  - 复用状态：blocked；类型：code_entry

### inference

- `evaluate.py`
  - 能力：推理/生成入口
  - 用途：评测驱动的模型调用与生成；未见独立 inference CLI
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `learnable_lora/lora/model.py`
  - 能力：LoRA/adapter 模型封装与合并
  - 用途：实现 Learnable LoRA 的核心模型包装、adapter 组合与合并逻辑
  - 复用状态：blocked；类型：code_entry
- `learnable_lora/lora/layer.py`
  - 能力：LoRA 层、配置与量化后端适配
  - 用途：提供 LoRA layer/config 以及 bnb、gptq、mapping 等后端接入
  - 复用状态：blocked；类型：code_entry
- `try_llama/modeling_llama.py`
  - 能力：Llama 模型变体
  - 用途：提供 Llama 架构的本地改写/封装，供训练与评测调用
  - 复用状态：blocked；类型：code_entry
- `cat_train_utils.py`
  - 能力：训练辅助工具
  - 用途：承载训练过程中的数据整理、prompt 处理或公共辅助函数
  - 复用状态：blocked；类型：code_entry

### training

- `cat_train.py`
  - 能力：category training entrypoint
  - 用途：启动 category / cat 任务训练
  - 复用状态：blocked；类型：code_entry
- `skill_finetune.py`
  - 能力：skill fine-tuning entrypoint
  - 用途：启动 skill 任务微调
  - 复用状态：blocked；类型：code_entry
- `train_cat.sh`
  - 能力：category training launcher
  - 用途：shell 封装训练参数与执行
  - 复用状态：blocked；类型：code_entry
- `train_skill.sh`
  - 能力：skill training launcher
  - 用途：shell 封装 skill 微调流程
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未安装依赖、未运行训练或评测。
- 仓库未发现显式 checkpoint，无法从静态路径确认可直接加载的权重。
- 数据文件多为命名式分片，无法仅凭路径确认其真实来源、清洗规则与数据许可。
- 部分路径可能是第三方实现的改写或搬运，但在未读到文件内容前不能做强断言。

## 仍未知

- `try_llama/modeling_llama.py` 是否为 vendored 第三方代码或本地改写，静态路径不足以判定。
- `evaluate.py` 是纯评测汇总还是同时承担生成推理，未执行无法确认。
- `data/skill_datasets/*.json` 与 `data/test_datasets/*.json` 的上游许可与去重规则未知。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
