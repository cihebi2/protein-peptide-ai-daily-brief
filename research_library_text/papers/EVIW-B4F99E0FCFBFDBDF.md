# MolMVC: Enhancing molecular representations for drug-related tasks through multi-view contrastive learning

- **论文 ID：** `EVIW-B4F99E0FCFBFDBDF`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2024 Sep 4
- **DOI：** [10.1093/bioinformatics/btae386](https://doi.org/10.1093/bioinformatics/btae386)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 MolMVC：一个多视图对比学习框架，结合 Transformer/Graph Transformer、attention-guided augmentation、AMCLoss 与层级对比学习，预训练得到可迁移的分子表示。

## 创新边界

`主要新意在表示学习与迁移，不涉及分子生成、候选设计或直接优化。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在药物相关任务中，如何同时利用分子的 1D 序列、2D 拓扑与 3D 几何信息，学习更通用的分子表示并提升下游预测性能。

## 方法

- SMILES、2D图、3D构象分别编码，在节点/子结构/图层级计算AMCLoss并动态平衡不同positive pairs。

## 数据与基准

- PCQM4Mv2预训练及多个药物性质benchmark。

## 比较基线

- Uni-Mol/GraphMVP等多视图预训练与单视图/固定contrastive loss消融。

## 结果证据

- 论文报告提高预测精度并降低部分计算成本；为下游计算benchmark。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 3D构象质量和view augmentation决定正样本质量；无实验药效验证。

## 仍未知

- 补充材料中的 drug repositioning 细节与可复现性未在主文完整展开。
- ClinTox 的提升幅度很大，是否受划分或实验设置影响需要外部复核。
- 下游仅转移 1D/2D 编码器，3D 信息的泛化边界不明。

## Pi 结构化证据摘录

- **baseline：** MPP baselines 包括 EdgePred、AttrMask、GraphCL、GPT-GNN、JOAO、GraphLoG、3D InfoMax、GraphMAE、GraphMVP 和 Mole-BERT。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.5]
- **baseline：** DTA baselines 包括 KronRLS、SimBoost、DeepDTA、WideDTA 和 GraphDTA。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.5]
- **baseline：** CDR baselines 包括 MOLI、CDRscan、tCNNs、DeepCDR 和 DeepTTA。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.5]
- **baseline：** 作者说明各基线结果大多取自既有论文，并在相同或可比协议下进行比较。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.5]
- **data：** 预训练数据集为 PCQM4Mv2，作者称其包含 340 万个分子样本。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.2]
- **data：** MPP 评估使用 MoleculeNet 的六个分类基准：BBBP、BACE、ClinTox、HIV、Sider 和 ToxCast，并采用 scaffold split 8:1:1。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.2]；[doi:10.1093/bioinformatics/btae386, p.5]
- **data：** DTA 评估使用 Davis 与 Kiba，指标为 CI 和 MSE。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.5]
- **data：** CDR 任务沿用与竞争方法一致的数据与划分，结果以 PCC/SCC 衡量；此外还做了 SARS-CoV-2 drug repositioning 作为应用展示。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.2]；[doi:10.1093/bioinformatics/btae386, p.5]
- **declared_resources：** 作者公开了 code 和 pre-trained model，GitHub 仓库为 https://github.com/Hhhzj-7/MolMVC。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.1]
- **declared_resources：** 论文还声明数据可在同一仓库获得，显示有可复用资源但仍需分别核查代码与数据许可边界。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.8]
- **limitations：** 转移学习阶段由于下游 3D 分子数据稀缺，作者只使用 1D 和 2D 编码器，说明该方法对显式 3D 下游任务的直接覆盖有限。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.2]
- **limitations：** 药物再定位只在主文简要提及、细节放在补充材料，冻结正文不足以独立评估其规模与稳健性。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.5]；[doi:10.1093/bioinformatics/btae386, p.8]
- **method：** 作者以 PCQM4Mv2 作为预训练语料，并用 Transformer 编码 1D ESPF、用 GIN+SchNet+Graph Transformer 编码 2D/3D 分子图。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.2]；[doi:10.1093/bioinformatics/btae386, p.3]
- **method：** 1D 输入由 ESPF embedding 与 positional embedding 组成；2D 引入 degree 与 shortest path distance，3D 引入 3D distance 与其求和嵌入。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.3]
- **method：** 他们按注意力分数对高权重片段或原子做 mask，借助 prior knowledge 构造模态特定的正样本增强。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.4]
- **method：** AMCLoss 将原始分子、增强分子和跨模态表示统一到对比学习中，并用 DWA 动态调整不同正对的权重。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.4]
- **method：** 模型还在 local/global 两个层级做对比学习；转移阶段仅保留 1D/2D 编码器，并将 local/global 表示汇总后输入预测器。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.2]；[doi:10.1093/bioinformatics/btae386, p.4]
- **results：** 在六个 MPP 基准上 MolMVC 均为最佳，作者报告相对 Mole-BERT 的整体性能提升 6.1%，其中 ClinTox 提升 19.5%，ToxCast 提升 6.6%。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.5]
- **results：** 在 DTA 上，MolMVC* 在 Davis/Kiba 上均优于 GraphDTA，且训练耗时从 5.4h→5.0h（Davis）和 88.3h→80.4h（Kiba）。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.5]
- **results：** 在 CDR 上，MolMVC* 的 PCC/SCC 优于 DeepTTA（94.3/93.7 vs 94.1/91.4），训练成本也从 0.8h 降到 0.3h。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.5]
- **results：** 消融显示去掉预训练、local 分支、3D 信息、attention-guided mask 或 AMCLoss 都会削弱效果，支持各组件有效。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.6]
- **results：** 可视化与检索实验显示模型会关注卤素或含氮基团，预训练后同类样本聚类更紧、检索到的分子结构更相似。
  - 证据：[doi:10.1093/bioinformatics/btae386, p.6]；[doi:10.1093/bioinformatics/btae386, p.7]

## 页码证据

- [doi:10.1093/bioinformatics/btae386, p.1]
- [doi:10.1093/bioinformatics/btae386, p.2]
- [doi:10.1093/bioinformatics/btae386, p.4]
- [doi:10.1093/bioinformatics/btae386, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
