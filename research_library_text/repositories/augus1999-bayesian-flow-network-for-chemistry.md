# Augus1999/bayesian-flow-network-for-chemistry

- **仓库：** [https://github.com/Augus1999/bayesian-flow-network-for-chemistry](https://github.com/Augus1999/bayesian-flow-network-for-chemistry)
- **固定 commit：** `07020a8cddd2d05deda5a6a955d8287d2dcad329`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 24

## 仓库摘要

该仓库是化学任务的 Bayesian Flow Network 实现与示例集合，包含模型、数据加载、训练、推理、评测脚本和一个预置 checkpoint；本次仅做静态清单审查，未运行代码或测试。

## 可复用模块与资源

### checkpoints

- `bayesianflow_for_chem/_data/coll_ae_v1.2.pt`
  - 能力：预置权重/自动编码器 checkpoint
  - 用途：仓库内置的模型权重文件，可能用于初始化或下游推理。
  - 复用状态：unknown；类型：model_weight

### datasets

- `bayesianflow_for_chem/_data/vocab.txt`
  - 能力：分子词表/字符集合
  - 用途：作为分子表示与输入编码的词表资源。
  - 复用状态：partial；类型：tokenizer

### evaluation

- `example/script/run_guacamol.py`
  - 能力：基准评测脚本
  - 用途：运行 GuacaMol 相关生成/评测流程。
  - 复用状态：partial；类型：code_entry
- `example/script/run_moses.py`
  - 能力：基准评测脚本
  - 用途：运行 MOSES 相关生成/评测流程。
  - 复用状态：partial；类型：code_entry
- `example/script/run_zinc250k.py`
  - 能力：基准评测脚本
  - 用途：运行 ZINC250k 相关生成/评测流程。
  - 复用状态：partial；类型：code_entry
- `test/test_qsar_test_function.py`
  - 能力：QSAR 测试
  - 用途：验证 QSAR 相关测试函数。
  - 复用状态：partial；类型：code_entry
- `test/test_split_dataset.py`
  - 能力：数据切分测试
  - 用途：验证数据集切分逻辑。
  - 复用状态：partial；类型：code_entry
- `test/test_molecular_embedding.py`
  - 能力：分子嵌入测试
  - 用途：验证分子嵌入相关功能。
  - 复用状态：partial；类型：code_entry
- `test/test_jit_compatibility.py`
  - 能力：JIT 兼容性测试
  - 用途：检查模型或模块的 JIT 兼容性。
  - 复用状态：partial；类型：code_entry
- `.github/workflows/pytest.yml`
  - 能力：CI 测试工作流
  - 用途：定义 pytest 持续集成执行。
  - 复用状态：partial；类型：config

### inference

- `example/script/masked_diffusion.py`
  - 能力：生成/采样接口
  - 用途：提供 masked diffusion 的生成或采样示例。
  - 复用状态：partial；类型：code_entry
- `bayesianflow_for_chem/cli.py`
  - 能力：命令行推理入口
  - 用途：用于触发模型相关命令行推理或生成流程。
  - 复用状态：partial；类型：code_entry
- `bayesianflow_for_chem/tool.py`
  - 能力：辅助生成工具
  - 用途：支持推理过程中的辅助操作与任务编排。
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `bayesianflow_for_chem/model.py`
  - 能力：模型架构
  - 用途：定义核心 Bayesian Flow Network 模型结构。
  - 复用状态：partial；类型：code_entry
- `bayesianflow_for_chem/data.py`
  - 能力：数据加载
  - 用途：提供数据读取、预处理与切分相关逻辑。
  - 复用状态：partial；类型：code_entry
- `bayesianflow_for_chem/cli.py`
  - 能力：推理/命令行接口
  - 用途：暴露命令行入口，便于运行生成或模型相关操作。
  - 复用状态：partial；类型：code_entry
- `bayesianflow_for_chem/tool.py`
  - 能力：辅助工具
  - 用途：封装附加工具函数，支持流程组织与任务调用。
  - 复用状态：partial；类型：code_entry
- `bayesianflow_for_chem/scorer.py`
  - 能力：评分/打分辅助
  - 用途：提供候选分子或任务输出的评分逻辑。
  - 复用状态：partial；类型：code_entry
- `bayesianflow_for_chem/mlff.py`
  - 能力：MLFF 相关功能
  - 用途：支持 MLFF 相关实验或功能模块。
  - 复用状态：partial；类型：code_entry
- `example/cli/model_config.toml`
  - 能力：配置模板
  - 用途：提供 CLI/模型参数配置范例。
  - 复用状态：partial；类型：config

### training

- `bayesianflow_for_chem/train.py`
  - 能力：训练主入口
  - 用途：承载训练流程的主模块。
  - 复用状态：partial；类型：code_entry
- `example/script/pretrain.py`
  - 能力：预训练示例
  - 用途：提供预训练脚本示例。
  - 复用状态：partial；类型：code_entry
- `example/script/finetune.py`
  - 能力：微调示例
  - 用途：提供微调脚本示例。
  - 复用状态：partial；类型：code_entry
- `example/script/train_mlff.py`
  - 能力：MLFF 训练示例
  - 用途：提供 MLFF 相关训练入口。
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态路径审查，未执行代码、未安装依赖、未运行测试。
- 文件存在不代表已验证可复现；尤其 checkpoint 与 `_data` 资源的来源、训练语料和许可边界仍不明。
- 评测与基准主要体现为 example 脚本和 pytest 覆盖，未见静态证据证明其与论文实验完全一致。

## 仍未知

- `bayesianflow_for_chem/_data/vocab.txt` 与 `bayesianflow_for_chem/_data/coll_ae_v1.2.pt` 的生成来源和许可未能从静态清单确认。
- `example/script/run_guacamol.py`、`run_moses.py`、`run_zinc250k.py` 是否对应论文主实验，未执行无法验证。
- 仓库是否依赖外部下载数据、远程 checkpoint 或运行时生成资产，静态审查无法确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
