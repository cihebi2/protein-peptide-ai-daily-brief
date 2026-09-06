# Integrating Transformers and Many-Objective Optimization for Cancer Drug Design

- **论文 ID：** `EVIW-794300AEDE5FAFED`
- **期刊 / 来源：** Research Square preprint（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.21203/rs.3.rs-4229436/v1](https://doi.org/10.21203/rs.3.rs-4229436/v1)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

论文提出一个把 latent Transformer 分子生成、ADMET 预测、分子对接与 many-objective metaheuristics 结合的完整药物设计框架，并在 LPA1 靶点上比较 ReLSO/FragNet 与六种优化算法，报告 ReLSO 在生成任务上更强、MOEA/DD 在多目标搜索上更有竞争力。

## 创新边界

`主要新意是系统级集成与经验比较，不是已被独立验证的全球首创，也不等于证明了新算法或新分子的普适新颖性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何在癌症药物设计中同时生成新分子并优化多项相互冲突的性质，使候选分子兼顾结合亲和力、ADMET、可合成性与药物相似性。

## 方法

- SMILES transformer与Pareto/evolutionary optimization。

## 数据与基准

- cancer target/compound datasets。

## 比较基线

- single/multiobjective generators。

## 结果证据

- 论文报告multiobjective candidates；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 预印本、reward bias、无实验。

## 仍未知

- GitHub 仓库是否仍可访问，以及代码是否与页内描述完全一致
- 是否存在未公开的模型权重、超参数细节或额外实验日志
- 该框架在其他靶点、其他化学空间与湿实验验证中的泛化能力

## Pi 结构化证据摘录

- **baseline：** 分子生成基线主要是 base ReLSO、contrastive ReLSO 和 FragNet，作者用它们比较重建与 latent space 组织能力。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.7]；[doi:10.21203/rs.3.rs-4229436/v1, p.12]；[doi:10.21203/rs.3.rs-4229436/v1, p.13]
- **baseline：** 优化基线包括 GrEA、HypE、KnEA、MOEA/DD、A-NSGA-III 和 NMPSO，初始种群则由训练数据随机采样得到。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.8]；[doi:10.21203/rs.3.rs-4229436/v1, p.9]
- **baseline：** 作者还把 initial population 和 molecular generation dataset 作为 novelty、uniqueness 与 Wasserstein 分布比较的参考基线。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.15]；[doi:10.21203/rs.3.rs-4229436/v1, p.17]；[doi:10.21203/rs.3.rs-4229436/v1, p.18]
- **data：** 分子生成模型与 MTL-BERT 预训练共享约 400 万个 unique canonicalized molecules，来源于 MOSES、ChEMBL 和 ZINC，并在长度与 augmentation 条件下做预处理。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.10]；[doi:10.21203/rs.3.rs-4229436/v1, p.11]；[doi:10.21203/rs.3.rs-4229436/v1, p.12]；[doi:10.21203/rs.3.rs-4229436/v1, p.22]
- **data：** 生成模型训练数据按 70%/10%/20% 划分为 train/validation/test，并仅保留长度不超过 198 且在 10 次尝试中至少有两种 unique augmentation 的分子。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.11]
- **data：** LPA1 结构来自 AlphaFold Protein Structure Database，作者将其作为对接靶点，并在论文数据可得性中公开了实现仓库。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.10]；[doi:10.21203/rs.3.rs-4229436/v1, p.22]
- **declared_resources：** 作者声明数据来自 MOSES、ChEMBL、ZINC-250k，并通过 TDC 获取；LPA1 结构来自 AlphaFold Protein Structure Database。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.22]
- **declared_resources：** 作者公开了实现仓库 Pixelatory/ManyObjectiveDrugDesign，便于复现其计算流程与实验设置。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.22]
- **declared_resources：** 论文还声明获得了 AI4D-108 及两项 NSERC Discovery Grant 的部分资助。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.22]
- **limitations：** 作者明确指出 many-objective 搜索计算代价很高，增加 function evaluations 可能改善 Pareto front，但这留待未来工作。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.17]；[doi:10.21203/rs.3.rs-4229436/v1, p.20]
- **limitations：** 文中说明 SMILES 在下游优化中曾出现较差的 molecular validity，因此生成阶段改用 SELFIES，这也限制了方法对表示选择的依赖。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.11]；[doi:10.21203/rs.3.rs-4229436/v1, p.5]
- **limitations：** 作者建议未来比较更多 recent molecular generation models，并分析 drug design objectives 与 metaheuristics 的可扩展性。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.20]
- **method：** 分子生成部分使用 SELFIES/SMILES 表示，并比较 FragNet 与经改造的 ReLSO，通过对比学习和 latent space 正则化学习可用于后续优化的表示。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.5]；[doi:10.21203/rs.3.rs-4229436/v1, p.7]；[doi:10.21203/rs.3.rs-4229436/v1, p.11]；[doi:10.21203/rs.3.rs-4229436/v1, p.12]
- **method：** 作者把编码器输出映射到 latent vector，再经 decoder 生成分子并重新编码修复位置，然后在 latent space 中运行六种 many-objective metaheuristics 做搜索。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.8]；[doi:10.21203/rs.3.rs-4229436/v1, p.9]
- **method：** 优化目标包括 binding affinity、SAS、bioavailability、solubility、LD50 和 ClinTox；其中对接用 QuickVina2-GPU，ADMET 由 MTL-BERT 预测。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.10]；[doi:10.21203/rs.3.rs-4229436/v1, p.12]
- **method：** 实验平台使用 PlatEMO，并设置 population size 2000、function evaluations 25000，以及基于验证损失的 early stopping 规则。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.8]；[doi:10.21203/rs.3.rs-4229436/v1, p.11]；[doi:10.21203/rs.3.rs-4229436/v1, p.12]
- **results：** 在测试集上，ReLSO 的 reconstruction loss 与 reconstruction accuracy 都优于 FragNet，说明其更适合该任务的分子重建。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.12]；[doi:10.21203/rs.3.rs-4229436/v1, p.13]
- **results：** 在 many-objective 搜索中，MOEA/DD 的 GD/IGD 表现最差，但它仍能在若干单项指标上给出具有竞争力的最优或接近最优结果。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.17]；[doi:10.21203/rs.3.rs-4229436/v1, p.18]；[doi:10.21203/rs.3.rs-4229436/v1, p.19]
- **results：** NMPSO 与 A-NSGA-III 在多个单项目标上持续给出较优解，且过滤后共有 1718 个分子保留，MOEA/DD 占比最高。
  - 证据：[doi:10.21203/rs.3.rs-4229436/v1, p.18]；[doi:10.21203/rs.3.rs-4229436/v1, p.19]

## 页码证据

- [doi:10.21203/rs.3.rs-4229436/v1, p.1]
- [doi:10.21203/rs.3.rs-4229436/v1, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
