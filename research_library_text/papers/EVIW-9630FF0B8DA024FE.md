# DL-PPI: a method on prediction of sequenced protein-protein interaction based on deep learning

- **论文 ID：** `EVIW-9630FF0B8DA024FE`
- **期刊 / 来源：** BMC Bioinformatics
- **发表时间：** 2023 Dec 14
- **DOI：** [10.1186/s12859-023-05594-5](https://doi.org/10.1186/s12859-023-05594-5)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出 DL-PPI：把 amino acid embedding、Inception V3、多层 GIN、self-attention 和改造 FRN 组合成端到端框架，用于序列式 PPI 多标签预测并提升未知蛋白泛化。

## 创新边界

`创新主要在模型结构与关系推理模块改造，不是新数据集、湿实验或候选蛋白设计流程。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何仅利用蛋白序列，在陌生/未知蛋白与跨数据集划分下，更稳健地预测 Protein-Protein Interaction (PPI) 及其多类关系。

## 方法

- sequence encoding与deep classifier。

## 数据与基准

- 公开PPI datasets。

## 比较基线

- 传统ML/深度PPI。

## 结果证据

- 论文报告超过baselines；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 负样本/同源拆分与无实验。

## 仍未知

- 未见独立 prior-art 证据，global novelty 无法验证。
- 未报告新的 wet-lab 实验。
- 代码仓库与数据声明已给出，但未核验可运行性。

## Pi 结构化证据摘录

- **baseline：** 主要对比基线是 DNN-PPI、PIPR、TAGPPI 与 GNN-PPI，其中 GNN-PPI 被作者称为 primary benchmark model。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.12]
- **baseline：** FRN 还与 NTN 做了模块级比较，作为关系推理基线。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.16]
- **data：** SHS148k 含 44,488 个 multi-label PPIs，SHS27k 含 7,624 个 multi-label PPIs，二者从 Homo sapiens 的 STRING 子集随机抽取且序列同一性低于 40%。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.5]
- **data：** STRING 数据集版本 10.5，含 593,397 PPIs，覆盖 activation、binding、catalysis、expression、inhibition、post-translational modification、reaction 七类相互作用。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.5]
- **data：** Yeast benchmark 含 2,497 proteins 与 11,188 PPIs，正例来自 DIP_20070219，负例由随机配对无交互证据的蛋白生成，序列来自 UniProt。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.5]
- **declared_resources：** 主要数据资源包括 STRING 10.5、SHS27k、SHS148k 与 Yeast benchmark。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.5]
- **declared_resources：** 数据可用性声明给出 cn.string-db.org 和 https://github.com/WuBoFu/DL-PPI.git；补充材料另有 precision/recall 对比。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.18]；[doi:10.1186/s12859-023-05594-5, p.19]
- **limitations：** 作者在引言中指出，现有深度学习 PPI 方法在更大、陌生的数据集上效果会下降，部分 GCN 在 unknown PPI datasets 上也有限。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.1]；[doi:10.1186/s12859-023-05594-5, p.3]；[doi:10.1186/s12859-023-05594-5, p.4]
- **limitations：** 论文未给出 wet-lab 验证，证据边界主要是公开数据集上的计算评测、generalization、消融与 GO/KEGG 富集。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.12]；[doi:10.1186/s12859-023-05594-5, p.15]；[doi:10.1186/s12859-023-05594-5, p.17]；[doi:10.1186/s12859-023-05594-5, p.18]
- **method：** DL-PPI 将蛋白建模为图节点、相互作用建模为边，并把 PPI 预测转化为 link prediction 加七类多标签分类任务。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.4]；[doi:10.1186/s12859-023-05594-5, p.5]；[doi:10.1186/s12859-023-05594-5, p.6]
- **method：** 每个 amino acid 的输入向量由 Skip-Gram 预训练的 3-mer 共现嵌入与基于电荷/疏水性的 7 类理化嵌入拼接而成，共 13 维。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.7]
- **method：** 蛋白节点特征通过 Inception V3 风格的多尺度卷积模块提取，使用 1、3、5 kernel 融合不同感受野。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.7]；[doi:10.1186/s12859-023-05594-5, p.8]
- **method：** 全局图表示用 GIN 聚合邻居节点，再通过 self-attention 重新加权关键蛋白特征。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.8]；[doi:10.1186/s12859-023-05594-5, p.9]
- **method：** FRN 在 NTN 基础上显式融合距离、方向和 cosine similarity，并以 Multi-task Binary Cross-Entropy 训练最终分类器。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.10]；[doi:10.1186/s12859-023-05594-5, p.11]
- **results：** 在 Table 1 的 micro-F1 比较中，DL-PPI 在 SHS27k/SHS148k/STRING 的 Random 划分分别达到 89.12/92.49/94.85，均高于 DNN-PPI、TAGPPI、PIPR 和 GNN-PPI。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.13]
- **results：** 在 BFS/DFS 划分下，DL-PPI 仍保持领先，分别在 SHS27k 达到 72.95/78.07，在 SHS148k 达到 68.87/85.45，在 STRING 达到 77.53/92.76。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.13]
- **results：** Yeast 表中，DL-PPI 报告 precision/recall/F1 为 97.90/97.93/97.91，优于对照模型。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.15]
- **results：** 消融实验表明 Inception、Attention、FRN 联用时在三套数据上取得最佳或并列最佳 micro-F1，说明模块间有互补效应。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.16]
- **results：** 在 testset-unknown 对比中，DL-PPI 在多种划分下优于或接近 GNN-PPI，作者据此主张其对未知蛋白更稳健。
  - 证据：[doi:10.1186/s12859-023-05594-5, p.15]

## 页码证据

- [doi:10.1186/s12859-023-05594-5, p.1]
- [doi:10.1186/s12859-023-05594-5, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
