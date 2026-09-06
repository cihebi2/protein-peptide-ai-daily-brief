# Rationally seeded computational protein design of ɑ-helical barrels

- **论文 ID：** `EVIW-FDA5C6B43CD436AE`
- **期刊 / 来源：** Nat Chem Biol
- **发表时间：** 2024 Jun 20
- **DOI：** [10.1038/s41589-024-01642-0](https://doi.org/10.1038/s41589-024-01642-0)
- **范围标签：** `待 Pi 解析` / `核心相关` / `论文声明资源` / `蛋白质设计` / `肽与抗菌肽` / `结构预测`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析待处理

## 作者主张的创新点

作者提出以已验证 peptide sequence-to-structure 规则为 seed，再用 loop building、ProteinMPNN、Rosetta 和 AlphaFold2 完成 antiparallel/parallel alpha-helical barrel 设计；贡献按论文自述。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何把已验证的多聚 coiled-coil peptide barrel 转换成可由单基因表达、可打破对称并保留中央通道的单链蛋白。

## 方法

- antiparallel 路线以短 loop 连接相邻螺旋；parallel 路线用 MASTER 检索实验结构片段构建较长 helix-turn-helix-turn-helix 外层连接。 固定定义开放通道的核心位点，ProteinMPNN 设计其余序列，Rosetta 按能量/packing/表面疏水过滤，AlphaFold2 复核并迭代。 每个 6 个目标只合成 2-6 个基因，在 E. coli 表达后用 SEC、CD、SAXS、晶体结构与小分子染料结合表征。

## 数据与基准

- 先测试 20 个 antiparallel peptide 组合；设计目标覆盖 antiparallel 6/8 螺旋及 parallel 5/6/7/8 中央螺旋。 多个高分辨结构与 PDB accession 8QAA、8QAC、8QAB、8QAD、8QAE、8QAF、8QKD、8QAG、8QAI、8QAH。

## 比较基线

- 纯 rational coiled-coil 规则与完全从头的大规模 backbone/sequence sampling 是两端对照。 MASTER、ProteinMPNN、Rosetta、AlphaFold2 是组装的既有工具，论文贡献主要在 seed+连接+约束工作流。

## 结果证据

- 每目标仅测试 2-6 个基因，平均约 70% 表达为可溶单体；多数目标获得与设计模型高吻合的高分辨结构。 核心重复 motif 的 backbone RMSD 小于等于 0.5 A；多数新蛋白中央通道可结合小分子染料。 Foldseek/PDB/AlphaFold2-SwissProt 搜索支持这些结构与已知蛋白存在局部/整体相似，但作者将其解释为新的单链 coiled-coil barrel 类别。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 成功率来自经过验证 seed 和高度约束的小批量目标，不能等同无条件 de novo design 的普适命中率。 一个 antiparallel 设计的 Ser-Ser 极性界面与模型不一致，parallel 结构末端有轻微 fraying，提示极性接触和边界仍难建模。 小分子功能证据主要为通道染料结合，实际催化/运输/治疗功能尚待工程化。

## 仍未知

- 仓库许可证、外部依赖版本、完整 pipeline 可重跑性尚未静态审计。
- 中央通道的可编程选择性、真实功能和其他 fold family 的迁移成功率未知。

## 页码证据

- [doi:10.1038/s41589-024-01642-0, p.10]
- [doi:10.1038/s41589-024-01642-0, p.11]
- [doi:10.1038/s41589-024-01642-0, p.1]
- [doi:10.1038/s41589-024-01642-0, p.2]
- [doi:10.1038/s41589-024-01642-0, p.3]
- [doi:10.1038/s41589-024-01642-0, p.4]
- [doi:10.1038/s41589-024-01642-0, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
