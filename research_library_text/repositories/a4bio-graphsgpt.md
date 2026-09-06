# A4Bio/GraphsGPT

- **仓库：** [https://github.com/A4Bio/GraphsGPT](https://github.com/A4Bio/GraphsGPT)
- **固定 commit：** `e71647c5a9e19322b4166bb7922c604778a71e1e`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 25

## 仓库摘要

该仓库是 GraphsGPT 的代码仓库，包含核心图生成模型、条件/无条件生成入口、representation 微调入口、MOSES/ZINC250K 评测脚本，以及若干内置数据与第三方评分资源；但未发现 LICENSE 或可核验 checkpoint，故当前仅能做静态 inventory，直接复用边界未明。

## 可复用模块与资源

### datasets

- `moses/data/train.csv.gz`
  - 能力：MOSES 训练集
  - 用途：MOSES 基准训练数据。
  - 复用状态：blocked；类型：unknown
- `moses/data/test.csv.gz`
  - 能力：MOSES 测试集
  - 用途：MOSES 基准测试数据。
  - 复用状态：blocked；类型：unknown
- `moses/data/test_scaffolds.csv.gz`
  - 能力：MOSES scaffold 测试集
  - 用途：MOSES scaffold 基准划分。
  - 复用状态：blocked；类型：unknown
- `data/zinc250k/all_250k_rndm_zinc_drugs_clean_3.txt`
  - 能力：ZINC250K 原始分子集
  - 用途：ZINC250K 相关生成实验与数据准备。
  - 复用状态：blocked；类型：unknown
- `data/zinc250k/valid_250k_rndm_zinc_drugs_clean_3.txt`
  - 能力：ZINC250K 验证集
  - 用途：ZINC250K 验证/开发划分。
  - 复用状态：blocked；类型：unknown
- `moses/data/test_stats.npz`
  - 能力：MOSES 预计算统计
  - 用途：MOSES 评测时的统计缓存。
  - 复用状态：blocked；类型：unknown
- `moses/data/test_scaffolds_stats.npz`
  - 能力：MOSES scaffold 预计算统计
  - 用途：MOSES scaffold 评测时的统计缓存。
  - 复用状态：blocked；类型：unknown

### evaluation

- `entrypoints/generation/evaluation/evaluate_moses_few_shot_sampling.py`
  - 能力：MOSES few-shot 评测入口
  - 用途：运行 MOSES 基准的 few-shot sampling 评测。
  - 复用状态：blocked；类型：code_entry
- `entrypoints/generation/evaluation/evaluate_zinc250k_few_shot_sampling.py`
  - 能力：ZINC250K few-shot 评测入口
  - 用途：运行 ZINC250K 基准的 few-shot sampling 评测。
  - 复用状态：blocked；类型：code_entry
- `moses/metrics.py`
  - 能力：MOSES 指标计算
  - 用途：计算生成分子的质量/多样性类指标。
  - 复用状态：blocked；类型：code_entry
- `scripts/generation/evaluation/moses.sh`
  - 能力：评测启动脚本
  - 用途：封装 MOSES/ZINC250K 评测命令。
  - 复用状态：blocked；类型：code_entry

### inference

- `entrypoints/generation/unconditional/generate.py`
  - 能力：无条件生成入口
  - 用途：按配置无条件采样分子图/分子。
  - 复用状态：blocked；类型：code_entry
- `entrypoints/generation/conditional/generate.py`
  - 能力：条件生成入口
  - 用途：按 scaffold 或属性约束进行条件采样。
  - 复用状态：blocked；类型：code_entry
- `scripts/generation/unconditional/examples/generate_strict.sh`
  - 能力：无条件生成示例脚本
  - 用途：展示严格约束的无条件生成调用方式。
  - 复用状态：blocked；类型：code_entry
- `scripts/generation/conditional/examples/generate_scaffold_logp.sh`
  - 能力：条件 scaffold 生成示例脚本
  - 用途：展示 scaffold 约束下的属性控制生成调用方式。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `models/graphsgpt/modeling_graphsgpt.py`
  - 能力：GraphsGPT 核心生成模型
  - 用途：实现主图生成模型与生成辅助逻辑，可作为无条件图生成的核心实现参考。
  - 复用状态：blocked；类型：code_entry
- `models/graphsgpt_cond_gen/modelling_graphsgpt_cond_gen.py`
  - 能力：GraphsGPT 条件生成变体
  - 用途：实现条件图生成模型与其配置，可用于 scaffold/属性控制生成。
  - 复用状态：blocked；类型：code_entry
- `data/tokenizer.py`
  - 能力：图分词与批处理
  - 用途：将分子图输入编码并整理 batch，支撑训练与推理。
  - 复用状态：blocked；类型：tokenizer
- `moses/dataset.py`
  - 能力：MOSES 数据集读取
  - 用途：读取和封装 MOSES 数据，用于生成评测或相关实验。
  - 复用状态：blocked；类型：code_entry
- `utils/representation/graphsgpt_finetune_model.py`
  - 能力：Representation 微调接口
  - 用途：封装 GraphsGPT 表示学习/微调模型接口。
  - 复用状态：blocked；类型：code_entry
- `configs/property_info.json`
  - 能力：条件属性配置
  - 用途：定义条件生成所需的 property 信息与约束字段。
  - 复用状态：blocked；类型：config
- `moses/NP_Score/publicnp.model.gz`
  - 能力：NP_Score 评分资源
  - 用途：MOSES 评测中的 natural product score 资源。
  - 复用状态：blocked；类型：unknown
- `moses/SA_Score/fpscores.pkl.gz`
  - 能力：SA_Score 评分资源
  - 用途：MOSES 评测中的 synthetic accessibility score 资源。
  - 复用状态：blocked；类型：unknown

### training

- `entrypoints/representation/finetune.py`
  - 能力：Representation 微调入口
  - 用途：启动 GraphsGPT 表示学习/下游微调流程。
  - 复用状态：blocked；类型：code_entry
- `scripts/representation/finetune.sh`
  - 能力：Representation 微调启动脚本
  - 用途：封装微调命令行参数并调用训练入口。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态分析，未执行代码、未安装依赖、未运行测试。
- 仓库无 tracked checkpoint，无法静态证明推理权重可用。
- 存在 5MiB 以上大文件可能为 promisor-only，且未初始化 submodules。
- 路径存在不等于可复现，不能据此推断训练或评测已经成功。

## 仍未知

- `moses/data/*.csv.gz`、`data/zinc250k/*.txt` 的上游来源与许可证未在静态清单中得到证实。
- `publicnp.model.gz`、`fpscores.pkl.gz` 等评分资源虽明显像第三方 vendored 资产，但其具体许可未核验。
- `test_stats.npz` 与 `test_scaffolds_stats.npz` 的生成来源只见静态路径，无法确认是否为项目派生缓存。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
