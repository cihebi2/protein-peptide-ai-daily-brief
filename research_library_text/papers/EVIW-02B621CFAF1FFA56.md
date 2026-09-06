# Predicting blood–brain barrier permeability of molecules with a large language model and machine learning

- **论文 ID：** `EVIW-02B621CFAF1FFA56`
- **期刊 / 来源：** Sci Rep
- **发表时间：** 2024 Jul 9
- **DOI：** [10.1038/s41598-024-66897-y](https://doi.org/10.1038/s41598-024-66897-y)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称提出了一个以 MegaMolBART SMILES embedding 结合 XGBoost 为核心的 BBB permeability 预测流程，并辅以 3D human BBB spheroids 与 LC-MS/MS 对 NPRL 化合物进行体外验证。

## 创新边界

`主要是现成模型与数据的迁移组合，不是 de novo 分子生成或候选物优化。`。这不是全球首创性检索或独立复现结论。

## 研究问题

预测小分子是否能够穿过 blood–brain barrier (BBB)，并比较基于 SMILES 的 Transformer 表征是否优于 Morgan fingerprints 和传统分子描述符。

## 方法

- MegaMolBART编码SMILES，XGBoost完成BBB+/BBB-分类，并以多来源BBB数据库训练和留出测试。

## 数据与基准

- 包括B3DB等多个BBB数据库；B3DB含7807个化合物，其中4956个BBB+、2851个BBB-，另有部分LogBB值。

## 比较基线

- 传统分子描述符/机器学习模型及不同数据组合。

## 结果证据

- 论文报告留出测试AUROC 0.88，并称由实验室对部分化合物进行体外验证；不能由此推断全部预测或体内脑暴露。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 数据库标签和测定条件异质，随机留出可能高估骨架外推；体外通透性不等同于体内BBB暴露。

## 仍未知

- 论文未给出明确的论文专属代码仓库或冻结提交。
- Supplementary materials 未在本次页内证据中展开，部分超参数与补充指标仍不完整。
- 外部独立前瞻性验证与阈值校准过程在主文中说明有限。

## Pi 结构化证据摘录

- **baseline：** Morgan/Circular fingerprints + XGBoost 被作为直接 baseline，与 MegaMolBART embeddings 做对照。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.1]；[doi:10.1038/s41598-024-66897-y, p.2]；[doi:10.1038/s41598-024-66897-y, p.3]；[doi:10.1038/s41598-024-66897-y, p.6]
- **baseline：** 文中还把 LightBBB 的 LightGBM 与 DeePred-BBB 的 DNN 作为外部文献 baseline 进行比较。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.4]
- **baseline：** 传统 physicochemical descriptors（Dragon、PaDEL）以及 SVM、kNN、RF、naive Bayes 等方法被用作历史基线背景。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.2]；[doi:10.1038/s41598-024-66897-y, p.4]
- **data：** CMUH 预处理后包含 105 个 BBB+ 与 2394 个 BBB−；B3DB 包含 4956 个 BBB+ 与 2851 个 BBB−。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.6]
- **data：** 回归任务只使用了 B3DB 中 1058 个带 LogBB 的样本，作者把 LogBB 作为 BBB 穿透性的连续标签来源。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.2]；[doi:10.1038/s41598-024-66897-y, p.6]
- **data：** 体外验证样本由 21 个预测 BBB-permeable 的 NPRL 化合物和 5 个预测 BBB-impermeable 的 NPRL 化合物组成，并设置 TMZ 与 ferulic acid 作为阳性与阴性对照。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.1]；[doi:10.1038/s41598-024-66897-y, p.3]；[doi:10.1038/s41598-024-66897-y, p.5]
- **data：** 作者声明本文中生成或分析的全部数据都已包含在已发表文章里。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.7]
- **declared_resources：** MegaMolBART 预训练模型来自 NVIDIA NGC；作者说明其在 64 V100 GPUs 上用 ZINC-15 训练，后续又在 TWS/Taiwania-2 上训练 large MegaMolBART。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.6]；[doi:10.1038/s41598-024-66897-y, p.8]
- **declared_resources：** 体外实验使用 ScienCell 提供的 3D-BBB spheroids，组成包括 human brain microvascular endothelial cells、brain vascular pericytes 和 astrocytes。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.6]
- **declared_resources：** LC-MS/MS 采用 UHPLC Ultimate 3000 与 maXis impact QTOF 平台完成。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.6]
- **declared_resources：** 实验与数据分析得到 CMUH Proteomics Core Laboratory 和 Medical Research Core Facilities Center 的支持。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.8]
- **declared_resources：** 作者把 B3DB 作为开源 BBB 数据库使用，并在正文中给出其 GitHub URL。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.6]
- **limitations：** 训练曲线在约 400 epochs 后出现 overfitting，作者认为小数据集限制了预训练模型优势。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.2]
- **limitations：** CMUH 与 B3DB 的分布偏移明显，模型在 B3DB 上训练后应用到 CMUH 时 accuracy 约下降 50%。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.3]；[doi:10.1038/s41598-024-66897-y, p.6]
- **limitations：** 只有 1058 个样本带 LogBB，回归监督信号偏少，作者也明确说需要更多 LogBB 数据和更多 pre-training 才能继续提升表现。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.2]；[doi:10.1038/s41598-024-66897-y, p.5]；[doi:10.1038/s41598-024-66897-y, p.6]
- **method：** 将 CMUH-NPRL 与 B3DB 的 SMILES 规范化后构建 BBB+ / BBB− 数据集，用 MegaMolBART 作为 SMILES encoder 生成 embedding，再接 XGBoost classifier/regressor；同时以 Morgan fingerprints 作为直接 baseline。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.1]；[doi:10.1038/s41598-024-66897-y, p.2]；[doi:10.1038/s41598-024-66897-y, p.6]
- **method：** 使用 80%/10%/10% 的训练、验证、测试切分评估模型，并把 LightBBB 与 DeePred-BBB 的 tenfold cross-validation 结果作为横向比较对象。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.3]；[doi:10.1038/s41598-024-66897-y, p.4]；[doi:10.1038/s41598-024-66897-y, p.6]
- **method：** 通过 t-SNE 检查 CMUH 与 B3DB embedding 的分布差异，发现两类数据相距较远，因此后续改为混合两库联合训练。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.2]；[doi:10.1038/s41598-024-66897-y, p.3]
- **method：** 在 3D human BBB spheroids 上开展 LC-MS/MS，比较 TMZ、ferulic acid 以及随机挑选的 21 个 BBB+ 和 5 个 BBB− NPRL compounds 的通透性。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.3]；[doi:10.1038/s41598-024-66897-y, p.4]；[doi:10.1038/s41598-024-66897-y, p.6]
- **results：** 在混合 CMUH+B3DB 的 80%/10%/10% 切分下，MegaMolBART + XGBoost 的 held-out test AUC 达到 0.88，整体优于 Morgan fingerprints baseline。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.1]；[doi:10.1038/s41598-024-66897-y, p.3]
- **results：** 与文中复现比较的外部模型相比，本文模型在 LightBBB 上得到 AUC 0.93，对照文献为 0.94；在 DeePred-BBB 上得到 0.96，对照文献为 0.99。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.4]
- **results：** LC-MS/MS 结果显示 TMZ 与 21 个 BBB+ NPRL compounds 能进入 human BBB spheroids，而 ferulic acid 与 5 个 BBB− compounds 未见进入。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.3]；[doi:10.1038/s41598-024-66897-y, p.4]；[doi:10.1038/s41598-024-66897-y, p.5]
- **results：** 作者还报告在部分 TWS embeddings + XGBoost 设置下 AUC/accuracy 可到约 0.90，但从 B3DB 外推到 CMUH 时性能会明显下降。
  - 证据：[doi:10.1038/s41598-024-66897-y, p.5]；[doi:10.1038/s41598-024-66897-y, p.6]

## 页码证据

- [doi:10.1038/s41598-024-66897-y, p.1]
- [doi:10.1038/s41598-024-66897-y, p.2]
- [doi:10.1038/s41598-024-66897-y, p.5]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
