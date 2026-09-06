# A Machine Learning-Enabled Venom Peptide Platform for Rapid Drug Discovery

- **论文 ID：** `EVIW-27ACE42DCA76D5BE`
- **期刊 / 来源：** Pharmaceuticals (Basel)
- **发表时间：** 2026 Feb 9
- **DOI：** [10.3390/ph19020288](https://doi.org/10.3390/ph19020288)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称建立了一个 ML-enabled venom peptide platform：先用 foldability model 设计 VCX library，再用 Trx-fusion 高通量表达与 phage display/NGS/SPR 验证获得四个靶点的 binder，最后通过 NNK-block screening 加 ML-assisted affinity maturation 将 DLL3 hits 推进到 nanomolar 级 lead。

## 创新边界

`新意主要是把既有 foldability 预测、venom scaffold mining、Trx 高通量表达、NNK-block 扫描和监督式 ML ranking 串成一条可执行的 hit-to-lead 流水线；冻结证据只能支持相对前作的组合式增量创新，不能证明全球首创。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何把天然 venom peptide 的结构多样性转化为可规模化筛选、可高通量表达、可快速优化的治疗性肽发现平台，同时避免随机突变导致折叠失败，以及化学合成 hit-to-lead 带来的高成本和长周期。

## 方法

- peptide representations、property/activity models与candidate prioritization。

## 数据与基准

- venom peptides/activities。

## 比较基线

- 传统venom mining。

## 结果证据

- 论文报告候选/可能实验；只明确assay写实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 毒性/物种/assay标签和体内未知。

## 仍未知

- VCX scaffold 数量在不同章节写成 482 与 491，口径不一致。
- 未提供可复用代码仓库或公开模型权重链接，DeepSeq.AI 模型为专有。
- 未见独立外部 prior-art 检索，全球首创性无法验证。
- focused library 的完整序列集未在正文展开，仅给出设计规模。

## Pi 结构化证据摘录

- **baseline：** 相对作者先前 seven-scaffold DCP platform，VCX 用 hundreds of scaffolds 构成更高 foldability 和更高 diversity 的 library。
  - 证据：[doi:10.3390/ph19020288, p.3]；[doi:10.3390/ph19020288, p.4]；[doi:10.3390/ph19020288, p.14]
- **baseline：** 相对 Metavenom，VCX 只保留 <45 aa peptide modality，并通过内部 randomization 具备可扩展性；文中称 Metavenom 约 41,000 unique sequences，且缺少内生扩增机制。
  - 证据：[doi:10.3390/ph19020288, p.14]
- **baseline：** 相对只用 primary panning data 训练的 model，加入 NNK-block data 后，DLL3 prediction correlation 从 0.33 提升到 0.57。
  - 证据：[doi:10.3390/ph19020288, p.10]；[doi:10.3390/ph19020288, p.12]
- **baseline：** 相对传统 directed evolution 需 2–3 轮迭代，作者声称 ML-assisted affinity maturation 可在单轮内获得 up to 500-fold 提升。
  - 证据：[doi:10.3390/ph19020288, p.13]；[doi:10.3390/ph19020288, p.15]
- **data：** VenomZone 与 ConoServer 的初筛规模分别为 7794 和 3073 条记录；经筛选后用于设计的 scaffold 为 391 个和 91 个，最终库规模约 6×10^5。
  - 证据：[doi:10.3390/ph19020288, p.3]；[doi:10.3390/ph19020288, p.15]
- **data：** 高通量表达共处理 689 个 Trx-VCX clone，其中 77% 产量超过 20 mg/L、16% 超过 100 mg/L，低产量样本常形成 inclusion bodies。
  - 证据：[doi:10.3390/ph19020288, p.5]
- **data：** Primary panning 对四个 target 共得到 33 个 CD47、22 个 DLL3、57 个 IL33 和 16 个 P2X7R hits，覆盖 11–39 个 scaffold。
  - 证据：[doi:10.3390/ph19020288, p.7]
- **data：** DLL3 affinity maturation 的训练数据来自 35 个 SPR-characterized binders，其中 21 个是 primary binders、14 个来自 NNK-block screen。
  - 证据：[doi:10.3390/ph19020288, p.10]；[doi:10.3390/ph19020288, p.12]；[doi:10.3390/ph19020288, p.13]
- **declared_resources：** Supplementary Materials 提供 LC-MS results、Figures S1-S5 和 Tables S1-S5；正文也说明 data availability 在 article/Supplementary Material 内。
  - 证据：[doi:10.3390/ph19020288, p.21]
- **declared_resources：** Funding 为 none，且作者披露部分作者受雇于 Genentech 或 DeepSeq.AI，构成明确的 resource/conflict context。
  - 证据：[doi:10.3390/ph19020288, p.21]
- **declared_resources：** 方法部分显式列出 Twist Bioscience、Integrated DNA Technology、Biacore S200、MiSeq、ESMFold、DeepSeq.AI transformer model 等资源与平台。
  - 证据：[doi:10.3390/ph19020288, p.16]；[doi:10.3390/ph19020288, p.17]；[doi:10.3390/ph19020288, p.18]；[doi:10.3390/ph19020288, p.19]；[doi:10.3390/ph19020288, p.20]
- **limitations：** 作者明确指出，affinity maturation 仍然不 trivial，且不能保证对每个 target 都成功。
  - 证据：[doi:10.3390/ph19020288, p.15]
- **limitations：** 对 GPCR 或 ion channel 等复杂 target，初始 binders 仍可能停留在 micromolar affinity，后续仍需 further engineering。
  - 证据：[doi:10.3390/ph19020288, p.15]
- **limitations：** 自然 venom scaffold 的 promiscuity 和 off-target specificity 尚未解决，作者将其列为未来关键任务。
  - 证据：[doi:10.3390/ph19020288, p.15]
- **limitations：** NGS enrichment 作为 affinity proxy 可能受 non-specific binding 或 growth bias 影响，因此作者才并行训练非特异性背景模型。
  - 证据：[doi:10.3390/ph19020288, p.14]；[doi:10.3390/ph19020288, p.19]
- **method：** 先从 VenomZone 和 ConoServer 过滤短于 45 aa、含多二硫键的 venom/conotoxin scaffold，再用既有 foldability model 标记 amenable positions 并生成 VCX library。
  - 证据：[doi:10.3390/ph19020288, p.3]；[doi:10.3390/ph19020288, p.15]
- **method：** Library 通过 Kunkel mutagenesis 构建并展示在 M13 phage 的 p3/p8 上，随后对 CD47、DLL3、IL33、P2X7R 进行分轮 panning，最后用 NGS 排序并以 SPR 复核阳性 clone。
  - 证据：[doi:10.3390/ph19020288, p.6]；[doi:10.3390/ph19020288, p.17]；[doi:10.3390/ph19020288, p.18]；[doi:10.3390/ph19020288, p.20]
- **method：** 作者将 selected VCX sequences 克隆到 Trx-His fusion，采用 T7 Shuffle E. coli、Ni-IMAC 和 24/96-well high-throughput 流程表达纯化，用于快速 triage hits。
  - 证据：[doi:10.3390/ph19020288, p.5]；[doi:10.3390/ph19020288, p.16]；[doi:10.3390/ph19020288, p.17]
- **method：** 对 DLL3 进一步采用 NNK-block screening，把连续 3 个氨基酸作为 block 做双 block 组合随机化，并用 enrichment heatmap 训练监督式 transformer regression model。
  - 证据：[doi:10.3390/ph19020288, p.9]；[doi:10.3390/ph19020288, p.10]；[doi:10.3390/ph19020288, p.11]；[doi:10.3390/ph19020288, p.19]
- **method：** SPR 用 Biacore S200 的单循环动力学测定 Trx-fusion 与 SPPS peptides 的 Kd，并用 disulfide reduction、LC-MS 和 HPLC 验证折叠与活性对应关系。
  - 证据：[doi:10.3390/ph19020288, p.7]；[doi:10.3390/ph19020288, p.8]；[doi:10.3390/ph19020288, p.19]；[doi:10.3390/ph19020288, p.20]
- **results：** VCX 的 predicted foldability 分布显著高于 DCP，median 0.8606 对 0.7028，Mann-Whitney U test 报告 p<<0.001。
  - 证据：[doi:10.3390/ph19020288, p.3]；[doi:10.3390/ph19020288, p.4]
- **results：** UMAP 显示 VCX 在 sequence space 中形成单一而连通的 diffuse cluster，而 DCP 更 fragmented，说明 VCX 覆盖更连续的序列区域。
  - 证据：[doi:10.3390/ph19020288, p.4]；[doi:10.3390/ph19020288, p.5]
- **results：** 四个 target 都筛到了 positive binders；P2X7R hits 达到 21 nM–2 µM，IL33 为 213 nM–34 µM，DLL3 为 6.6–185 µM，CD47 为 1–555 µM。
  - 证据：[doi:10.3390/ph19020288, p.7]；[doi:10.3390/ph19020288, p.8]
- **results：** Trx-fusion 与 SPPS peptide 的 Kd 相关性较强（R=0.711），且 TCEP 破坏 disulfide 后 IL-33 binding 几乎消失，说明折叠结构对活性关键。
  - 证据：[doi:10.3390/ph19020288, p.7]；[doi:10.3390/ph19020288, p.8]
- **results：** NNK-trained model 的 Spearman ρ=0.57，优于 VCX-trained model 的 ρ=0.33；最终两条 DLL3 lead 达到 6.7 nM 和 12.6 nM，并实现最高约 500-fold affinity improvement。
  - 证据：[doi:10.3390/ph19020288, p.10]；[doi:10.3390/ph19020288, p.12]；[doi:10.3390/ph19020288, p.13]

## 页码证据

- [doi:10.3390/ph19020288, p.1]
- [doi:10.3390/ph19020288, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
