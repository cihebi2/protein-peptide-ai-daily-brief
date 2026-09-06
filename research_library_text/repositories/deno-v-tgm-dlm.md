# Deno-V/tgm-dlm

- **仓库：** [https://github.com/Deno-V/tgm-dlm](https://github.com/Deno-V/tgm-dlm)
- **固定 commit：** `12b6c26c212b537044ad91639292a7f855eec9ed`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** mixed
- **资产记录数：** 17

## 仓库摘要

仓库主体是 `improved-diffusion` 的文本引导分子生成实现，辅以大规模 `transformers` vendored 代码、SMILES 数据和若干 checkpoint 说明；静态清单未能证明复现，且仓库顶层未见统一 LICENSE。

## 可复用模块与资源

### checkpoints

- `checkpoints/desc.txt`
  - 能力：主 checkpoint 目录说明
  - 用途：仅见 checkpoint 目录描述，未见权重本体
  - 复用状态：unknown；类型：unknown
- `correction_checkpoints/desc.txt`
  - 能力：修正 checkpoint 目录说明
  - 用途：仅见修正模型 checkpoint 目录描述
  - 复用状态：unknown；类型：unknown
- `bert-base-uncased/config.json`
  - 能力：基座模型配置/词表
  - 用途：预训练基座模型的 config/tokenizer/vocab 引用
  - 复用状态：blocked；类型：config

### datasets

- `datasets/SMILES/train.txt`
  - 能力：SMILES 数据集
  - 用途：分子 SMILES 的训练/验证/测试与词表生成
  - 复用状态：blocked；类型：unknown
- `transformers/examples/research_projects/rag/test_data/my_knowledge_dataset.csv`
  - 能力：RAG 演示知识库
  - 用途：RAG 示例的 dummy knowledge base
  - 复用状态：blocked；类型：unknown
- `transformers/examples/legacy/seq2seq/test_data/fsmt/fsmt_val_data.json`
  - 能力：FSMT 测试数据
  - 用途：seq2seq/FSMT 示例测试集
  - 复用状态：blocked；类型：config

### evaluation

- `improved-diffusion/control_gen/eval_control.py`
  - 能力：控制生成评估
  - 用途：control generation 与 infill 任务的离线评估
  - 复用状态：blocked；类型：code_entry
- `transformers/examples/research_projects/rag/eval_rag.py`
  - 能力：RAG 评测
  - 用途：RAG 与 end-to-end retriever 评估
  - 复用状态：blocked；类型：code_entry
- `transformers/src/transformers/benchmark/benchmark.py`
  - 能力：Benchmark 与指标
  - 用途：benchmark 框架与 SQuAD 指标
  - 复用状态：blocked；类型：code_entry

### inference

- `improved-diffusion/scripts/text_sample.py`
  - 能力：采样与插补推断
  - 用途：生成样本、插补与批量后处理；冻结库存未单列 inference 目录，但这些路径承担推断功能
  - 复用状态：blocked；类型：code_entry
- `transformers/src/transformers/pipelines/text_generation.py`
  - 能力：生成 pipeline
  - 用途：通用 text-generation / text2text-generation 推断接口
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `improved-diffusion/improved_diffusion/gaussian_diffusion.py`
  - 能力：扩散语言模型主干
  - 用途：定义 diffusion 过程与采样/训练核心
  - 复用状态：blocked；类型：code_entry
- `improved-diffusion/scripts/text_sample.py`
  - 能力：生成/插补/批量解码入口
  - 用途：采样、插补与批量解码的推断侧入口
  - 复用状态：blocked；类型：code_entry
- `transformers/src/transformers/trainer.py`
  - 能力：Transformers 通用训练与处理器代码
  - 用途：训练框架、数据处理与模型适配的 vendored 上游实现
  - 复用状态：blocked；类型：code_entry

### training

- `improved-diffusion/scripts/train.py`
  - 能力：主训练入口
  - 用途：分子 diffusion 模型训练
  - 复用状态：blocked；类型：code_entry
- `transformers/examples/research_projects/distillation/train.py`
  - 能力：蒸馏/序列到序列训练
  - 用途：distillation 训练流程与 training_configs
  - 复用状态：blocked；类型：code_entry
- `transformers/src/transformers/commands/train.py`
  - 能力：统一 Trainer 命令
  - 用途：通用训练 CLI 与 Trainer 框架
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查；未运行代码、未安装依赖、未执行测试。
- 冻结清单里 checkpoint 多为说明文本或配置/分词器文件，未见可验证权重本体。
- `datasets/SMILES` 的来源、构造过程与授权未在冻结证据中明确。
- `transformers/` 大量文件看起来是 vendored 上游代码，但未核验对应上游版本与改动范围。
- 仓库级 LICENSE 未找到，直接整体复用受限。

## 仍未知

- `improved-diffusion` 是否为原始自研实现还是对上游扩散代码的再包装，冻结证据不足。
- `bert-base-uncased/` 与 `scibert/` 目录是本地缓存、下载副本还是实验产物，未能确认。
- 推断脚本是否实际进入论文主实验链路，还是仅保留为通用工具，未能从静态清单判定。
- `transformers` 子树的具体许可证文本虽存在，但与仓库顶层许可边界仍需人工复核。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
