# CircSI-SSL: circRNA-binding site identification based on self-supervised learning

- **论文 ID：** `EVIW-886EEFF6D7C82C08`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2024 Jan 5
- **DOI：** [10.1093/bioinformatics/btae004](https://doi.org/10.1093/bioinformatics/btae004)
- **范围标签：** `待 Pi 解析` / `可迁移方法` / `论文声明资源` / `数据集/基准`
- **Pi 状态：** 已专家复核，等待 Pi 解析

## 作者主张的创新点

论文声称CircSI-SSL用RNA_Transformer做跨视图序列预测预任务，再以少量真实标签fine-tune。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

在少量标注下利用多视图自监督学习circRNA-RBP结合位点。

## 方法

- 组合多种序列编码为views，通过Transformer预测另一视图以最大化互信息，最终做位置/片段结合分类。

## 数据与基准

- 六个circRNA benchmark和六个linear RNA迁移集；极端1:9训练/测试设置。

## 比较基线

- 监督CNN/RNN/Transformer和单视图模型，另有标注比例/视图消融。

## 结果证据

- 论文报告在六个circRNA集优于既有方法，并无需修改网络即可迁移到linear RNA；均为计算预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 自监督视图来自同一序列且可能共享偏差；数据集小、负样本构造和跨RBP泛化仍有限。

## 仍未知

- 跨蛋白/跨细胞系外部验证和许可未复核。

## 页码证据

- [doi:10.1093/bioinformatics/btae004, p.1]
- [doi:10.1093/bioinformatics/btae004, p.2]
- [doi:10.1093/bioinformatics/btae004, p.5]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
