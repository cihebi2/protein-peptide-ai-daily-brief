# HLA I immunopeptidome of synthetic long peptide pulsed human dendritic cells for therapeutic vaccine design

- **论文 ID：** `EVIW-0EA8CC81C58675DC`
- **期刊 / 来源：** NPJ Vaccines
- **发表时间：** 2025 Jan 18
- **DOI：** [10.1038/s41541-025-01069-1](https://doi.org/10.1038/s41541-025-01069-1)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者构建并解析了 6 位供者 moDC 的 HLA-I immunopeptidome 数据集，识别出 33 条 SLP-derived peptides、14 条作者标记为 novel 的 HBV HLA peptides，并说明两种 adjuvant 对 SLP cross-presentation 的支持没有显著差异。

## 创新边界

`创新主要在实验性 immunopeptidomics 评估与候选筛选支持，不是新算法、也不是新候选分子的生成或优化。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何直接评估 HBV synthetic long peptide 在 human dendritic cells 上的 cross-presentation，并比较 TLR1/2 与 TLR3 adjuvant 对 HLA-I immunopeptidome 的影响，以辅助 therapeutic vaccine design。

## 方法

- 人源moDC脉冲SLP和adjuvant，HLA-I免疫沉淀/质谱鉴定并人工检查PSM，比较allele/adjuvant呈递。

## 数据与基准

- 12条HBV SLP、多供者DC与27条中/高质量SLP相关谱图。

## 比较基线

- in-silico HLA预测与T细胞assay作为现有路径，不是统一算法基线。

## 结果证据

- 论文报告直接检测cross-presentation和TRIF相关signature；这是湿实验数据资源，不是计算模型。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 供者/SLP数量小、HLA多样性和质谱覆盖有限，不能外推所有疫苗。

## 仍未知

- 14 条作者标记为 novel 的 HBV HLA peptides 是否在外部文献中真正未曾报道，未做独立检索核验。
- primary DC 试验样本量和质量都有限，不能证明该流程已稳健适用于体内 patient-derived DC。
- adjuvant 与 antigen 的共定位、以及不同 cDC subset 中的 cross-presentation 差异，仍未被该研究排除。

## Pi 结构化证据摘录

- **baseline：** 作者将既有 HBV SLP 设计流程概括为主要依赖 in silico prediction 和 labor-intensive in vitro T cell assays，因此难以直接回答 cross-presentation。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.2]；[doi:10.1038/s41541-025-01069-1, p.8]
- **baseline：** 文中用 HBcAg18-27 作为 HLA-A2 binding positive control，并把 HLYSHPIIL 视为已知对照 epitope，用于比较新发现的候选。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.7]；[doi:10.1038/s41541-025-01069-1, p.8]
- **data：** 共有 6 位供者纳入，且全部匹配 HLA-A*02:01 与 HLA-A*11:01；B/C 位点分别为不同组合，因此样本在 HLA-B/C 维度上存在明显变异。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.3]；[doi:10.1038/s41541-025-01069-1, p.9]
- **data：** DDA 共得到 34,315 个 unique peptides，样本层面约 2,945–12,622 个；其中 8–11-mers 占 93.2%±1.3%，符合典型 HLA peptide 长度分布。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.3]
- **data：** DIA 单次运行又获得 22,070 个 peptides；主分析中共识别 33 条 unique SLP-derived peptides，来自 10/12 条 SLP，另在 primary DC 试验中检出 2 条 SLP-derived peptides。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.4]；[doi:10.1038/s41541-025-01069-1, p.5]
- **declared_resources：** 实验材料包括 12 条 HBV SLP、Amplivant®、PolyI:C、W6/32 pan-HLA-I beads，以及 Orbitrap Eclipse 和 PEAKS Studio 11 等分析工具。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.2]；[doi:10.1038/s41541-025-01069-1, p.9]；[doi:10.1038/s41541-025-01069-1, p.10]
- **declared_resources：** HLA mapping 使用 NetMHCpan4.1，HLA typing 使用 HLA-TAPAS，统计与可视化则依赖 R、Prism、FlowJo 和 Illustrator。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.10]；[doi:10.1038/s41541-025-01069-1, p.11]
- **declared_resources：** 质谱数据已存入 PRIDE PXD051490，代码在 GitHub 公开，但供者 SNP 数据因 consent 限制未公开。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.10]
- **limitations：** primary DC 的 immunopeptidome 尚未达到可比质量，因此主要结论仍来自 moDC，外推到体内 cDC 需要谨慎。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.4]；[doi:10.1038/s41541-025-01069-1, p.8]；[doi:10.1038/s41541-025-01069-1, p.9]
- **limitations：** 作者明确承认，LC-MS/MS 可能漏检部分真实 HLA peptides，且峰强不一定等于生物学丰度。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.9]
- **limitations：** 作者也指出，不同 cDC subset、以及 antigen 与 TLR ligand 在细胞内共定位的方式，仍可能改变 in vivo cross-presentation。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.8]
- **method：** 作者用来自 6 位 HLA-A*02:01/HLA-A*11:01 匹配供者的 moDC，脉冲 12 条 HBV SLP，并分别用 Amplivant® 或 PolyI:C 处理 22 h。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.2]；[doi:10.1038/s41541-025-01069-1, p.9]
- **method：** 随后通过 W6/32 介导的 pan-HLA-I immunoprecipitation，结合 DDA 与 DIA LC-MS/MS 解析 HLA-I peptide repertoire，并用 PEAKS 与 NetMHCpan4.1 做鉴定和 HLA mapping。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.9]；[doi:10.1038/s41541-025-01069-1, p.10]
- **method：** 作者还做了 primary DC 试验、T2 HLA-A2 stabilization assay、HLA typing 和 STRING/GO 分析，用于验证和解释观察到的呈递模式。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.4]；[doi:10.1038/s41541-025-01069-1, p.7]；[doi:10.1038/s41541-025-01069-1, p.9]；[doi:10.1038/s41541-025-01069-1, p.10]
- **results：** TLR1/2 与 TLR3 处理并未显著改变总 peptide yield 或 SLP-derived peptide 数量，说明两类 adjuvant 对 SLP cross-presentation 的支持相近。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.3]；[doi:10.1038/s41541-025-01069-1, p.5]；[doi:10.1038/s41541-025-01069-1, p.8]
- **results：** TLR3 条件下出现更明显的 interferon/response to virus 相关 source protein network，说明 immunopeptidome 可以读出 TRIF 驱动的成熟特征。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.4]；[doi:10.1038/s41541-025-01069-1, p.8]
- **results：** HLA-I peptide 组成主要由 B alleles 主导，而不是 A/C；共享 B alleles 的供者共享更多 peptides，显示 HLA-B 对该 immunopeptidome 的影响最强。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.3]；[doi:10.1038/s41541-025-01069-1, p.8]
- **results：** SLP8 的 HLYSHPIIL 与 HLYSHPIILG 都能被重复检出，后者虽被算法判为 non-binder，却在 T2 assay 中稳定结合 HLA-A2。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.5]；[doi:10.1038/s41541-025-01069-1, p.6]；[doi:10.1038/s41541-025-01069-1, p.7]；[doi:10.1038/s41541-025-01069-1, p.8]
- **results：** 不同 SLP 的可呈递性差异很大：SLP6 产生最多 distinct peptides，而 SLP1 和 SLP7 未检出，提示序列本身对 cross-presentation 影响显著。
  - 证据：[doi:10.1038/s41541-025-01069-1, p.7]；[doi:10.1038/s41541-025-01069-1, p.9]

## 页码证据

- [doi:10.1038/s41541-025-01069-1, p.1]
- [doi:10.1038/s41541-025-01069-1, p.2]
- [doi:10.1038/s41541-025-01069-1, p.3]
- [doi:10.1038/s41541-025-01069-1, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
