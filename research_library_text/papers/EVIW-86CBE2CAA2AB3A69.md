# DeepEnzyme: a robust deep learning model for improved enzyme turnover number prediction by utilizing features of protein 3D-structures

- **论文 ID：** `EVIW-86CBE2CAA2AB3A69`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2024 Aug 20
- **DOI：** [10.1093/bib/bbae409](https://doi.org/10.1093/bib/bbae409)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 DeepEnzyme，一个融合 Transformer、GCN 与注意力机制的 kcat 预测框架，将蛋白序列、蛋白3D结构和底物特征联合建模，并声称在低序列同源与突变体场景下优于既有方法。

## 创新边界

`主要创新是结构增强的酶性质预测与解释分析；它不属于候选酶/药物生成、序列优化或分子设计搜索。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在实验测定昂贵且样本稀缺的情况下，如何利用蛋白序列、3D结构和底物信息更准确、更稳健地预测酶的 turnover number（kcat），并分析突变与关键残基对催化效率的影响。

## 方法

- 蛋白序列表示、三维结构特征融合、监督kcat回归、按相似性控制的鲁棒性评估。

## 数据与基准

- 实验kcat数据库与经去高相似处理的DLKcat相关集合。

## 比较基线

- DLKcat及只用序列/不同特征的消融。

## 结果证据

- 论文报告融合结构后，尤其在与训练集低相似的酶上提高预测鲁棒性。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 依赖高质量实验kcat与三维结构；低相似性能仍是回顾性数据结果。

## 仍未知

- 是否能在未见于训练集的新酶类别上稳定泛化，仍需独立前瞻性验证。
- 未纳入 pH、temperature 等条件后，跨实验条件迁移性能未知。
- ColabFold 预测结构在低置信度蛋白上的误差对模型输出的影响程度未知。

## Pi 结构化证据摘录

- **baseline：** 论文把 TurNuP、DLKcat 和 DLTKcat 作为主要对比基线，并声称 DeepEnzyme 的综合表现更好。
  - 证据：[doi:10.1093/bib/bbae409, p.4]
- **baseline：** 作者还用 Only-sequence 和 Only-structure 消融设置来证明结构特征带来额外增益。
  - 证据：[doi:10.1093/bib/bbae409, p.3]
- **baseline：** 讨论部分提到 UniKP 在某些测试中可能更准，但 DeepEnzyme 在单点突变的定性预测和推理速度上更有优势。
  - 证据：[doi:10.1093/bib/bbae409, p.6]
- **baseline：** 作者也指出 TurNuP 的 RMSE 略低，部分原因是其训练时去掉了极端 kcat 值样本。
  - 证据：[doi:10.1093/bib/bbae409, p.4]
- **data：** 主要训练数据来自 DLKcat 数据集；原始 16,838 对 enzyme-substrate pairs 经相似性清洗后缩减为 11,927 对。
  - 证据：[doi:10.1093/bib/bbae409, p.2]；[doi:10.1093/bib/bbae409, p.7]
- **data：** 由于大量酶没有实验结构，作者用 ColabFold 补齐结构，并报告所有预测结构的平均 pLDDT 为 92.67。
  - 证据：[doi:10.1093/bib/bbae409, p.2]；[doi:10.1093/bib/bbae409, p.7]
- **data：** 外部验证包括 CYP2C9 大规模变异体数据、PafA saturation mutagenesis 数据，以及多个物种的 genome-scale metabolic models。
  - 证据：[doi:10.1093/bib/bbae409, p.5]；[doi:10.1093/bib/bbae409, p.6]；[doi:10.1093/bib/bbae409, p.8]
- **declared_resources：** 作者在 Data availability 中给出了 DeepEnzyme 数据集的 figshare 链接，说明训练大文件已公开托管。
  - 证据：[doi:10.1093/bib/bbae409, p.9]
- **declared_resources：** 作者在 Code availability 中给出 GitHub 仓库 https://GitHub.com/hongzhonglu/DeepEnzyme 作为公开代码入口。
  - 证据：[doi:10.1093/bib/bbae409, p.9]
- **declared_resources：** 致谢部分说明模型部分训练依赖上海交大 Center for High Performance Computing 的 π2.0 cluster。
  - 证据：[doi:10.1093/bib/bbae409, p.9]
- **limitations：** 作者明确承认数据集规模仍不足 12,000 对，更多且更异质的 enzyme-substrate pairs 可能继续提升效果。
  - 证据：[doi:10.1093/bib/bbae409, p.7]
- **limitations：** pH 和 temperature 等关键实验条件没有纳入训练，因此某些预测与实测之间可能出现偏差。
  - 证据：[doi:10.1093/bib/bbae409, p.7]
- **limitations：** 大部分 3D 结构来自 ColabFold 预测而非实验测定，所以结果会受到结构预测质量的影响。
  - 证据：[doi:10.1093/bib/bbae409, p.2]；[doi:10.1093/bib/bbae409, p.7]
- **method：** 先用 MMseqs2 评估酶序列相似性，再对高相似 enzyme-substrate pairs 做过滤，只保留每组中序列最长者，重建出 11,927 对样本并按 80/10/10 划分训练、验证和测试集。
  - 证据：[doi:10.1093/bib/bbae409, p.2]；[doi:10.1093/bib/bbae409, p.7]
- **method：** 对缺失实验结构的酶使用 ColabFold 预测 3D 结构，再按 Cα-Cα 距离小于 10Å 构建 contact map，把结构转成适合深度学习的图表示。
  - 证据：[doi:10.1093/bib/bbae409, p.2]；[doi:10.1093/bib/bbae409, p.7]
- **method：** 用 Transformer 提取蛋白 1D sequence 特征，用 GCN 提取蛋白结构与 substrate graph 特征，并通过 neural attention 汇总后输出 kcat 预测值。
  - 证据：[doi:10.1093/bib/bbae409, p.2]；[doi:10.1093/bib/bbae409, p.8]
- **method：** 底物侧同时使用 RDKit 从 SMILES 生成 fingerprints 和 adjacency matrices，以补充酶端表示并与序列/结构向量融合。
  - 证据：[doi:10.1093/bib/bbae409, p.2]；[doi:10.1093/bib/bbae409, p.8]
- **results：** 在测试集上，DeepEnzyme 的 PCC 接近 0.77；作者还报告五轮训练的平均测试集 R2 约为 0.58，表示整体预测较稳健。
  - 证据：[doi:10.1093/bib/bbae409, p.2]
- **results：** 与只用序列或只用结构的输入相比，加入 protein 3D-structure 后，预测准确性明显提高。
  - 证据：[doi:10.1093/bib/bbae409, p.3]
- **results：** 与 TurNuP、DLKcat 和 DLTKcat 相比，DeepEnzyme 在测试集上取得更高的 R2，且 RMSE 为 0.95。
  - 证据：[doi:10.1093/bib/bbae409, p.4]
- **results：** 在 0–50% 低序列相似度分组中，DeepEnzyme 仍保持较好的 R2，并且对不同相似度区间的波动更小。
  - 证据：[doi:10.1093/bib/bbae409, p.4]
- **results：** 在 CYP2C9 和 PafA 变异体上，模型能区分 missense/nonsense 以及 high/low kcat 变体，说明它对单点突变效应有一定分辨力。
  - 证据：[doi:10.1093/bib/bbae409, p.5]
- **results：** 在 PafA 与 P00558 中，binding/active sites 的权重高于一般位点，高权重位点在三维空间上与功能位点邻近或部分重叠。
  - 证据：[doi:10.1093/bib/bbae409, p.6]
- **results：** 用于 GEM 级推断时，DeepEnzyme 能为多个物种的酶催化反应生成分布合理的 kcat 预测，并支持大规模批量计算。
  - 证据：[doi:10.1093/bib/bbae409, p.6]；[doi:10.1093/bib/bbae409, p.7]

## 页码证据

- [doi:10.1093/bib/bbae409, p.1]
- [doi:10.1093/bib/bbae409, p.2]
- [doi:10.1093/bib/bbae409, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
