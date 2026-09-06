# ACP-CapsPred: an explainable computational framework for identification and functional prediction of anticancer peptides based on capsule network

- **论文 ID：** `EVIW-9740ACD6DFDD26CD`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2024 Sep 18
- **DOI：** [10.1093/bib/bbae460](https://doi.org/10.1093/bib/bbae460)
- **范围标签：** `待 Pi 解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析待处理

## 作者主张的创新点

论文提出两阶段 ACP-CapsPred，将蛋白语言模型、进化/理化特征和胶囊网络结合用于 ACP 与癌种功能预测。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

同时识别抗癌肽并预测其针对不同癌种的功能标签，同时提高序列模型可解释性。

## 方法

- 第一阶段区分 ACP/非 ACP，第二阶段做五类癌症的多标签功能预测；用截断实验和 SHAP 分析残基贡献。

## 数据与基准

- 两个 ACP 识别基准集，以及人工整理的五癌种 ACP 功能数据。

## 比较基线

- 传统 ML、CNN/RNN 类 ACP 工具和已有多标签 ACP 方法。

## 结果证据

- 论文报告第一阶段两数据集 ACC 80.25%/95.71%、F1 79.86%/95.90%，并报告多标签任务优于比较方法；均为计算评估。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 数据规模、负样本构造和潜在同源泄漏限制外推；解释图是模型归因而非抗癌机制实验。

## 仍未知

- 跨实验平台外部验证、序列分簇切分及候选肽真实选择性仍未知。

## 页码证据

- [doi:10.1093/bib/bbae460, p.12]
- [doi:10.1093/bib/bbae460, p.1]
- [doi:10.1093/bib/bbae460, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
