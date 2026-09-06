# Benchmarking antigen-aware inverse folding methods for antibody design

- **论文 ID：** `EVIW-A1AD09D7AFFD0BA7`
- **期刊 / 来源：** bioRxiv preprint（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1101/2025.08.05.668698](https://doi.org/10.1101/2025.08.05.668698)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白质设计` / `结构预测` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者声称建立了一个面向真实抗体发现场景的基准，系统比较 ProteinMPNN、ESM-IF 及其抗体特化版本在多个数据集上的富集、相关性和采样表现，并据此评估抗原上下文的实际增益。

## 创新边界

`创新主要在基准评测与任务设置，不是新生成模型；结论边界是这些方法更像可折叠性/自然性排序器，而不是强抗原条件的设计器。`。这不是全球首创性检索或独立复现结论。

## 研究问题

比较抗原感知逆折叠方法在抗体设计中的真实排序与富集能力，并检验抗原信息是否真的提升对高亲和力 binder 的识别。

## 方法

- 固定Ab-Ag structures、CDR sequence recovery/designability评估。

## 数据与基准

- SAbDab/complex test sets。

## 比较基线

- ProteinMPNN/ESM-IF/antibody-specific models。

## 结果证据

- 论文报告模型差异；为计算benchmark。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 预印本、sequence recovery不等于affinity、结构泄漏。

## 仍未知

- 补充材料中的具体图表与统计检验细节未在正文外独立复核。
- 是否存在未公开代码或内部实现细节，冻结稿件未说明。
- 模型训练数据是否已完整覆盖 HER2/Trastuzumab 场景，正文只能做推测。

## Pi 结构化证据摘录

- **baseline：** 相较于 AbLang2、ESM2_650M、SaProt 和 PWM 等 baseline，抗体特化逆折叠在多数组合任务上更稳，但 PWM 在最简单的 HER2 high vs low 任务上意外很强。
  - 证据：[doi:10.1101/2025.08.05.668698, p.4]；[doi:10.1101/2025.08.05.668698, p.6]
- **baseline：** 作者把 HER2/Trastuzumab 结果定位为 sanity check，而不是严格 zero-shot，因为这些对象很可能已被模型在训练中见过。
  - 证据：[doi:10.1101/2025.08.05.668698, p.3]
- **baseline：** 在 AbDesign DB 中，native structure 可视为更强的参照上限，因为模型在原生结构上通常优于 modeled structure，但抗原加入带来的提升非常有限。
  - 证据：[doi:10.1101/2025.08.05.668698, p.7]；[doi:10.1101/2025.08.05.668698, p.9]
- **data：** AbDesign DB 由 7 个抗原构成，每个抗原对应两种抗体；作者以 CDR-H3 与抗原重原子距离 4.5 Å 作为接触定义来选取突变位点。
  - 证据：[doi:10.1101/2025.08.05.668698, p.2]
- **data：** HER2-aff-large 原始规模超过 50 万条序列，三类样本数分别为 178,160、196,392 和 171,732；去除重叠后得到 524,346 条序列。
  - 证据：[doi:10.1101/2025.08.05.668698, p.2]
- **data：** BI-PD1 数据集包含 59 条 binder 重/轻链序列，并通过随机替换 CDR3 的方式构造了 59 条 non-binder 序列。
  - 证据：[doi:10.1101/2025.08.05.668698, p.2]；[doi:10.1101/2025.08.05.668698, p.7]
- **data：** AbDesign DB 的突变体由 ABodyBuilder2 建模并用 OpenMM relaxation，野生型结构也走了同样的优化流程。
  - 证据：[doi:10.1101/2025.08.05.668698, p.2]
- **data：** 作者公开说明数据可用性仅覆盖 AbDesign DB 和 Trastuzumab HER2 Large，BI-PD1 属于内部 proprietary 数据。
  - 证据：[doi:10.1101/2025.08.05.668698, p.13]
- **declared_resources：** 使用了 ABodyBuilder2 和 OpenMM 生成/优化结构，并把这些结构作为逆折叠条件输入。
  - 证据：[doi:10.1101/2025.08.05.668698, p.2]
- **declared_resources：** 使用了 AbDesign DB、Trastuzumab HER2 Large 和 BI-PD1 作为评测资源，其中 BI-PD1 为内部数据。
  - 证据：[doi:10.1101/2025.08.05.668698, p.2]；[doi:10.1101/2025.08.05.668698, p.13]
- **declared_resources：** 数据可用性部分列出了 AbDesign DB 和 Trastuzumab HER2 Large 的公开链接，但未给出可复用代码仓库。
  - 证据：[doi:10.1101/2025.08.05.668698, p.13]
- **limitations：** 作者自己也指出抗原上下文对当前 inverse folding 预测的影响很弱，模型更偏向学到 foldability 和内部稳定性，而不是界面特异性。
  - 证据：[doi:10.1101/2025.08.05.668698, p.9]；[doi:10.1101/2025.08.05.668698, p.10]；[doi:10.1101/2025.08.05.668698, p.12]
- **limitations：** PD1 场景里缺少可靠的 antibody-antigen docking，导致只能依赖 modeled structure，限制了抗原作用的判断。
  - 证据：[doi:10.1101/2025.08.05.668698, p.7]
- **limitations：** 低温采样会严重塌缩到少数重复序列，限制模型探索更大序列空间的能力。
  - 证据：[doi:10.1101/2025.08.05.668698, p.11]
- **limitations：** oracle 对随机序列的高误判率表明，回顾性富集结果未必等价于真实实验可转移性。
  - 证据：[doi:10.1101/2025.08.05.668698, p.11]
- **limitations：** 稿件没有报告新的湿实验验证，核心证据来自既有公开/内部数据集上的回顾性 benchmark。
  - 证据：[doi:10.1101/2025.08.05.668698, p.2]；[doi:10.1101/2025.08.05.668698, p.13]
- **method：** 作者比较了四个逆折叠模型：ESM-IF、ProteinMPNN、AntiFold、AbMPNN，并加入 AbLang2、ESM2_650M、SaProt 和 PWM 作为对照。
  - 证据：[doi:10.1101/2025.08.05.668698, p.2]；[doi:10.1101/2025.08.05.668698, p.3]；[doi:10.1101/2025.08.05.668698, p.4]；[doi:10.1101/2025.08.05.668698, p.6]
- **method：** 评测使用三类数据：HER2-aff-large、BI-PD1、NaturalAntibody AbDesign DB；其中 AbDesign DB 含 14 个抗体-抗原复合物、7 个抗原和约 700 个 CDR-H3 点突变。
  - 证据：[doi:10.1101/2025.08.05.668698, p.2]；[doi:10.1101/2025.08.05.668698, p.7]
- **method：** HER2 基准采用 88-well 增量抽样，分别考察 high vs low 与 high vs (medium 作为 negative) 两种富集任务，并在 native structure 与 ABodyBuilder2 modeled structure 两种条件下比较。
  - 证据：[doi:10.1101/2025.08.05.668698, p.4]；[doi:10.1101/2025.08.05.668698, p.5]；[doi:10.1101/2025.08.05.668698, p.6]
- **method：** AbDesign DB 部分同时做了 perplexity 与 ELISA ratio 的相关性分析，以及把 ELISA ratio > 1.0 视为 binding 的二分类成功率分析。
  - 证据：[doi:10.1101/2025.08.05.668698, p.7]；[doi:10.1101/2025.08.05.668698, p.10]
- **method：** 采样实验在 HER2 上训练 CNN oracle，对不同 temperature 采样的序列做 binder/non-binder 判别，并统计 unique sequence 数量与序列 identity。
  - 证据：[doi:10.1101/2025.08.05.668698, p.10]；[doi:10.1101/2025.08.05.668698, p.11]
- **results：** 在 HER2 上，AntiFold 在 native structure 条件下的 high vs low 富集最强，N=88 时达 95.5%，N=880 时仍有 89.8%。
  - 证据：[doi:10.1101/2025.08.05.668698, p.5]；[doi:10.1101/2025.08.05.668698, p.6]
- **results：** AbMPNN 在 modeled structure 条件下表现最好，high vs low 在 N=88 时为 85.2%，到 N=880 时维持 85.3%。
  - 证据：[doi:10.1101/2025.08.05.668698, p.5]
- **results：** PWM 这个简单 sequence-only baseline 在 HER2 high vs low 上也达到 95.5%，但当 medium 被并入 non-binder 后降到 64.8%。
  - 证据：[doi:10.1101/2025.08.05.668698, p.6]
- **results：** 在 BI-PD1 上，AntiFold 在 top 12 达到 75% 富集；AbMPNN 也能到 75%，但样本扩大后下降更快，ProteinMPNN 最弱。
  - 证据：[doi:10.1101/2025.08.05.668698, p.7]；[doi:10.1101/2025.08.05.668698, p.8]
- **results：** 在 AbDesign DB 上，AntiFold 的相关性最高，modelled single-chain pearson 为 0.40、multi-chain 为 0.38；ESM-IF 最低。
  - 证据：[doi:10.1101/2025.08.05.668698, p.10]
- **results：** 二分类成功率里，native structure 明显优于 modeled structure；例如 ESM-IF 从 3/4 与 3/4 级别提升到 11/9，AntiFold 从 5/5 提升到 10/10。
  - 证据：[doi:10.1101/2025.08.05.668698, p.10]
- **results：** 采样统计显示低温会产生大量重复序列，AntiFold 在 temperature 0.1 时只有 36 个 unique sequences，而 AbMPNN、ESM-IF、ProteinMPNN 分别为 114、336、194。
  - 证据：[doi:10.1101/2025.08.05.668698, p.11]
- **results：** oracle sanity check 中，随机 CDRH3 仍有 5.6%、38.0% 和 10.6% 被判为 binder，说明分类器可能学到的是一般 antibody-like 特征。
  - 证据：[doi:10.1101/2025.08.05.668698, p.11]

## 页码证据

- [doi:10.1101/2025.08.05.668698, p.1]
- [doi:10.1101/2025.08.05.668698, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
