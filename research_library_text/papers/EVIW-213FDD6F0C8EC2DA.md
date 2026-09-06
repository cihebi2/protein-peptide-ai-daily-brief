# One step forward towards deep-learning protein complex structure prediction by precise multiple sequence alignment construction

- **论文 ID：** `EVIW-213FDD6F0C8EC2DA`
- **期刊 / 来源：** Clin Transl Med
- **发表时间：** 2024 Jun 16
- **DOI：** [10.1002/ctm2.1689](https://doi.org/10.1002/ctm2.1689)
- **范围标签：** `Pi 已解析` / `背景资料` / `论文声明资源` / `结构预测`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作为 commentary，文章总结 DMFold 通过精确构建多链 MSA、在 CASP15 盲测中取得领先，并通过在线 server 扩展到结构与功能注释的进展。

## 创新边界

`本文主要是对既有 DMFold 工作的解读与推广，不是新的算法发明或新的实验研究。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在缺乏大规模 PPI 序列数据库的情况下，如何通过更精确的 multiple sequence alignment 构建可靠的跨链 co-evolution 信息，从而提升 protein complex structure prediction。

## 方法

- commentary。

## 数据与基准

- 被评述研究。

## 比较基线

- 不适用。

## 结果证据

- 无原创结果。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 观点性。

## 仍未知

- 文中未披露训练细节、推理成本和资源消耗。
- 未给出源码仓库或可执行代码链接，只提到在线 server。
- 性能主要来自 CASP15 盲测转述，独立复现范围不明。

## Pi 结构化证据摘录

- **baseline：** 主要基线包括标准版 AlphaFold2 与 March 2022 version 的 AlphaFold2 server（NBIS-AF2-multimer）。
  - 证据：[doi:10.1002/ctm2.1689, p.3]；[doi:10.1002/ctm2.1689, p.4]
- **baseline：** 文中还将 DMFold 与 CASP15 official assessors 的整体排名直接对照，用于突出其第一名表现。
  - 证据：[doi:10.1002/ctm2.1689, p.3]；[doi:10.1002/ctm2.1689, p.4]
- **baseline：** 在 nanobody-antigen 例子中，DMFold 也与 AlphaFold2 的结构姿态预测逐一比较。
  - 证据：[doi:10.1002/ctm2.1689, p.4]
- **data：** 该工作依赖 metagenome repositories 提供的大规模序列资源来构造 monomer/PPI MSAs。
  - 证据：[doi:10.1002/ctm2.1689, p.2]；[doi:10.1002/ctm2.1689, p.4]
- **data：** CASP15 blind test 涵盖 41 个 targets、87 个 registered assembly groups，作为主要评测背景。
  - 证据：[doi:10.1002/ctm2.1689, p.3]
- **data：** 文中还展示了 six large-size complexes（>1500 residues）以及三个 nanobody-antigen targets：H1140、H1141、H1144。
  - 证据：[doi:10.1002/ctm2.1689, p.4]
- **declared_resources：** 作者声明获得 NIGMS、NIAID、NSF 和 NUS Start-up Grant 支持。
  - 证据：[doi:10.1002/ctm2.1689, p.4]
- **declared_resources：** 文中提供了在线 DMFold server：https://zhanggroup.org/DMFold/。
  - 证据：[doi:10.1002/ctm2.1689, p.4]
- **limitations：** 本文没有单列失败案例、算力/时间开销或独立复现分析，因此对方法边界的判断仍需回看 DMFold 原始论文和 CASP 报告。
  - 证据：[doi:10.1002/ctm2.1689, p.4]；[doi:10.1002/ctm2.1689, p.5]
- **limitations：** 文章强调结构预测对 drug discovery 的前景，但没有给出新的下游药物设计实验验证。
  - 证据：[doi:10.1002/ctm2.1689, p.1]；[doi:10.1002/ctm2.1689, p.4]
- **method：** DMFold 先为每条链用 iterative dynamic programming 和 HMM searches 在多个 metagenome sequence libraries 中构建 monomer MSAs，再把同种属同源序列配对以推断跨链 co-evolution。
  - 证据：[doi:10.1002/ctm2.1689, p.2]；[doi:10.1002/ctm2.1689, p.4]
- **method：** 在序列配对前，DMFold 引入 AI-driven MSA scoring strategy 对候选 MSA 排序，以尽量保证 orthologous sequence alignment 的质量。
  - 证据：[doi:10.1002/ctm2.1689, p.4]
- **method：** 拼接后的 PPI MSAs 被送入 end-to-end deep-learning neural network 生成复合物结构模型，在线 server 还输出 top10 experimental structures 和 GO/EC/ligand 注释。
  - 证据：[doi:10.1002/ctm2.1689, p.4]
- **results：** DMFold 在 CASP15 的 overall Z-score 为 35.4，明显高于第二名 29.9 和 AlphaFold2 的 12.3。
  - 证据：[doi:10.1002/ctm2.1689, p.4]
- **results：** 在六个大型复合物目标上，DMFold 的 TM-score 分别达到 .98、.91、.94、.93、.93 和 .85。
  - 证据：[doi:10.1002/ctm2.1689, p.4]
- **results：** 在三个 nanobody-antigen 目标上，AlphaFold2 的 TM-score 都低于 .7，而 DMFold 达到 .92、.95 和 .99。
  - 证据：[doi:10.1002/ctm2.1689, p.4]

## 页码证据

- [doi:10.1002/ctm2.1689, p.1]
- [doi:10.1002/ctm2.1689, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
