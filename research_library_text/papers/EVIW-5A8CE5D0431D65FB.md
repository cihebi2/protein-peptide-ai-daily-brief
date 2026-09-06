# Next Generation SICLOPPS Screening for the Identification of Inhibitors of the HIF-1α/HIF-1β Protein-Protein Interaction

- **论文 ID：** `EVIW-5A8CE5D0431D65FB`
- **期刊 / 来源：** ACS Chem Biol
- **发表时间：** 2024 Sep 23
- **DOI：** [10.1021/acschembio.4c00494](https://doi.org/10.1021/acschembio.4c00494)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

论文声称提出了一套 revised high-content, high-throughput SICLOPPS workflow，并用它找到比既往 manual screen 更高命中率、且在体外和细胞中更活跃的 HIF-1α/HIF-1β inhibitors。

## 创新边界

`本工作的边界是筛选流程与 hit-ranking 的改进，以及对已知 HIF-1α/HIF-1β 体系的验证；本文没有在 frozen evidence 中证明跨靶标普适性，也没有独立 prior-art 证据支持全球新颖性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

作者要解决的是：如何把 SICLOPPS 从手工挑 colony 的低通量流程，升级为可用 NGS、biopanning 和计算分析来稳定识别 HIF-1α/HIF-1β PPI 抑制性 cyclic peptide 的筛选流程。

## 方法

- genetic encoded cyclic peptide library、cell selection与biochemical validation。

## 数据与基准

- SICLOPPS library/HIF PPI candidates。

## 比较基线

- earlier SICLOPPS/controls。

## 结果证据

- 明确实验screening/inhibition数据。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 细胞/target特异、命中机制与药代未知。

## 仍未知

- 该工作在其他 PPI 靶标上的泛化性能未在本文直接验证。
- 改进后的排名公式在不同库规模或不同筛选压力下是否稳定，仍未回答。
- cyclo-CLLFCL 的高亲和力是否主要来自二硫键或其他构象约束，作者未能确定。

## Pi 结构化证据摘录

- **baseline：** 作者明确把旧流程定义为手工挑选 surviving colonies 再做进一步 drop spotting 的方法，并指出它会引入 bias/errors，也不适合 enrichment 型 hit selection。
  - 证据：[doi:10.1021/acschembio.4c00494, p.1]
- **baseline：** 相较既往手工 SICLOPPS screens，本文所用 HIF-1 体系过去的 hit rate 很低：3.2 million 库只得到 1 个 validated hit，dual inhibitor screen 也只有 3 个 validated hits。
  - 证据：[doi:10.1021/acschembio.4c00494, p.2]
- **data：** 初始 CX5 库中，超过 67% 的序列落在每百万 reads 的 1-10 次区间，90% 低于 100 次；被 spike 的 cyclo-AAAAA 约占库的 8%。
  - 证据：[doi:10.1021/acschembio.4c00494, p.4]
- **data：** round 1 后，CAAAAA、CRLYVL 和 CVTYVL 三个序列合计 7.8%，其中 control 序列从 80,000 降到 45,000 copies per million reads；round 2 后 top sequence CRTYIL 达 159,000 copies per million reads，top 15 占据超过一半库。
  - 证据：[doi:10.1021/acschembio.4c00494, p.4]
- **data：** 作者把 top 20 cyclic peptides 和 control cyclo-CLLFVY 合成后用于 MST；同时把 7 个最活跃候选做了 Tat-tagged 版本，用于 U2OS-HRE-Luc 和后续 MCF7 CAIX qPCR。
  - 证据：[doi:10.1021/acschembio.4c00494, p.5]；[doi:10.1021/acschembio.4c00494, p.6]；[doi:10.1021/acschembio.4c00494, p.7]
- **declared_resources：** 论文声明 supporting information 可用，且 Python scripts 已放在 Tavassoli Lab GitHub；raw data 另存于 University of Southampton data repository，DOI 为 10.5258/SOTON/D3197。
  - 证据：[doi:10.1021/acschembio.4c00494, p.7]
- **declared_resources：** Supporting Information 还包括 HIF-1 RTHS、同源性分析、motif 图、剂量反应曲线、相关性分析、细胞活性评估、top 25 hits 表格和 compound data PDF。
  - 证据：[doi:10.1021/acschembio.4c00494, p.7]
- **limitations：** 作者承认 rank 与 KD 只有有限一致性，尤其按 % enrichment after 2 rounds 排序时与体外亲和力相关性较差。
  - 证据：[doi:10.1021/acschembio.4c00494, p.6]
- **limitations：** 最强结合者 cyclo-CLLFCL 并不是最富集的序列，说明 enrichment-based ranking 仍然不能直接等同生物活性。
  - 证据：[doi:10.1021/acschembio.4c00494, p.6]
- **limitations：** 作者自己也指出，现有 IEDB cluster tool 和 XSTREME 对 6 aa SICLOPPS 库并不合适，因此分析依赖自定义 Python 规则。
  - 证据：[doi:10.1021/acschembio.4c00494, p.4]
- **limitations：** cyclo-CLLFCL 的高亲和力是否来自二硫键或其他构象约束，作者未能证实；同时他们也提到 E. coli growth advantage 或 toxicity 可能干扰排序。
  - 证据：[doi:10.1021/acschembio.4c00494, p.4]；[doi:10.1021/acschembio.4c00494, p.6]
- **method：** 作者把 SICLOPPS 与 pooled colony collection、NGS 和 biopanning 结合，用生存筛选来富集可解除 HIF-1 RTHS 抑制的 cyclic peptide。
  - 证据：[doi:10.1021/acschembio.4c00494, p.1]；[doi:10.1021/acschembio.4c00494, p.4]
- **method：** 筛选库是 CXXXXX hexa-peptide library，15 个随机位点由 NNS codons 编码；作者用两步 PCR 加入 i5/i7 adapters、indexes 和 P5/P7，并额外插入 6 个随机碱基提升测序多样性。
  - 证据：[doi:10.1021/acschembio.4c00494, p.2]；[doi:10.1021/acschembio.4c00494, p.4]
- **method：** 作者编写 Python scripts 做 QC、截取正确 intein 序列、翻译 extein，并根据初始库、round 1 和 round 2 的丰度与富集计算 adjusted inverse enrichment 重新排序 hits。
  - 证据：[doi:10.1021/acschembio.4c00494, p.4]；[doi:10.1021/acschembio.4c00494, p.5]
- **method：** HIF-1 RTHS 通过 HIF-1α-P22 与 HIF-1β-434 fusion proteins 形成 chimeric repressor，进而控制 KanR 和 His3 reporter genes 的存活选择。
  - 证据：[doi:10.1021/acschembio.4c00494, p.4]
- **results：** NGS 富集结果显示多个共享 motif，特别是 CRXXIL 相关家族，以及更宽的 CRX(L/V/F/Y)XL motif。
  - 证据：[doi:10.1021/acschembio.4c00494, p.4]
- **results：** 在 MST 中，20 个合成候选里有 19 个能结合 HIF-1α；其中 7 个优于 cyclo-CLLFVY，最强者 cyclo-CLLFCL 的 KD 为 470 ± 10 nM。
  - 证据：[doi:10.1021/acschembio.4c00494, p.5]
- **results：** 在 U2OS-HRE-Luc 细胞中，7 个 Tat-tagged peptides 在 40 μM、6 h hypoxia 下都能降低 luciferase；cyclo-CLLFCL 最强，20/40 μM 分别降低 65% 和 71%，16 h 条件下 IC50 为 13 ± 4 μM。
  - 证据：[doi:10.1021/acschembio.4c00494, p.6]
- **results：** 在 MCF7 细胞中，4 个候选都抑制了 CAIX 表达，IC50 范围为 4.4 ± 0.2 到 22 ± 3 μM。
  - 证据：[doi:10.1021/acschembio.4c00494, p.7]

## 页码证据

- [doi:10.1021/acschembio.4c00494, p.1]
- [doi:10.1021/acschembio.4c00494, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
