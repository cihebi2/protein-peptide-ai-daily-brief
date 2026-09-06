# 3 = 1 + 2: how the divide conquered de novo protein structure prediction and what is next?

- **论文 ID：** `EVIW-CE1BFEB1B4EFF5F3`
- **期刊 / 来源：** Natl Sci Rev
- **发表时间：** 2023 Oct 3
- **DOI：** [10.1093/nsr/nwad259](https://doi.org/10.1093/nsr/nwad259)
- **范围标签：** `Pi 已解析` / `背景资料` / `论文声明资源` / `结构预测`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者主张，AlphaFold2 的成功并非突然出现，而是建立在先前 1D 与 2D 预测进展之上；他们用 “3 = 1 + 2” 的框架重述这一演进，并指出真正未解决的仍是单序列到真实结构、动力学与变体效应。

## 创新边界

`这是综述/观点文章，不是新算法或新实验。`。这不是全球首创性检索或独立复现结论。

## 研究问题

回顾蛋白质结构预测如何从模板法、片段法与能量驱动方法，逐步走向把 3D 问题拆成 1D 背骨结构和 2D 距离图的分解式建模，并讨论 AlphaFold 之后还剩下什么问题。

## 方法

- perspective。

## 数据与基准

- 被引研究。

## 比较基线

- 不适用。

## 结果证据

- 无原创结果。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 观点性。

## 仍未知

- 补充材料中的具体方法清单和对照细节未在主文逐项展开。
- 文中对未来方向的判断属于观点性推断，缺少新实验支撑。
- 是否存在更细粒度的 prior-art 比较，需结合 Supplementary material 才能完全确认。

## Pi 结构化证据摘录

- **baseline：** 作为历史基线，文章回顾 CASP 难题上的整体 GDT 在 1996 到 2016 年只从约 27 缓慢升到约 32，直到 AlphaFold 才出现显著跃迁。
  - 证据：[doi:10.1093/nsr/nwad259, p.1]；[doi:10.1093/nsr/nwad259, p.3]
- **baseline：** 作为另一条基线，单序列 secondary structure 预测仍约 74%，而基于 evolutionary profiles 的方法已接近 87% 并逼近 86%–90% 的理论上限。
  - 证据：[doi:10.1093/nsr/nwad259, p.1]；[doi:10.1093/nsr/nwad259, p.2]；[doi:10.1093/nsr/nwad259, p.4]
- **data：** 文中使用的是既有公开评测与文献结果，例如 CASP 的 GDT、Q3、contact precision 曲线，以及历史方法性能图，并没有报告新实验数据集。
  - 证据：[doi:10.1093/nsr/nwad259, p.1]；[doi:10.1093/nsr/nwad259, p.2]；[doi:10.1093/nsr/nwad259, p.3]；[doi:10.1093/nsr/nwad259, p.4]
- **data：** 作者还引用了训练与规模背景信息，如 BFD、PDB 约 170000 结构，以及单序列和同源序列相关的既有性能统计。
  - 证据：[doi:10.1093/nsr/nwad259, p.4]；[doi:10.1093/nsr/nwad259, p.1]
- **declared_resources：** 作者声明获得了 Chinese National Key Research and Development Program、Shenzhen Bay Laboratory Major Program 和 Griffith University Postgraduate Fellowship 资助。
  - 证据：[doi:10.1093/nsr/nwad259, p.5]
- **declared_resources：** 文章还声明无利益冲突，并注明提供 Supplementary data。
  - 证据：[doi:10.1093/nsr/nwad259, p.5]
- **limitations：** 作者明确认为，AlphaFold2 对富同源序列依赖很强，因此对单序列、致病变体、动力学、稳定性和 protein-ligand interactions 的预测仍然困难。
  - 证据：[doi:10.1093/nsr/nwad259, p.4]；[doi:10.1093/nsr/nwad259, p.5]
- **limitations：** 文章本身也受篇幅限制，许多方法只在 Supplementary material 中展开，因此主文对部分比较与方法细节并不完整。
  - 证据：[doi:10.1093/nsr/nwad259, p.1]；[doi:10.1093/nsr/nwad259, p.5]
- **method：** 文章采用回顾式比较框架，把蛋白质结构预测拆成 1D 背骨结构、2D 距离图与 3D 组装三层，再用历史方法谱系解释 AlphaFold 的位置。
  - 证据：[doi:10.1093/nsr/nwad259, p.1]；[doi:10.1093/nsr/nwad259, p.2]；[doi:10.1093/nsr/nwad259, p.3]；[doi:10.1093/nsr/nwad259, p.4]
- **method：** 文章以 fragment-based、fragment-free、以及 end-to-end learning 三类路线做对照，强调从显式能量函数走向可微学习和结构模块化更新。
  - 证据：[doi:10.1093/nsr/nwad259, p.3]；[doi:10.1093/nsr/nwad259, p.4]
- **results：** 作者的核心判断是，AlphaFold2 主要解决了“多同源序列映射到单一结构”的问题，但对单序列静态结构、构象变化和动力学并未真正解决。
  - 证据：[doi:10.1093/nsr/nwad259, p.4]；[doi:10.1093/nsr/nwad259, p.5]
- **results：** 文章还指出，在 CASP15 中 AI 驱动的 RNA 结构预测并未压倒传统 energy-based 方法，反而是后者表现更好。
  - 证据：[doi:10.1093/nsr/nwad259, p.5]

## 页码证据

- [doi:10.1093/nsr/nwad259, p.1]
- [doi:10.1093/nsr/nwad259, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
