# A Generative Neuro‐Symbolic AI for Protein Sequence Design

- **论文 ID：** `EVIW-0B50D08AC6A9EB98`
- **期刊 / 来源：** Adv Sci (Weinh)
- **发表时间：** 2026 Jul 30
- **DOI：** [10.1002/advs.76464](https://doi.org/10.1002/advs.76464)
- **范围标签：** `待 Pi 解析` / `核心相关` / `论文声明资源` / `扩散/生成`
- **Pi 状态：** 已专家复核，等待 Pi 解析

## 作者主张的创新点

论文提出 EffieDes 神经符号框架：神经网络把骨架适应度编码成 Potts 图模型，再由符号优化器求解约束序列。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

克服自回归逆折叠在长程依赖和硬约束下的序列采样局限。

## 方法

- EffieNN 从 SE(3) 不变骨架特征预测 pairwise Potts 势，LR-BCD/toulbar2 或双目标优化加入对称、正负多态等硬约束。

## 数据与基准

- 标准逆折叠数据、BMC-H 六聚体多态设计和 de novo SARS-CoV-2 XBB.1.16 nanobody 设计。

## 比较基线

- ProteinMPNN、精确/随机 Potts 优化及 Rosetta 结构评分。

## 结果证据

- BMC-H 体内 tGFP 中 EffieDes 12/14 呈阳性而 ProteinMPNN 2/10；一个 nanobody 以 BLI 测得 KD 64 nM 且对 XBB.1.16 有选择性。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- nanobody 只有限候选，无法估计总体成功率；pairwise Potts 仍忽略多体作用。

## 仍未知

- 更大 binder 挑战、非蛋白配体和多体相互作用下的性能未知。

## 页码证据

- [doi:10.1002/advs.76464, p.13]
- [doi:10.1002/advs.76464, p.1]
- [doi:10.1002/advs.76464, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
