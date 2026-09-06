# AutoPeptideML: a study on how to build more trustworthy peptide bioactivity predictors

- **论文 ID：** `EVIW-BE76B197C5D200BF`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2024 Sep 18
- **DOI：** [10.1093/bioinformatics/btae555](https://doi.org/10.1093/bioinformatics/btae555)
- **范围标签：** `待 Pi 解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析待处理

## 作者主张的创新点

论文声称AutoPeptideML提供多活性数据库抽取负肽、同源校正拆分、表示/模型优化和透明报告的端到端AutoML。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

自动化肽活性分类器的数据构建/拆分，同时减少负样本混杂和同源泄漏导致的性能虚高。

## 方法

- 从具有其他已知活性的肽中采负样本，按同源性构建独立测试；比较手工特征、PLM与AutoML模型，并自动输出评估。

## 数据与基准

- 多个肽生物活性二分类数据集和不同负样本/随机/同源拆分版本。

## 比较基线

- 随机序列负样本、一般bioactive负样本、随机拆分/同源拆分及不同表示模型。

## 结果证据

- 论文证明无同源校正会高估性能，新负样本使任务更难但更可信；不是新肽活性实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 只系统研究二分类；相似性度量与阈值选择仍开放，PLM scaling/transfer对肽任务未解决。

## 仍未知

- 非二分类任务和不同同源阈值下结论未知。

## 页码证据

- [doi:10.1093/bioinformatics/btae555, p.10]
- [doi:10.1093/bioinformatics/btae555, p.1]
- [doi:10.1093/bioinformatics/btae555, p.2]
- [doi:10.1093/bioinformatics/btae555, p.5]
- [doi:10.1093/bioinformatics/btae555, p.6]
- [doi:10.1093/bioinformatics/btae555, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
