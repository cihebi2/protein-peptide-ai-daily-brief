# Deep learning in GPCR drug discovery: benchmarking the path to accurate peptide binding

- **论文 ID：** `EVIW-7BBE077F641CF7F4`
- **期刊 / 来源：** Briefings in Bioinformatics（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1093/bib/bbaf186](https://doi.org/10.1093/bib/bbaf186)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `语言模型` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

论文声称构建了一个独立的 GPCR–peptide 基准集，并系统比较 8 个深度学习工具在配体重发现、分类和结构建模上的表现，同时给出面向不同使用场景的实用选择流程。

## 创新边界

`这篇工作主要是 benchmark 与分析，不是提出新模型；其创新边界在于数据集构建、工具对比、rescoring 评估和工作流总结。`。这不是全球首创性检索或独立复现结论。

## 研究问题

作者要解决的是：在 GPCR–peptide 药物发现中，如何可靠地区分真实内源性肽配体与高相似度 decoy，并判断预测到的复合物结构是否足够准确、足以支持筛选与排序。

## 方法

- 多种sequence/structure/PLM模型在一致数据上训练/评价。

## 数据与基准

- GPCR-peptide binding benchmark与cold-start splits。

## 比较基线

- 各受测DL/结构模型。

## 结果证据

- 论文揭示模型性能/泛化差异；无新实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- GPCR peptide数据少、负样本与同源泄漏显著。

## 仍未知

- 这些模型在含 PTM、不同构象态、或更大复合体（如 G protein、arrestin）上的外推能力尚不明确。
- GitHub/Zenodo 资源在本次评审中未被额外核验，只依据论文数据可用性声明。

## Pi 结构化证据摘录

- **baseline：** Peptriever 和 D-SCRIPT 被作为序列/语言模型基线，其中 D-SCRIPT 近似随机，而 Peptriever 需要更高的 ligand 选择数才表现更好。
  - 证据：[doi:10.1093/bib/bbaf186, p.3]
- **baseline：** AF3、Chai-1 与 RF-AA 构成主要结构基线；在分类和结构精度上，AF2 整体优于这些模型。
  - 证据：[doi:10.1093/bib/bbaf186, p.3]；[doi:10.1093/bib/bbaf186, p.6]；[doi:10.1093/bib/bbaf186, p.7]
- **baseline：** ESMFold 与 NeuralPLexer 在该任务上表现最弱，前者难以富集真实配体，后者几乎未能复现任何 GPCR–peptide interface。
  - 证据：[doi:10.1093/bib/bbaf186, p.3]；[doi:10.1093/bib/bbaf186, p.6]
- **baseline：** 大多数 rescoring 方法并未超过原始基线，只有 AFM-LIS 明显带来增益，因此 rescoring 并非普遍有效。
  - 证据：[doi:10.1093/bib/bbaf186, p.3]；[doi:10.1093/bib/bbaf186, p.5]
- **data：** 分类基准集最终包含 124 个主配体 GPCR–ligand 对和 1240 个 decoy 对，总计 1364 个 GPCR–peptide 交互样本。
  - 证据：[doi:10.1093/bib/bbaf186, p.3]；[doi:10.1093/bib/bbaf186, p.10]
- **data：** 受体覆盖 105 个 class A、15 个 class B1 和 3 个 class F GPCR，体现出较广的受体家族跨度。
  - 证据：[doi:10.1093/bib/bbaf186, p.3]
- **data：** 结构基准集覆盖 47 个受体与 58 个肽配体，且所有输入都从 PDB 的 SEQRES 提取为完整表达序列。
  - 证据：[doi:10.1093/bib/bbaf186, p.6]；[doi:10.1093/bib/bbaf186, p.10]
- **data：** 作者明确只使用天然氨基酸序列，不纳入 unnatural amino acids，以避免部分模型无法接受这类输入。
  - 证据：[doi:10.1093/bib/bbaf186, p.10]
- **declared_resources：** 作者在 Data availability 中给出了 GitHub 仓库与 Zenodo 数据包，说明 benchmark 数据与分析代码可公开获取。
  - 证据：[doi:10.1093/bib/bbaf186, p.11]
- **declared_resources：** 所有结构预测与 runtime 对比都在 NVIDIA A100 GPUs 上完成。
  - 证据：[doi:10.1093/bib/bbaf186, p.11]
- **declared_resources：** 论文还声明了 Carlsberg Foundation 资助（grant CF20-0248）。
  - 证据：[doi:10.1093/bib/bbaf186, p.11]
- **limitations：** 作者明确指出，competitive tournament 虽然能加速多肽同时建模，但会降低 true-positive recovery。
  - 证据：[doi:10.1093/bib/bbaf186, p.3]
- **limitations：** 结构模板有时会把肽引导到错误的 intracellular docking 方向，作者认为这可能与 GPCR–G protein 模板偏置有关。
  - 证据：[doi:10.1093/bib/bbaf186, p.8]
- **limitations：** 10:1 的 decoy-to-ligand 设定适合 benchmark，但与真实筛选中负例远多于正例、命中率极低的情形并不完全一致。
  - 证据：[doi:10.1093/bib/bbaf186, p.8]
- **limitations：** RF-AA 在部分案例中会把 GPCR 折叠进 binding pocket，且对含大 extracellular domains 的受体更容易产生错误结构。
  - 证据：[doi:10.1093/bib/bbaf186, p.6]；[doi:10.1093/bib/bbaf186, p.9]
- **method：** 作者从 IUPHAR/BPS Guide to Pharmacology 通过 Pygtop API 收集人类 GPCR 与内源性肽配体，并以主配体为单位建立分类任务。
  - 证据：[doi:10.1093/bib/bbaf186, p.10]
- **method：** 基准集为每个受体构造 10 个 decoy，其中 5 个较相似、5 个较不相似，decoy 选择依据是 GPCR pocket 相似性与配体序列相似性。
  - 证据：[doi:10.1093/bib/bbaf186, p.10]
- **method：** 作者用 AF2、AF3、Chai-1、NeuralPLexer、RoseTTAFold-AllAtom、Peptriever、ESMFold 和 D-SCRIPT 对 1364 个 GPCR–peptide 复合体进行打分与排序。
  - 证据：[doi:10.1093/bib/bbaf186, p.2]；[doi:10.1093/bib/bbaf186, p.10]
- **method：** 结构基准部分选取了 2021-09-30 之后公开的 67 个 GPCR–peptide 复合物，并用 DockQ 评估 docked pose 的准确性。
  - 证据：[doi:10.1093/bib/bbaf186, p.6]；[doi:10.1093/bib/bbaf186, p.10]
- **method：** 作者还对 AF2、AF3、RF-AA、Chai-1 等预测结果进行了 RIA、APPRAISE、AFM-LIS、DOVE-GNN 与 DeepRank-GNN-esm 等 rescoring。
  - 证据：[doi:10.1093/bib/bbaf186, p.3]；[doi:10.1093/bib/bbaf186, p.10]
- **results：** 在配体/decoy 分类上，结构-aware 模型整体优于序列型模型；最佳模型 AF2 的 AUC 为 0.86，AF3 为 0.82，Chai-1 为 0.76，而 D-SCRIPT 接近随机。
  - 证据：[doi:10.1093/bib/bbaf186, p.2]；[doi:10.1093/bib/bbaf186, p.3]
- **results：** AF2 在不使用模板时可将主配体在 58% 的 GPCR 上排到第 1 名，显示出较强的 ligand recall。
  - 证据：[doi:10.1093/bib/bbaf186, p.3]
- **results：** AFM-LIS 是唯一显著提升分类排名的 rescoring 方法，且对 AF2 的改进具有统计显著性（P=.0018）。
  - 证据：[doi:10.1093/bib/bbaf186, p.5]
- **results：** 在独立结构基准中，AF2 正确复现了约 94% 的配体结合模式，并总体上优于 AF3、Chai-1 与 RF-AA。
  - 证据：[doi:10.1093/bib/bbaf186, p.2]；[doi:10.1093/bib/bbaf186, p.6]；[doi:10.1093/bib/bbaf186, p.7]
- **results：** AFM-LIS 与 DockQ 在 AF2 预测上呈明显正相关（r=.67），说明其确实提取到了与真实对接质量相关的局部界面信息。
  - 证据：[doi:10.1093/bib/bbaf186, p.7]

## 页码证据

- [doi:10.1093/bib/bbaf186, p.1]
- [doi:10.1093/bib/bbaf186, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
