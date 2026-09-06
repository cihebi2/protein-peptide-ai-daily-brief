# SPIN-CGNN: Improved fixed backbone protein design with contact map-based graph construction and contact graph neural network

- **论文 ID：** `EVIW-B62B9EA1E43384ED`
- **期刊 / 来源：** PLoS Comput Biol
- **发表时间：** 2023 Dec 7
- **DOI：** [10.1371/journal.pcbi.1011330](https://doi.org/10.1371/journal.pcbi.1011330)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白质设计` / `图与几何学习`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出 SPIN-CGNN：用 contact map-based graph construction 取代固定 KNN 图，并结合 symmetric edge、second-order edge 与 selective kernel，提升固定 backbone protein design 的序列恢复与生物学合理性。

## 创新边界

`仅能确认其在作者选定基准上的增量改进，冻结证据不足以证明相对全部既有工作具有全球新颖性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在给定固定蛋白骨架结构的前提下，设计更接近天然分布、且更容易折叠为目标结构的氨基酸序列，并同时改善 sequence recovery、perplexity、组成偏差、复杂度与复折一致性。

## 方法

- backbone contact graph、residue features与sequence prediction。

## 数据与基准

- CATH/protein structures。

## 比较基线

- SPIN/GraphTrans/ProteinMPNN类。

## 结果证据

- 论文报告sequence recovery/design metrics提升；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- recovery非fold/function，contact cutoff。

## 仍未知

- 未独立验证 GitHub 仓库的可运行性与复现细节。
- 未见 wet-lab 实验，结论全部来自计算基准与 AlphaFold2 复折。
- 与更近外部 prior-art 的全局新颖性比较不在冻结证据内。

## Pi 结构化证据摘录

- **baseline：** 主要对比基线包括 RosettaFixBB、OSCAR-design、ProteinMPNN 和 PiFold；作者还按原始设置重现了 ProteinMPNN 与 PiFold，并报告了与原论文相近的 recovery。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.11]
- **baseline：** 图构建基线采用 KNN-30，并与 CGraph-8/10/12 对比；结果显示 CGraph-12 在两个非冗余测试集上均优于 KNN-30。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.11]
- **baseline：** 文中还汇总了 StructGNN、GraphTrans、GCA、GVP、AlphaDesign、LM-DESIGN 等方法的公开结果，用于 whole CATH4.2 对照。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.14]
- **data：** 主训练/验证/测试集采用 CATH4.2，共 18024/608/1120 个 structure-sequence pairs，分别覆盖 950/100/150 folds。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.4]
- **data：** 为减少结构冗余偏置，作者构建 CATH4.2-StructNR193：按 TM-score > 0.4 迭代删除测试集近邻，最终保留 193 个样本。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.5]
- **data：** 作者还构建 PDB-StructNR156：仅保留 2019-04-09 之后、长度不少于 30 residues、且与既有集合最大 TM-score ≤ 0.4 的链。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.5]
- **data：** 补充评测集包括 129 个 hallucinated structures 的 Hallucination129，以及从 1000 个 SE(3) diffusion 结构中按 median refold RMSD 选出的 100 个结构组成的 Diffusion100。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.5]
- **declared_resources：** 作者在文中提供了 source code and datasets 的 GitHub 链接：https://github.com/EricZhangSCUT/SPIN-CGNN。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.1]
- **declared_resources：** Acknowledgments 提到研究使用了 Shenzhen Bay Laboratory 的 supercomputing facility。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.23]
- **limitations：** 作者明确指出，设计序列的 low complexity regions 仍明显高于 native，尤其在 generated structures 上更突出，说明该问题尚未解决。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.15]；[doi:10.1371/journal.pcbi.1011330, p.19]；[doi:10.1371/journal.pcbi.1011330, p.21]
- **limitations：** 作者也承认 AlphaFold2 refolding 对高度接近 wild type 的设计序列不够敏感，且其输入包含天然同源序列，因此不能把 refolding 当作唯一质量指标。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.21]
- **limitations：** 若进一步用 TM-score < 0.4 严格去冗余训练集，训练规模会从 18024 缩到 9311，反而导致性能下降，说明过严过滤会损失有用的局部结构信息。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.21]
- **method：** SPIN-CGNN 以基于虚拟 Cβ 距离阈值的 contact graph 表示蛋白骨架，替代固定 KNN 邻居图，并显式记录对称边与二阶边以增强消息传递。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.5]；[doi:10.1371/journal.pcbi.1011330, p.6]；[doi:10.1371/journal.pcbi.1011330, p.7]
- **method：** 节点特征由局部坐标系下的方向向量、键角/扭转角，以及到 N、C、O 和 virtual Cβ 的 RBF 距离构成；边特征整合 25 个原子对方向特征、64 个距离特征与 positional encoding。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.5]；[doi:10.1371/journal.pcbi.1011330, p.6]
- **method：** 网络堆叠 10 个 CGNN block，先做 edge update 再做 node update，并用 selective kernel 融合对称/二阶/基础边更新，以及局部/全局 node 更新。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.6]；[doi:10.1371/journal.pcbi.1011330, p.7]；[doi:10.1371/journal.pcbi.1011330, p.8]；[doi:10.1371/journal.pcbi.1011330, p.9]
- **method：** 训练以 native sequence 为监督，采用 AdamW、OneCycle learning rate、100 epochs、dropout 0.1、mixed precision 和最大 4096 residues 的 batch size。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.9]
- **results：** 在 whole CATH4.2 test set 上，SPIN-CGNN 取得最好的 perplexity 5.01，并以 54.81% recovery 领先多数深度学习基线，但 recovery 略低于 LM-DESIGN 的 55.65%。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.14]
- **results：** 在 CATH4.2-StructNR193 与 PDB-StructNR156 上，SPIN-CGNN 的 perplexity 为 4.36/3.42，median recovery 为 52.50%/58.88%，均优于 PiFold 的 4.88/4.00 和 50.00%/54.81%。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.15]
- **results：** 加入 edge updates 后，perplexity 约下降 4–6%，recovery 约提升 1%；再加入 selective kernel 后，perplexity 进一步下降约 3%，recovery 再提升约 1%。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.12]；[doi:10.1371/journal.pcbi.1011330, p.13]
- **results：** 在 AA composition、BLOSUM、LCR 与 hydrophobic conservation 上，SPIN-CGNN 在非冗余测试集上总体优于 ProteinMPNN 和 PiFold；例如在 PDB-StructNR156 上 median Rel.Dev. 为 0.063、relative BLOSUM 为 0.517、LCR 为 5.49%、hydrophobic conservation 为 85.44%。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.15]；[doi:10.1371/journal.pcbi.1011330, p.16]
- **results：** 用 AlphaFold2 复折时，SPIN-CGNN 在 PDB-StructNR156 上达到 1.75 Å RMSD、85.65 GDT-TS 和 0.913 TM-score，且在 CATH4.2-StructNR193 上也与 PiFold 接近并明显优于 ProteinMPNN。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.15]；[doi:10.1371/journal.pcbi.1011330, p.17]
- **results：** 在 Hallucination129 和 Diffusion100 上，SPIN-CGNN 的 refold RMSD/GDT-TS/TM-score 分别为 1.19 Å/89.00/0.923 和 1.91 Å/81.13/0.878；整体优于 RosettaFixBB 与 ProteinMPNN，并与 OSCAR-design、PiFold 接近。
  - 证据：[doi:10.1371/journal.pcbi.1011330, p.19]

## 页码证据

- [doi:10.1371/journal.pcbi.1011330, p.1]
- [doi:10.1371/journal.pcbi.1011330, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
