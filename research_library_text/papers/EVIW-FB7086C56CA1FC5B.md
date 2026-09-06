# Improving deep learning protein monomer and complex structure prediction using DeepMSA2 with huge metagenomics data

- **论文 ID：** `EVIW-FB7086C56CA1FC5B`
- **期刊 / 来源：** Nat Methods
- **发表时间：** 2024 Jan 2
- **DOI：** [10.1038/s41592-023-02130-4](https://doi.org/10.1038/s41592-023-02130-4)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `结构预测` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 DeepMSA2/DMFold/DMFold-Multimer：用多路迭代搜索、MSA 评分与多链配对/拼接/选择，在不重训 AlphaFold2/AlphaFold2-Multimer 权重的前提下，显著提升单体与复合物结构预测，并公开相关数据库与模型。

## 创新边界

`创新主要在输入 MSA 的构建、配对和排序，以及数据库扩展；底层 AlphaFold2 与 AlphaFold2-Multimer 模型参数保持不变。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何借助超大规模基因组与宏基因组序列库，构建更深、更均衡、可自动筛选的 MSA，以提升蛋白单体与多链复合物的结构预测质量，尤其是对低同源、难折叠目标的预测效果。

## 方法

- 多数据库迭代profile/MSA construction与structure predictor输入。

## 数据与基准

- 大规模metagenomics sequence DB及CASP/complex benchmarks。

## 比较基线

- DeepMSA/HHblits/JackHMMER。

## 结果证据

- 论文报告结构预测改善；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 搜索成本/数据库bias；末3页图像无文本层。

## 仍未知

- 独立于 CASP 与 human proteome 之外的数据集上，增益幅度是否稳定仍未充分展示。
- heteromer 的 species-based linking 在缺少 UniProt 注释的 metagenomic 序列上效果上限不明。
- 公开下载页是否包含完整可复现环境、权重版本与许可证边界，冻结页未完全说明。
- human proteome 新模型的绝对正确率仍需更多实验结构继续检验。

## Pi 结构化证据摘录

- **baseline：** 单体对照主要是 BLAST、HHblits、HMMER、MMseqs2、PSIBLAST，以及 AlphaFold2 本身；作者还构造了去掉 in-house metagenome 数据库的 DMFold-noh 作为消融基线。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.2]；[doi:10.1038/s41592-023-02130-4, p.3]
- **baseline：** 多聚体主对照是 AlphaFold2-Multimer，并进一步比较了公开的 March-2022 v.2.2.0 server 版本 NBIS-AF2-multimer。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.6]；[doi:10.1038/s41592-023-02130-4, p.8]
- **baseline：** 作者还把仅用 genome+Mgnify+BFD 的版本与加入 in-house metagenomics 库的完整版本区分开，用来拆分算法增益与数据库增益。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.6]
- **data：** 单体基准来自 CASP13-15 的 293 个 domain，其中包含 132 个 FM 与 155 个 TBM；作者分别按 CASP13、CASP14、CASP15 汇总这些目标。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.12]
- **data：** 复合体基准来自 CASP13 和 CASP14 的 54 个 complex targets，其中 14 个为 heteromer、40 个为 homomer；同源复合体以 A2/A3/A4/A8 等 stoichiometry 表示。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.12]
- **data：** 人类蛋白组部分先从 AlphaFold2 DB 中筛出约 6,757 个低置信度蛋白，再选择长度小于 800 aa 的 5,042 个目标交由 DMFold 重建。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.12]
- **data：** 论文还公开了用于分析的 CASP benchmark 数据、5,042 个 human proteome 重建结果，以及相关的第三方和 in-house sequence databases。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.15]
- **declared_resources：** 公开资源包括 DeepMSA2/DeepMSA2-Multimer 与 DMFold/DMFold-Multimer 的在线服务、standalone package 以及 Zenodo 归档下载。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.15]
- **declared_resources：** 第三方数据库包括 Uniclust30/UniRef30、Uniref90、BFD、Metaclust 和 MGnify；作者还构建了 TaraDB、MetaSourceDB 和 JGIclust，合计约 35.6 billion 条非冗余序列。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.12]；[doi:10.1038/s41592-023-02130-4, p.13]
- **declared_resources：** CASP benchmark 数据与 5,042 个 human proteome 预测结果被公开；训练还使用了 XSEDE 计算资源。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.15]
- **limitations：** 异源复合体上的提升较小，因为当前 sequence linking 依赖 UniProt species annotation，而 metagenomic 序列缺少该注释，导致这部分信息无法充分利用。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.7]；[doi:10.1038/s41592-023-02130-4, p.10]
- **limitations：** DMFold-Multimer 需要先验的 stoichiometry 信息，作者明确指出这会限制方法的实际应用范围。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.10]
- **limitations：** 作者也承认，human proteome 新模型的绝对质量仍需等待更多实验结构出现后继续验证。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.5]；[doi:10.1038/s41592-023-02130-4, p.10]
- **method：** DeepMSA2-Monomer 先用 dMSA、qMSA、mMSA 三路迭代搜索生成最多 10 个候选 MSA，再用简化版 AlphaFold2 按预测模型的 pLDDT 对这些 MSA 排序并返回最佳结果。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.2]；[doi:10.1038/s41592-023-02130-4, p.12]；[doi:10.1038/s41592-023-02130-4, p.13]；[doi:10.1038/s41592-023-02130-4, p.14]
- **method：** 单体搜索覆盖 Uniclust30/UniRef30、UniRef90、Metaclust、BFD、Mgnify，以及 TaraDB、MetaSourceDB、JGIclust 等宏基因组库；当 MSA 的 Neff 超过 128 时会停止继续扩展。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.12]；[doi:10.1038/s41592-023-02130-4, p.13]
- **method：** DeepMSA2-Multimer 先为每条链保留最多 10 个单体 MSA，再按同源/异源复合体规则进行配对、species-based linking 和拼接，最后用 M-score 综合 Neff 与链级 pLDDT 筛选 MSA，并交给 AlphaFold2-Multimer 生成与排序模型。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.2]；[doi:10.1038/s41592-023-02130-4, p.14]
- **method：** 作者明确说明 DMFold 与 DMFold-Multimer 复用预训练的 AlphaFold2/AlphaFold2-Multimer，不重新训练网络，只替换输入的 MSA。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.14]
- **results：** 在 293 个 monomer domain 上，DeepMSA2 在模板识别 TM-score、Top-L long-range contact precision 和 Top 5L long-range distance MAE 三项指标上都优于 BLAST、HHblits、HMMER、MMseqs2 和 PSIBLAST。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.2]
- **results：** 在 132 个 FM monomer domain 上，DMFold 有 63% 的案例 TM-score 高于 AlphaFold2，平均 TM-score 为 0.821，对比 AlphaFold2 的 0.781；在更难的子集上差距更大。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.2]
- **results：** 在人类蛋白组 5,042 个低置信度目标中，DMFold 的平均 pLDDT 为 0.663，比 AlphaFold2 DB 高 11%，并让 1,934 个蛋白达到 pLDDT ≥ 0.7。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.4]；[doi:10.1038/s41592-023-02130-4, p.5]
- **results：** 在 54 个复合体上，DMFold-Multimer 的平均 TM-score 为 0.834，高于 AlphaFold2-Multimer 的 0.743；CASP15 blind test 中其累计 Z-score 为 35.30，也显著高于 NBIS-AF2-multimer 的 12.27。
  - 证据：[doi:10.1038/s41592-023-02130-4, p.6]；[doi:10.1038/s41592-023-02130-4, p.8]

## 页码证据

- [doi:10.1038/s41592-023-02130-4, p.1]
- [doi:10.1038/s41592-023-02130-4, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
