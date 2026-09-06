# MoleMCL: a multi-level contrastive learning framework for molecular pre-training

- **论文 ID：** `EVIW-1E03BAE643FFD505`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2024 Mar 26
- **DOI：** [10.1093/bioinformatics/btae164](https://doi.org/10.1093/bioinformatics/btae164)
- **范围标签：** `待 Pi 解析` / `可迁移方法` / `论文声明资源` / `数据集/基准`
- **Pi 状态：** 已专家复核，等待 Pi 解析

## 作者主张的创新点

论文声称MoleMCL结合节点attribute masking和gradient-compensated encoder参数扰动进行多层对比预训练。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

同时学习分子图结构与属性语义，并避免随机参数扰动造成不稳定正样本。

## 方法

- 节点级mask重构，图级对比原图与参数扰动编码；用下游监督梯度近似补偿扰动方向。

## 数据与基准

- 常用分子预训练语料与多个分子性质分类/回归benchmark。

## 比较基线

- GraphCL/JOAO/Mole-BERT/TMCL等自监督分子图预训练及组件消融。

## 结果证据

- 论文报告匹配或超过Mole-BERT、TMCL等SOTA；均为下游计算预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- gradient compensation仍依赖有限下游标签/任务，OOD泛化未充分验证；图2D表示缺少构象。

## 仍未知

- 预训练去重、scaffold拆分和许可未复核。

## 页码证据

- [doi:10.1093/bioinformatics/btae164, p.1]
- [doi:10.1093/bioinformatics/btae164, p.2]
- [doi:10.1093/bioinformatics/btae164, p.3]
- [doi:10.1093/bioinformatics/btae164, p.6]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
