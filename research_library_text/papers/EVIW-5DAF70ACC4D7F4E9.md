# De novo designed proteins neutralize lethal snake venom toxins

- **论文 ID：** `EVIW-5DAF70ACC4D7F4E9`
- **期刊 / 来源：** Nature（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1038/s41586-024-08393-x](https://doi.org/10.1038/s41586-024-08393-x)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `扩散/生成` / `结构预测`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者声称用深度学习从头设计了能结合并中和 3FTx 毒素的蛋白，得到 SHRT、LNG 和 CYTX 等候选，并展示了体外中和、晶体结构吻合和小鼠保护效果。

## 创新边界

`冻结材料足以支持针对 3FTx 的 de novo binder 设计与验证；但是否属于全球首个同类 antivenom 方案，材料内没有独立 prior-art 证据可核实。`。这不是全球首创性检索或独立复现结论。

## 研究问题

针对短链/长链 α-neurotoxins 与 cytotoxins 的 3FTx 毒素，现有动物来源 antivenom 在免疫原性、成本、冷链和中和效力上都不理想，因此需要可重组、稳定且可低成本制造的新型中和分子。

## 方法

- RFdiffusion/sequence design/structure prediction筛选，表达binding/neutralization与动物挑战。

## 数据与基准

- 多蛇毒毒素、设计binder库和实验。

## 比较基线

- 抗体/传统antivenom与计算筛选对照。

## 结果证据

- 标题/正文明确报告中和致死毒素；属于直接实验，具体剂量按论文。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 毒素覆盖、免疫原性/PK/临床转化未知。

## 仍未知

- 未见公开代码仓库或可复用脚本的冻结证据。
- 补充材料未展开，无法核对全部原始图表与统计细节。
- CYTX 的局部 dermonecrosis 体内效力不足，后续优化空间仍大。
- 全球首创性未被冻结材料独立核验。

## Pi 结构化证据摘录

- **baseline：** 与既有 ScNtx 和 α-cobratoxin nanobody 对照相比，SHRT 和 LNG 的功能中和表现更强或相当，且论文明确把这些既有 VHH 作为 benchmark。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.7]；[doi:10.1038/s41586-024-08393-x, p.16]
- **baseline：** 作者将传统动物来源 antivenom 及既有 recombinant antibodies, nanobodies, aptamers 视为基线方案，并强调其在 3FTx 中和、生产成本和批次一致性上的不足。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.5]；[doi:10.1038/s41586-024-08393-x, p.9]；[doi:10.1038/s41586-024-08393-x, p.10]
- **data：** 设计目标包括短链 α-neurotoxin ScNtx、长链 α-neurotoxin α-cobratoxin，以及来自 86 个序列的 consensus cytotoxin。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.6]；[doi:10.1038/s41586-024-08393-x, p.7]；[doi:10.1038/s41586-024-08393-x, p.17]
- **data：** 每个目标最初各生成约 2000 个 RFdiffusion 设计；后续实验筛选了 44 个 ScNtx、42 个 α-cobratoxin 和 55 个 cytotoxin 设计，并对部分命中进行了 78/38 个 partial diffusion 优化。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.6]；[doi:10.1038/s41586-024-08393-x, p.7]；[doi:10.1038/s41586-024-08393-x, p.17]
- **data：** 体外和体内实验分别使用了 RD 细胞、HEK293T、N/TERT 角质形成细胞、male NSA mice、CD1 mice，以及来自多个 Naja 物种的 whole venoms。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.8]；[doi:10.1038/s41586-024-08393-x, p.21]；[doi:10.1038/s41586-024-08393-x, p.22]；[doi:10.1038/s41586-024-08393-x, p.23]
- **declared_resources：** 计算资源：RFdiffusion、ProteinMPNN、AF2 initial guess、Rosetta FastRelax/ddg、partial diffusion。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.6]；[doi:10.1038/s41586-024-08393-x, p.17]
- **declared_resources：** 实验平台：yeast display、Octet Red96 BLI、Biacore 8K SPR、Jasco J-1500 CD、QUBE automated patch clamp、NSLS2 AMX beamline。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.18]；[doi:10.1038/s41586-024-08393-x, p.19]；[doi:10.1038/s41586-024-08393-x, p.20]；[doi:10.1038/s41586-024-08393-x, p.21]
- **declared_resources：** 生物材料：ScNtx（K. phaffii 表达）、α-cobratoxin（Latoxan）、Naja pallida cytotoxin（Sigma-Aldrich）和多个 Naja venoms。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.18]；[doi:10.1038/s41586-024-08393-x, p.22]；[doi:10.1038/s41586-024-08393-x, p.23]
- **limitations：** CYTX 在小鼠 intradermal Naja nigricollis dermonecrosis 模型中于 1:1、1:2.5 和 1:5 比例均未显著降低病灶，作者明确指出其亲和力可能还需进一步优化。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.7]；[doi:10.1038/s41586-024-08393-x, p.23]
- **limitations：** 作者也承认传统 antivenom 在可预见的短期内仍可能是临床主力，这些设计蛋白更可能先作为 antivenom 的 fortifying agents。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.9]
- **limitations：** 整套设计依赖已知结构或序列信息可用的毒素目标，因此对未结构化、未测序或难表达毒素的外推能力仍不明确。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.5]；[doi:10.1038/s41586-024-08393-x, p.9]
- **method：** 用 RFdiffusion 结合 secondary structure tensor 与 block adjacency tensor 预设 binder β-strand 和毒素 β-strand 配对，再经 ProteinMPNN、AF2 initial guess 和 Rosetta ddg/PAE/pLDDT 过滤；对优胜构型再做 partial diffusion 优化。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.6]；[doi:10.1038/s41586-024-08393-x, p.17]
- **method：** 对 cytotoxin，先从 UniProt 收集 86 个 unique CTX 序列并做 MSA/consensus 设计，再把 consensus cytotoxin 作为 RFdiffusion 输入，热点约束其三指环区域。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.7]；[doi:10.1038/s41586-024-08393-x, p.17]
- **method：** 候选蛋白分别在 yeast display、E. coli 或 K. phaffii 中表达纯化，并用 SEC、BLI、SPR、CD 与 X-ray crystallography 做表征。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.18]；[doi:10.1038/s41586-024-08393-x, p.19]；[doi:10.1038/s41586-024-08393-x, p.20]
- **method：** 功能验证包括 RD 细胞 patch-clamp、HEK293T 与 N/TERT 细胞毒性实验，以及 NSA/CD1 小鼠的 LD50、预混和 rescue 型体内保护实验。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.21]；[doi:10.1038/s41586-024-08393-x, p.22]；[doi:10.1038/s41586-024-08393-x, p.23]
- **results：** SHRT 对 ScNtx 的 SPR Kd 达到 0.9 nM，Tm 78°C，晶体结构与设计模型 2.58 Å 分辨率、1.04 Å RMSD 一致。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.6]；[doi:10.1038/s41586-024-08393-x, p.15]
- **results：** LNG 对 α-cobratoxin 的 SPR Kd 为 1.9 nM，Tm >95°C，复合物晶体结构 2.68 Å 分辨率且对设计模型 RMSD 仅 0.42 Å。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.6]；[doi:10.1038/s41586-024-08393-x, p.15]
- **results：** CYTX 对 Naja pallida cytotoxin 的 SPR Kd 为 271 nM，Tm 61°C；后续 CYTX_B10 通过引入二硫键提高到 70.3°C，但亲和力降至 740 nM。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.7]；[doi:10.1038/s41586-024-08393-x, p.15]
- **results：** SHRT 与 LNG 在 patch-clamp 中可于 1:1 摩尔比完全中和对应神经毒素；CYTX 对七种 Naja whole venoms 及分离 cytotoxin 提供约 70–90% 或 85% 的保护；小鼠中 SHRT/LNG 可在预混和部分 rescue 条件下提供完全保护或部分保护。
  - 证据：[doi:10.1038/s41586-024-08393-x, p.7]；[doi:10.1038/s41586-024-08393-x, p.8]；[doi:10.1038/s41586-024-08393-x, p.16]

## 页码证据

- [doi:10.1038/s41586-024-08393-x, p.1]
- [doi:10.1038/s41586-024-08393-x, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
