# Design of high-specificity binders for peptide-MHC-I complexes

- **论文 ID：** `EVIW-5B2A016A7A13F3AF`
- **期刊 / 来源：** Science Advances（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1126/science.adv0185](https://doi.org/10.1126/science.adv0185)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出一条面向 pMHCI 的端到端计算设计与筛选流程：用 RFdiffusion、ProteinMPNN、AF2/AF3 与 Chai-1 生成并排序 binder，再经 yeast display、CAR 功能实验、SPR 和结构解析验证；该流程在 11 个靶标上找到特异性 binder，其中 8 个可驱动 peptide-specific T 细胞激活。

## 创新边界

`主要新意在 pMHCI 结合蛋白的结构生成、排序与实验验证管线；它证明该靶类可被系统设计，但不独立证明全球唯一性或对所有 HLA/peptide 组合的完全覆盖。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何为特定 peptide-MHC-I 复合物设计既能高亲和结合、又能强区分目标肽与同一 HLA 上其他肽的结合蛋白，从而用于 CAR 或蛋白式肿瘤/感染靶向。

## 方法

- 从实验或预测pMHC结构出发生成界面骨架，后续序列设计、结构预测筛选和论文报告的细胞/生化验证。[doi:10.1126/science.adv0185, p.2][doi:10.1126/science.adv0185, p.5]

## 数据与基准

- 覆盖11个不同pMHC-I目标；至少一个复合物结构公开为PDB 9O5S。[doi:10.1126/science.adv0185, p.2][doi:10.1126/science.adv0185, p.8]

## 比较基线

- 与经验TCR筛选、scFv库和既有深度学习binder设计策略作任务/流程比较。[doi:10.1126/science.adv0185, p.2]

## 结果证据

- 论文报告获得识别目标肽-HLA组合的高特异性结合体，并用结构及功能测定支持；不可外推至未测试等位基因/肽。[doi:10.1126/science.adv0185, p.2][doi:10.1126/science.adv0185, p.7]

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 广泛人群覆盖需要成百上千种结合体；脱靶于同一HLA呈递的其他肽仍是中心难题。[doi:10.1126/science.adv0185, p.2][doi:10.1126/science.adv0185, p.7]

## 仍未知

- 更广泛的 peptidome 交叉反应图谱未被穷尽测定。
- 体内疗效、药代与安全性未在这些页内展示。
- 对更多 HLA allele 与更多 peptide 长度/来源的泛化能力仍待验证。

## Pi 结构化证据摘录

- **baseline：** 特异性判定的主要基线是同一 HLA 上的 1 到 4 个 closely related off-target peptides，以及 DMSO 或未脉冲的背景细胞。
  - 证据：[doi:10.1126/science.adv0185, p.3]；[doi:10.1126/science.adv0185, p.5]
- **baseline：** mage-513 的 top-hit peptides 先在 yeast 上出现，再被 target-cell pulsing 复测，以排除 covalent-linkage 造成的假阳性。
  - 证据：[doi:10.1126/science.adv0185, p.6]
- **baseline：** 杀伤实验用 cognate peptide、noncognate peptide 和 unpulsed controls 作对照，避免把一般性细胞毒性误判为靶向性。
  - 证据：[doi:10.1126/science.adv0185, p.7]
- **data：** 研究覆盖 11 个 pMHCI 复合物，涉及 HLA-A*01:01、A*02:01、A*03:01 和 C*07:02，抗原来源包括病毒蛋白、肿瘤相关蛋白和 neoantigen。
  - 证据：[doi:10.1126/science.adv0185, p.3]
- **data：** 每个靶标对应的设计规模约为 200 到 12000 条序列，显示该工作在库规模上是按靶标定制的大规模设计。
  - 证据：[doi:10.1126/science.adv0185, p.3]
- **data：** mage-513 的特异性还通过 covalently linked peptide-HLA-A*01:01 yeast library 以及基于 human proteome 的 sequence-similarity scan 做了二次筛查。
  - 证据：[doi:10.1126/science.adv0185, p.6]
- **declared_resources：** mart1 binder-antigen complex 的坐标和 structure factors 已存入 PDB，编号为 9O5S/pdb_00009o5s。
  - 证据：[doi:10.1126/science.adv0185, p.8]
- **declared_resources：** 用于 pMHC-I binder 计算设计的 code 和 examples 已在 Zenodo 以 10.5281/zenodo.15169815 发布。
  - 证据：[doi:10.1126/science.adv0185, p.8]；[doi:10.1126/science.adv0185, p.9]
- **limitations：** 作者明确指出，RFdiffusion 的大量 trajectories 只有很小一部分能生成既大量接触 peptide 又主要避开 MHC 的 backbone，因此计算代价较高。
  - 证据：[doi:10.1126/science.adv0185, p.4]
- **limitations：** 有些设计虽然能在 yeast 上结合，但在 Jurkat/CAR 中只表现为弱或背景激活，说明 residual cross-reactivity 仍然是实际风险。
  - 证据：[doi:10.1126/science.adv0185, p.5]
- **limitations：** Discussion 里作者也承认，需要从更多 design campaigns 学习哪些性质与 scaffold geometry 最能预测 specific cell activation，说明当前泛化规律仍不完整。
  - 证据：[doi:10.1126/science.adv0185, p.7]
- **method：** 先用 RFdiffusion 以外露的 peptide 残基为条件生成跨越 MHC-I groove 的 binder backbone，再用 ProteinMPNN 设计序列并用 AF2 评估是否按设计折叠与结合。
  - 证据：[doi:10.1126/science.adv0185, p.3]
- **method：** 随后用 ProteinMPNN 和 fine-tuned AF2 比较 on-target 与 proteome 中近似 off-target peptide 的复合物置信度，以筛除更可能交叉反应的设计。
  - 证据：[doi:10.1126/science.adv0185, p.3]
- **method：** 作者为 11 个 pMHCI 靶标合成 200 到 12000 个设计，做 yeast display、on/off-target tetramer FACS，以及 NGS enrichment 或 clonal selection 来鉴定命中。
  - 证据：[doi:10.1126/science.adv0185, p.3]
- **method：** 对可复用 scaffold，他们用 partial diffusion 从已命中的骨架出发重采样以扩展到相关靶标，并对命中设计做 E. coli 表达、SEC 和 SPR 验证。
  - 证据：[doi:10.1126/science.adv0185, p.4]；[doi:10.1126/science.adv0185, p.5]
- **method：** 他们把部分设计嵌入 CAR，在 Jurkat 细胞和 293T peptide-pulsing 系统中测 CD69；对更关键的靶标，还在 primary human T cells 中测试杀伤。
  - 证据：[doi:10.1126/science.adv0185, p.4]；[doi:10.1126/science.adv0185, p.5]；[doi:10.1126/science.adv0185, p.7]
- **results：** 对 8/11 个 pMHCI 靶标，de novo diffusion 给出了能在 yeast 或 CAR 中区分 on-target 与近似 off-target 的特异性 binder。
  - 证据：[doi:10.1126/science.adv0185, p.2]；[doi:10.1126/science.adv0185, p.3]
- **results：** mart1-3 与 MART-1 pMHCI 的 2.2 Å 晶体结构与设计模型高度一致，Cα RMSD 为 0.4 Å，interface all-atom RMSD 也为 0.4 Å。
  - 证据：[doi:10.1126/science.adv0185, p.3]
- **results：** hiv-10 和 mage-513 纯化后在 SPR 中表现为单峰折叠，且对各自 cognate pMHCI 的亲和力达到单到双位数 nM。
  - 证据：[doi:10.1126/science.adv0185, p.5]
- **results：** mage-513 CAR 对 MAGE-A3 peptide 产生强而特异的 Jurkat activation，而对 Titin peptide、DMSO 和部分自肽背景较低；alanine scanning 与设计模型一致地指出关键接触位点。
  - 证据：[doi:10.1126/science.adv0185, p.5]；[doi:10.1126/science.adv0185, p.6]
- **results：** 针对 gp100、MART-1、WT1、SARS、HIV、PRAME 和 PHOX2B 的设计都能给出 target-selective CD69 activation，且 PRAME/WT1 binder 还能在 primary T cells 中介导对脉冲靶细胞的 killing。
  - 证据：[doi:10.1126/science.adv0185, p.6]；[doi:10.1126/science.adv0185, p.7]

## 页码证据

- [doi:10.1126/science.adv0185, p.2]
- [doi:10.1126/science.adv0185, p.2]
- [doi:10.1126/science.adv0185, p.5]
- [doi:10.1126/science.adv0185, p.7]
- [doi:10.1126/science.adv0185, p.8]
- [doi:10.1126/science.adv0185, p.2]
- [doi:10.1126/science.adv0185, p.8]
- [doi:10.1126/science.adv0185, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
