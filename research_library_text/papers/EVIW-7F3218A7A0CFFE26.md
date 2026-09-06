# BBB-PEP-prediction: improved computational model for identification of blood–brain barrier peptides using blending position relative composition specific features and ensemble modeling

- **论文 ID：** `EVIW-7F3218A7A0CFFE26`
- **期刊 / 来源：** J Cheminform
- **发表时间：** 2023 Nov 18
- **DOI：** [10.1186/s13321-023-00773-1](https://doi.org/10.1186/s13321-023-00773-1)
- **范围标签：** `待 Pi 解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析待处理

## 作者主张的创新点

论文提出结合位置相对组成特征与blending集成的BBB-PEP-Prediction。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

从序列识别可能穿越血脑屏障的肽。

## 方法

- 构造位置/统计矩特征，训练bagging、boosting、stacking和blending集成分类器。

## 数据与基准

- 公开BBB肽基准数据集及交叉验证/独立测试。

## 比较基线

- RF、ExtraTrees、boosting、stacking及既有BBB肽预测器。

## 结果证据

- 论文报告blending模型优于比较方法；仅为序列分类。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 数据集小、负样本和相似序列可能影响估计，缺少穿透实验。

## 仍未知

- 不同物种、给药途径和修饰肽的泛化未知。

## 页码证据

- [doi:10.1186/s13321-023-00773-1, p.10]
- [doi:10.1186/s13321-023-00773-1, p.16]
- [doi:10.1186/s13321-023-00773-1, p.1]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
