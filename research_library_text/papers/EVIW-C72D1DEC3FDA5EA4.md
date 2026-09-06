# Genomic annotation for vaccine target identification and immunoinformatics-guided multi-epitope-based vaccine design against Songling virus through screening its whole genome encoded proteins

- **论文 ID：** `EVIW-C72D1DEC3FDA5EA4`
- **期刊 / 来源：** Frontiers in Immunology（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.3389/fimmu.2023.1284366](https://doi.org/10.3389/fimmu.2023.1284366)
- **范围标签：** `Pi 已解析` / `背景资料` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称通过免疫信息学流程筛选出 4 个 SGLV 候选蛋白，组装 4 个多表位疫苗构建体，并以 SGLV-V4 为最优候选，认为其兼具较高免疫原性、稳定性和潜在表达可行性。

## 创新边界

`边界在于这是纯计算候选设计，不是已验证疫苗。`。这不是全球首创性检索或独立复现结论。

## 研究问题

围绕新发现的 Songling virus 缺乏治疗与疫苗的问题，作者试图从其全基因组编码蛋白中筛选可用于多表位疫苗设计的候选靶点，并优选出最有前景的构建体。

## 方法

- 筛选antigenic proteins和B/T-cell epitopes，组合adjuvant并预测3D结构。

## 数据与基准

- SGLV基因组/蛋白序列和免疫数据库。

## 比较基线

- 不同protein/epitope/adjuvant组合。

## 结果证据

- 只报告in silico构建体和结构质量，无表达、免疫或challenge实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 计算评分不能证明跨物种免疫保护。

## 仍未知

- SGLV-V4 在真实实验中的免疫保护效力未知
- 文中未给出独立复现实验或代码仓库链接
- 表位筛选数量在摘要与结果段落中存在轻微口径不一致
- Supplementary Material 的细节未在正文页内完全展开

## Pi 结构化证据摘录

- **baseline：** 文中唯一明确的比较基线是 4 个构建体 V1–V4 之间的内部对照；在这一组内，V4 的 docking 与验证指标最好。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.8]；[doi:10.3389/fimmu.2023.1284366, p.9]
- **baseline：** 没有看到独立的实验疫苗、临床候选物或外部 benchmark 作为正式对照，作者主要是在计算流程内部做优选。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.12]；[doi:10.3389/fimmu.2023.1284366, p.14]
- **data：** 输入数据为 NCBI/ViPR 中的 SGLV proteome，共 40 个蛋白；经过去冗余与人蛋白相似性过滤后，剩下 4 个候选蛋白进入后续分析。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.5]；[doi:10.3389/fimmu.2023.1284366, p.6]
- **data：** 设计阶段形成了 4 个构建体 SGLV-V1 至 SGLV-V4；其中 V4 被用于后续 docking、MD、免疫模拟与表达优化。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.7]；[doi:10.3389/fimmu.2023.1284366, p.8]；[doi:10.3389/fimmu.2023.1284366, p.10]
- **data：** Population coverage 被报告为全球 100%，且在 east Asia、Europe 与 south east Asia 等区域覆盖率较高。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.6]
- **data：** 理化性质显示候选构建体分子量约 30–55 kDa，GRAVY 约为 -0.128 到 -0.310，理论 pI 为 8.87–10.07，aliphatic index 为 69.09–82.50，instability index 为 30.93–41.81。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.8]
- **data：** mRNA 二级结构预测给出的最低自由能分别约为 -268.90 kcal/mol 与 -283.12 kcal/mol。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.10]
- **declared_resources：** 数据与序列资源主要来自 NCBI RefSeq、ViPR 与 IEDB population coverage 工具。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.3]；[doi:10.3389/fimmu.2023.1284366, p.4]
- **declared_resources：** 分析资源包括 AllerTop、VaxiJen、ToxinPred、ABCpred、PDBsum、PSIPRED、SWISS-MODEL、ProSA-web、ERRAT、RAMPAGE、HDock、HawkDock、HADDOCK、iMODS、C-ImmSim、JCAT、SnapGene、Mfold 和 RNAfold。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.4]；[doi:10.3389/fimmu.2023.1284366, p.5]；[doi:10.3389/fimmu.2023.1284366, p.8]；[doi:10.3389/fimmu.2023.1284366, p.10]
- **limitations：** 作者明确表示还需要后续 in vitro immunological assays 来确认这些预测。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.3]；[doi:10.3389/fimmu.2023.1284366, p.12]
- **limitations：** 文中也指出需要 challenge-protection preclinical trial 来进一步验证安全性与有效性。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.12]
- **limitations：** 作者承认当前研究完全依赖 computational approaches，因此保护效果、表达可行性与体内安全性都尚未被实验确认。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.14]；[doi:10.3389/fimmu.2023.1284366, p.15]
- **method：** 作者先从 NCBI 与 ViPR 获取 SGLV 蛋白序列，用 CD-hit 去冗余，并以 BLASTp 排除与人蛋白相近的序列，再用 AllerTop、VaxiJen 和 ToxinPred 做抗原性、过敏性与毒性筛选。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.3]；[doi:10.3389/fimmu.2023.1284366, p.4]
- **method：** 随后用 IEDB 预测 MHC-I 和 MHC-II 表位，用 ABCpred 预测 B 细胞表位，并按 antigenicity、IFN-γ、toxicity 与 allergenicity 选择重叠表位。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.4]；[doi:10.3389/fimmu.2023.1284366, p.6]
- **method：** 他们使用 IEDB population coverage 评估全球覆盖率，并通过 EAAAK、AAY、GPGPG 等 linker 及不同 adjuvant 组装 4 个多表位疫苗构建体。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.4]；[doi:10.3389/fimmu.2023.1284366, p.6]；[doi:10.3389/fimmu.2023.1284366, p.7]
- **method：** 结构层面采用 PDBsum、PSIPRED、SWISS-MODEL、DeepRefiner、ProSA、ERRAT 和 RAMPAGE 进行建模与验证，随后用 HDock、HawkDock 和 HADDOCK 与 TLR3/TLR4/TLR8 对接，并用 iMODS 做 NMA/MD 分析。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.5]；[doi:10.3389/fimmu.2023.1284366, p.7]；[doi:10.3389/fimmu.2023.1284366, p.8]
- **method：** 最后通过 C-ImmSim、JCAT、SnapGene、RNAfold 和 Mfold 分析免疫反应、密码子优化、in silico cloning 与 mRNA 二级结构。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.8]；[doi:10.3389/fimmu.2023.1284366, p.10]
- **results：** V4 与 TLR4 的对接表现最好，HawkDock 报告的 binding energy 为 -66.26 kcal/mol，HADDOCK 的 Cluster 6 也被选为最优结果。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.8]
- **results：** iMODS 的 NMA/MD 结果中，SGLV-V4-TLR4 复合物的 eigenvalue 为 2.395982e-05，作者据此认为其具有较好的稳定性。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.8]；[doi:10.3389/fimmu.2023.1284366, p.9]
- **results：** C-ImmSim 预测疫苗后 IgM、IgG1+IgG2、B cell、T-cytotoxic、T-helper、macrophage、NK cell 以及 IL-2、IFN-γ 均上升，而 antigen levels 下降。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.9]；[doi:10.3389/fimmu.2023.1284366, p.12]
- **results：** 结构验证中，V4 有 97.4% 残基位于 favored region，ERRAT 为 93.75，ProSA Z-score 为 -4.52。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.9]
- **results：** 密码子优化后，CAI 达到 1.0、GC content 为 52.7%，并且通过 SnapGene 将优化后的 V4 插入 pET28a(+) 进行 in silico cloning。
  - 证据：[doi:10.3389/fimmu.2023.1284366, p.10]；[doi:10.3389/fimmu.2023.1284366, p.13]

## 页码证据

- [doi:10.3389/fimmu.2023.1284366, p.11]
- [doi:10.3389/fimmu.2023.1284366, p.1]
- [doi:10.3389/fimmu.2023.1284366, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
