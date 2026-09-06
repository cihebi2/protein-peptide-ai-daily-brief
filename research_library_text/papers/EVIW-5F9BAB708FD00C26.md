# Benchmarking antibody clustering methods using sequence, structural, and machine learning similarity measures for antibody discovery applications

- **论文 ID：** `EVIW-5F9BAB708FD00C26`
- **期刊 / 来源：** Front Mol Biosci
- **发表时间：** 2024 Mar 28
- **DOI：** [10.3389/fmolb.2024.1352508](https://doi.org/10.3389/fmolb.2024.1352508)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称首次对五类抗体聚类/相似性方法做 head-to-head benchmark，并给出 CLAP 在线工具，帮助用户在不同相似性维度上比较、可视化并进行二步筛选。

## 创新边界

`创新主要在统一基准评测与交互式比较工具，不在新的抗体生成、优化或设计算法本身。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在抗体发现流程中，如何在统一框架下比较序列、clonotype、paratope、结构与 embedding 五类相似性/聚类方法，并判断它们在 binder detection 与 epitope mapping 中是否能提供更有用的候选分组与多样性选择。

## 方法

- 对多种相似度和聚类方案统一调参，在binder detection与epitope mapping上比较。

## 数据与基准

- 两个任务的抗体数据集及盲测/验证集。

## 比较基线

- 序列、结构、clonotype、paratope和ML embedding聚类。

## 结果证据

- binder detection没有单一方法稳定胜出；epitope mapping中clonotype、paratope和embedding聚类表现最好。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 表现强依赖数据集和参数，验证集调参不一定迁移到盲测集。

## 仍未知

- CLAP 网页工具的后端实现与源码公开状态未被页内证据证实。
- 补充材料中的完整参数表、图表和数据可重现性未在正文页内完全展开。
- 文中未提供独立代码仓库地址，因此复用边界不明确。

## Pi 结构化证据摘录

- **baseline：** 作者将传统 sequence clustering 与 clonotyping 作为主要对照基线，用来评估更复杂的 paratope、structure 和 embedding 方法是否带来增益。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.4]；[doi:10.3389/fmolb.2024.1352508, p.7]；[doi:10.3389/fmolb.2024.1352508, p.8]
- **baseline：** Pure 队列里还显式报告了 random baseline，且其 F1 在两个目标上差异很大，提示数据分布会强烈影响表观性能。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.11]
- **data：** 基准数据包括 PTx、OVA、Pure_Target1、Pure_Target2 和 Cao：分别用于 binder/non-binder 分类、盲测，以及 12 个 epitope 组的 binning。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.3]；[doi:10.3389/fmolb.2024.1352508, p.11]
- **data：** PTx 与 OVA 均为 paired heavy-light 数据集，Pure 数据来自 Pure Biologics 的 discovery program，Cao 数据来自 SARS-CoV-2 相关抗体并带有 epitope 标签。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.3]
- **data：** 作者还说明 PTx 由免疫小鼠样本与 SPR/HTRF 标注构成，OVA 来自 scBCR-seq 与后续实验验证，Pure 盲测序列来自 phage library 与 PacBio，Cao 结合了高通量测序和 DMS。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.3]
- **declared_resources：** 作者提供了 CLAP 在线应用，可输入 paired heavy/light FASTA，比较 sequence、embedding、structure 和 paratope 聚类，并支持二步聚类筛选。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.1]；[doi:10.3389/fmolb.2024.1352508, p.12]
- **declared_resources：** 论文正文没有给出独立代码仓库或可下载模型权重链接，只明确提到网页工具与补充材料入口。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.13]
- **limitations：** 论文反复指出最优阈值与参数高度 dataset-specific，缺少可跨数据集复用的统一配置。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.7]；[doi:10.3389/fmolb.2024.1352508, p.8]
- **limitations：** blind test 表明 clustering 不是通用解法，结果完全依赖底层数据与参数；而 clonotyping 在样本过小时甚至无法应用。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.10]；[doi:10.3389/fmolb.2024.1352508, p.11]
- **limitations：** 结构比较依赖预测模型，且 ABodyBuilder2 在 OVA 部分结构上失败，说明结构基准受建模误差影响。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.7]
- **method：** 论文统一评测了 sequence、clonotype、paratope、structure 和 embedding 五类聚类方案，并系统扫描长度分层、聚类区域、阈值与模型选择等参数。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.4]；[doi:10.3389/fmolb.2024.1352508, p.5]；[doi:10.3389/fmolb.2024.1352508, p.6]
- **method：** binder detection 采用 probe-mining：用一个已知 binder 作为 probe，把与其同簇者视为 binder，再计算 precision、recall 与 F1。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.5]；[doi:10.3389/fmolb.2024.1352508, p.6]
- **method：** epitope binning 用 multiple occupancy consistent cluster members fraction (MOCM) 衡量同簇抗体是否只来自单一 epitope。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.6]；[doi:10.3389/fmolb.2024.1352508, p.11]
- **method：** 结构聚类比较了 NanoNet 与 ABodyBuilder2，并在聚类阶段对比 mTM-align 与 SPACE；embedding 聚类则使用 heavy 与 paired transformers 的最后一层表示。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.4]；[doi:10.3389/fmolb.2024.1352508, p.5]；[doi:10.3389/fmolb.2024.1352508, p.7]
- **results：** 在 PTx 与 OVA 上，没有任何单一方法稳定压倒其他方法；最佳 F1 明显依赖数据集，PTx 约低于 0.8，而 OVA 可超过 0.9。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.7]；[doi:10.3389/fmolb.2024.1352508, p.8]
- **results：** sequence、clonotype、paratope、structure 与 embedding 的簇划分大多高度重叠，Jaccard 多在 85%–90% 左右，但组合不同方法可以找回更多 binder。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.8]；[doi:10.3389/fmolb.2024.1352508, p.9]
- **results：** 在 Pure_Target1 上，没有方法优于随机基线；Pure_Target2 上基线本身很高，但跨数据集沿用的参数并不稳定，说明盲测场景下泛化有限。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.10]；[doi:10.3389/fmolb.2024.1352508, p.11]
- **results：** 在 Cao epitope binning 上，clonotype 与 paratope 整体优于 sequence、structure 等方法，embedding 居中，structure 相对一般。
  - 证据：[doi:10.3389/fmolb.2024.1352508, p.11]；[doi:10.3389/fmolb.2024.1352508, p.12]

## 页码证据

- [doi:10.3389/fmolb.2024.1352508, p.10]
- [doi:10.3389/fmolb.2024.1352508, p.12]
- [doi:10.3389/fmolb.2024.1352508, p.1]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
