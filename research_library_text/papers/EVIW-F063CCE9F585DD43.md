# The Accurate Prediction of Antibody Deamidations by Combining High-Throughput Automated Peptide Mapping and Protein Language Model-Based Deep Learning

- **论文 ID：** `EVIW-F063CCE9F585DD43`
- **期刊 / 来源：** Antibodies (Basel)
- **发表时间：** 2024 Sep 10
- **DOI：** [10.3390/antib13030074](https://doi.org/10.3390/antib13030074)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称建立了一个包含 2285 个 site-specific deamidation 实例的抗体数据集，并提出将 ESM-2 全序列 embeddings 与局部序列窗口特征结合的 chimeric deep learning model；该模型可仅用序列完成 deamidation 热点分类，同时还能对 2/4/8 周的 deamidation extents 做定量预测，并用于候选抗体的高通量 triage。

## 创新边界

`可确认的新意主要是 ESM-2 global embeddings 与 31-aa local window/LSTM 特征的拼接，以及自动化 peptide mapping 生成训练数据；但 'state-of-the-art'、'first' 和更广泛的跨任务可迁移性都未被冻结证据独立验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在抗体药物研发中，如何在早期仅依赖序列信息更准确地识别 N/Q 位点 deamidation 风险，并进一步估计未来时点的 deamidation extent，以减少昂贵且耗时的 peptide mapping 与筛选负担。

## 方法

- 高通量LC-MS肽图量化脱酰胺，模型将ESM-2表示与局部序列窗口融合，同时预测位点倾向和程度。

## 数据与基准

- 由多种抗体模态构成的2285条/个脱酰胺专用样本记录，并包含加速应力和时间零点测量。

## 比较基线

- 传统序列特征模型、结构/手工特征方法及模型组件消融。

## 结果证据

- 论文声称达到先进表现且仅需序列输入；这是以实验肽图标签训练的计算预测，不是对所有抗体稳定性的实验替代。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 作者指出模型可解释性有限；天冬氨酸异构化因无质量变化而难以用同一高通量流程扩展。

## 仍未知

- 未见独立 prior-art 证据来验证作者关于 'first' 或 'state-of-the-art' 的更强新颖性断言。
- 训练数据主要来自 45 个 in-house antibodies，跨机构、跨平台与跨序列家族的泛化仍不清楚。
- 回归任务只验证了 2/4/8 周三个时间点，未说明更长时间窗或真实生产场景的表现。

## Pi 结构化证据摘录

- **baseline：** 仅 local sequence 的 MCC 为 0.673±0.030，仅 global embeddings 的 MCC 为 0.731±0.027；二者都低于 chimeric model 的 0.787±0.038。
  - 证据：[doi:10.3390/antib13030074, p.8]；[doi:10.3390/antib13030074, p.11]
- **baseline：** 与已发表方法相比，decision tree、random forest、NGOME、以及 NG/NS/NN motif 规则的 MCC 分别为 0.733、0.757、0.705、0.704，而 chimeric model 为 0.775。
  - 证据：[doi:10.3390/antib13030074, p.12]；[doi:10.3390/antib13030074, p.13]
- **baseline：** 经典 NG/NS/NN motif 规则虽然 recall 高达 0.944，但 precision 只有 0.586，说明其存在明显过预测。
  - 证据：[doi:10.3390/antib13030074, p.13]
- **data：** 训练集来自 45 个 in-house antibodies，共 2285 个 labeled deamidation instances，其中 276 个为 hot spots、2009 个为 inactive；作者用 t0 到 t1week 或 t1week 到 t2week 的增量超过 1.0% 作为 active 标记阈值。
  - 证据：[doi:10.3390/antib13030074, p.6]；[doi:10.3390/antib13030074, p.7]
- **data：** 独立测试集包含 6 个 antibodies（5 个 in-house + NISTmAb），覆盖 312 个 potential deamidation sites，其中 36 个 active、276 个 inactive。
  - 证据：[doi:10.3390/antib13030074, p.11]；[doi:10.3390/antib13030074, p.12]
- **data：** 作者还做了一个 86 clones 的 pilot screening，直接以 FASTA 序列推断 heavy-chain 的 deamidation liability，并筛出一组低风险候选。
  - 证据：[doi:10.3390/antib13030074, p.14]；[doi:10.3390/antib13030074, p.15]
- **declared_resources：** 实验样本来自 Bristol Myers Squibb 的 CHO 生产抗体，NISTmAb 来自 Sigma-Aldrich；核心仪器包括 Lynx liquid handling robot、BioShake Q1、Vanquish UHPLC 和 Exploris 480。
  - 证据：[doi:10.3390/antib13030074, p.3]；[doi:10.3390/antib13030074, p.4]；[doi:10.3390/antib13030074, p.5]
- **declared_resources：** 模型侧明确使用 ESM-2 的 esm2_t33_650m_UR50D（33 layers, 650M parameters）作为 global embedding 提取器，并以 DNN/LSTM/FC 作为下游头。
  - 证据：[doi:10.3390/antib13030074, p.7]；[doi:10.3390/antib13030074, p.8]；[doi:10.3390/antib13030074, p.9]；[doi:10.3390/antib13030074, p.10]
- **declared_resources：** Data Availability 仅说明补充材料提供 model construct 和 layer hyperparameters，未见公开代码仓库链接。
  - 证据：[doi:10.3390/antib13030074, p.18]
- **limitations：** 作者明确承认 pLM/LLM 的黑盒性较强，难以清楚解释究竟哪些 features 驱动了 deamidation 判断。
  - 证据：[doi:10.3390/antib13030074, p.16]；[doi:10.3390/antib13030074, p.17]
- **limitations：** 数据规模仍偏小且类别极不平衡，训练集中只有 276 个阳性与 2009 个阴性，作者也指出需要更大的数据集进一步提升性能。
  - 证据：[doi:10.3390/antib13030074, p.7]；[doi:10.3390/antib13030074, p.11]；[doi:10.3390/antib13030074, p.17]
- **limitations：** 实验覆盖存在盲点，例如短 tryptic peptide 造成某些位点丢失 LC-MS 覆盖，需要额外 LysC 验证；此外，窗口长度超过 61 未探索，部分原因是计算负担。
  - 证据：[doi:10.3390/antib13030074, p.9]；[doi:10.3390/antib13030074, p.12]；[doi:10.3390/antib13030074, p.13]
- **method：** 先将 51 个抗体在 pH 8.0、40°C 条件下强制应激至 8 周，并在 0/1/2/4/8 周采样，再通过高通量自动化 peptide mapping 与 LC-MS/MS 获取位点级 deamidation 读数。
  - 证据：[doi:10.3390/antib13030074, p.3]；[doi:10.3390/antib13030074, p.4]；[doi:10.3390/antib13030074, p.5]；[doi:10.3390/antib13030074, p.6]
- **method：** 自动化前处理由 Lynx liquid handling robotic system 完成，流程包括浓度归一化、变性、二硫键还原、半胱氨酸烷基化、microdialysis buffer exchange、trypsin digestion、quenching 和冷却存放。
  - 证据：[doi:10.3390/antib13030074, p.4]
- **method：** 模型以 ESM-2（esm2_t33_650m_UR50D）提取 residue-level embeddings，再与 31-aa local window 的 supervised word embedding 和 bi-directional LSTM 特征拼接，经 FC DNN 做分类；回归头进一步输出 2/4/8 周的 quantitative deamidation extent。
  - 证据：[doi:10.3390/antib13030074, p.7]；[doi:10.3390/antib13030074, p.8]；[doi:10.3390/antib13030074, p.9]；[doi:10.3390/antib13030074, p.10]；[doi:10.3390/antib13030074, p.13]
- **results：** 五折交叉验证中，local + global 的 chimeric model 达到 accuracy 0.956±0.014、precision 0.835±0.059、recall 0.790±0.036、MCC 0.787±0.038，优于仅用 local sequence 或仅用 global embeddings 的模型。
  - 证据：[doi:10.3390/antib13030074, p.8]；[doi:10.3390/antib13030074, p.11]
- **results：** 独立测试集上，chimeric model 的 accuracy 为 0.955、precision 0.823、recall 0.778、MCC 0.775、specificity 0.978，ROC AUC 达到 0.986。
  - 证据：[doi:10.3390/antib13030074, p.11]；[doi:10.3390/antib13030074, p.12]；[doi:10.3390/antib13030074, p.13]
- **results：** 定量回归部分表明模型可对 2/4/8 周 deamidation extents 做较好预测，并与 NISTmAb、Antibody-1、Antibody-2 的 peptide mapping 结果总体一致；其中 N73 还通过 LysC peptide mapping 被再次确认。
  - 证据：[doi:10.3390/antib13030074, p.13]；[doi:10.3390/antib13030074, p.14]

## 页码证据

- [doi:10.3390/antib13030074, p.16]
- [doi:10.3390/antib13030074, p.1]
- [doi:10.3390/antib13030074, p.5]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
