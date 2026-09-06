# PTM-Mamba: a PTM-aware protein language model with bidirectional gated Mamba blocks

- **论文 ID：** `EVIW-5AD4D124DC0AC35A`
- **期刊 / 来源：** Nat Methods
- **发表时间：** 2025 Apr 10
- **DOI：** [10.1038/s41592-025-02656-9](https://doi.org/10.1038/s41592-025-02656-9)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 PTM-Mamba：在 Mamba backbone 上加入双向 gated Mamba blocks，并将 PTM tokens 与 ESM-2-650M embeddings 做门控融合，使模型能够同时表示 wild-type 与 PTM sequences，并服务于 PTM 相关下游任务与零样本发现。

## 创新边界

`新意主要在 PTM-aware 表示学习与下游预测，不是直接生成或优化新的蛋白/肽候选。`。这不是全球首创性检索或独立复现结论。

## 研究问题

现有 protein language models 虽能编码蛋白序列性质，但在训练与推理中基本不显式表示 PTM residues/proteoforms，因而难以刻画 PTM 对结构、功能、相互作用以及疾病/药物相关性的影响。

## 方法

- 在通用序列表示上加入双向state-space/Mamba block，以PTM-aware训练目标建模长程上下文。

## 数据与基准

- 79707条modified sequences，来自Swiss-Prot 311350条实验PTM记录。

## 比较基线

- ESM-2、ProtT5及其他PTM predictor。

## 结果证据

- 论文报告多项PTM benchmark和zero-shot PTM discovery优于比较模型；为计算预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 实验PTM注释不足，作者计划整合MS数据库；训练标注偏差限制新PTM泛化。

## 仍未知

- 冻结证据未提供独立 prior-art，因此无法确认全球新颖性。
- 正文未独立验证代码与权重是否能无误复现全部 benchmark 数值。
- zero-shot PTM discovery 只展示少量示例，泛化边界未量化。

## Pi 结构化证据摘录

- **baseline：** 作者将 PTM-Transformer 作为直接 baseline，并报告 PTM-Mamba 在 training accuracy 上收敛更快。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.2]
- **baseline：** 比较基线覆盖 one-hot、one-hot(+PTM)、ESM-2-650M、ESM-2-3B、PTM-Transformer，以及在部分任务中加入的 PTM-SaProt。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.3]；[doi:10.1038/s41592-025-02656-9, p.4]
- **data：** 训练语料来自 UniProt Swiss-Prot 中 311,350 条 experimentally validated PTM records，映射后得到 79,707 条 PTM sequences。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.1]
- **data：** 磷酸化 site 数据来自 ProteinBERT benchmark，原始来源为 PhosphoSitePlus，并过滤到 256–512 aa，划分为 15,588/1,707/3,106 的 train/val/test 集。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.6]
- **data：** 疾病关联、druggability 与 PTM-PPI effect 分别来自 dbPTM 和 PTMint；其中 PTMint 包含 2,477 个 nonredundant PTM sites、1,169 proteins 与 2,371 protein-protein pairs。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.3]；[doi:10.1038/s41592-025-02656-9, p.6]
- **data：** 词表在 20 个标准 amino acid tokens 之外新增 25 个 UniProt PTM tokens，包括 phosphoserine、phosphothreonine、N6-acetyllysine、sulfotyrosine 和多种 glyco/lipid 修饰。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.6]
- **declared_resources：** 训练与 benchmark 在 Nvidia 8xA100 DGX system 上完成，作者注明共享 VRAM 为 640 GB。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.6]
- **declared_resources：** 数据可通过 Zenodo DOI 10.5281/zenodo.14794992 获取。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.6]
- **declared_resources：** PTM-Mamba、PTM-Transformer、PTM-SaProt、baseline weights、training code 与 preprocessing scripts 分别公开在 Hugging Face 和 GitHub。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.6]
- **limitations：** 作者明确指出该模型主要优化于带 PTM tokens 的 modified sequences，而不是 wild-type-only benchmarks。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.4]
- **limitations：** 作者承认 experimentally validated PTM annotations 数量仍有限，并计划用 mass spectrometry-based PTM databases 扩充训练数据。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.5]
- **limitations：** 结构预测与 PTM-specific binders design 被列为 future work，说明这些能力尚未在本文中实现。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.5]
- **method：** 模型以 Mamba 为骨架，加入 forward/backward 两路处理形成 bidirectional Mamba block，再用全连接层融合两路输出并保留 residual 贡献。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.1]
- **method：** PTM-Mamba 将 wild-type amino acids 送入 ESM-2-650M 获取 embedding，PTM tokens 则由 PTM-Mamba 自身 embedding 层处理，两路表示通过 sigmoid gate 融合。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.2]
- **method：** 训练采用调整后的 masked language modeling：80% 概率做标准 15% masking，20% 概率 mask 所有 PTM tokens 并随机 mask 15% wild-type tokens。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.6]
- **method：** 下游 benchmark 通过预训练 embeddings 接分类头微调，并对每个模型重复训练 n=5，使用 accuracy、precision、recall、F1、MCC、AUROC 和 AUPRC 评估。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.3]；[doi:10.1038/s41592-025-02656-9, p.6]
- **results：** t-SNE 显示 wild-type 与对应 PTM sequence 的 embedding 彼此靠近，而 PTM token embeddings 呈现一定的 class-specific 聚类与更高空间多样性。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.4]
- **results：** 在 phosphorylation site prediction 与 non-histone acetylation site prediction 上，PTM-Mamba 在各项指标上与 ESM-2-650M、ESM-2-3B、PTM-Transformer 和 one-hot embeddings 表现相近。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.4]
- **results：** 在 disease association 与 druggability 预测上，PTM-Mamba 相比 baseline 表现更强，并常在 F1 和 MCC 等指标上占优。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.3]
- **results：** 在 PTM 对 PPI 的影响任务上，PTM-Mamba 在所有模型中取得最高指标，包括 PTM-Transformer 与 PTM-SaProt。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.3]
- **results：** zero-shot PTM discovery 给出了具体示例，例如对 Q02261 的 serine 预测为 phosphoserine、对 Q4L7X2 的 cysteine 预测为 S-diacylglycerol cysteine。
  - 证据：[doi:10.1038/s41592-025-02656-9, p.4]

## 页码证据

- [doi:10.1038/s41592-025-02656-9, p.1]
- [doi:10.1038/s41592-025-02656-9, p.3]
- [doi:10.1038/s41592-025-02656-9, p.4]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
