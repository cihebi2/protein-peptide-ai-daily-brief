# Prediction of protein secondary structure by the improved TCN-BiLSTM-MHA model with knowledge distillation

- **论文 ID：** `EVIW-CFF211E7FC7B9340`
- **期刊 / 来源：** Sci Rep
- **发表时间：** 2024 Jul 17
- **DOI：** [10.1038/s41598-024-67403-0](https://doi.org/10.1038/s41598-024-67403-0)
- **范围标签：** `待 Pi 解析` / `可迁移方法` / `论文声明资源` / `语言模型` / `数据集/基准`
- **Pi 状态：** 已专家复核，等待 Pi 解析

## 作者主张的创新点

论文融合改进TCN、BiLSTM、multi-head attention和ProtT5 knowledge distillation。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

以轻量student提高三态/八态蛋白secondary structure预测。

## 方法

- teacher PLM提供soft targets/表示，student以TCN捕获局部、BiLSTM建模双向上下文、MHA融合。

## 数据与基准

- 多个secondary-structure benchmark。

## 比较基线

- 单TCN/BiLSTM/MHA、无蒸馏和既有predictor。

## 结果证据

- 论文报告多数据集性能提升；为序列到二级结构计算预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- teacher-student能力差异和数据规模限制学习，模型解释性仍弱。

## 仍未知

- 严格去同源外部集和低复杂序列表现未知。

## 页码证据

- [doi:10.1038/s41598-024-67403-0, p.18]
- [doi:10.1038/s41598-024-67403-0, p.1]
- [doi:10.1038/s41598-024-67403-0, p.3]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
