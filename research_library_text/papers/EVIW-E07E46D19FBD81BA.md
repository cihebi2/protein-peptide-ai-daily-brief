# Structure-based TCR-pMHC binding prediction and generalization to unseen peptides

- **论文 ID：** `EVIW-E07E46D19FBD81BA`
- **期刊 / 来源：** npj Drug Discovery（Crossref 书目信息）
- **发表时间：** 2026-08-14
- **DOI：** [10.1038/s44386-026-00064-3](https://doi.org/10.1038/s44386-026-00064-3)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

论文声称系统评估了 GNN-based TCR-pMHC 绑定预测在 unseen peptides 上失效的原因，比较 peptide、MHC、TCR 交互的重要性与结构不确定性，并展示 dual encoder、context conditioning 与 preference-data 训练可在部分测试集上改善泛化。[doi:10.1038/s44386-026-00064-3, p.1] [doi:10.1038/s44386-026-00064-3, p.10]

## 创新边界

`主要是结构化泛化分析与训练策略改进，不是新蛋白设计或新复合物生成方法。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在使用计算预测的 TCR-pMHC 复合物结构进行 binding specificity 预测时，如何提升对 unseen peptides 的泛化能力，并识别影响泛化的关键结构与建模因素。[doi:10.1038/s44386-026-00064-3, p.1]

## 方法

- 从TCR-pMHC预测复合物构建界面图，比较多种GNN；以辅助任务和结构不确定性分析约束分类器。

## 数据与基准

- 使用公开TCR-pMHC样本，并生成/比较initial、Rosetta-relaxed和TCRmodel2三套结构数据。

## 比较基线

- 不同GNN架构、原始/松弛/TCRmodel2结构及无辅助目标模型。

## 结果证据

- 论文确认即使有界面结构，未见肽准确率仍偏低；辅助目标可改善部分泛化，但特定簇难题在三种结构来源中持续存在。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 预测结构误差、样本稀缺和肽簇分布偏移仍限制泛化；分类不证明T细胞功能。

## 仍未知

- 补充信息中的具体实验设置与统计检验细节未独立读取。
- 公开代码仓库与 Zenodo 数据是否能逐项复现实验，未在本次冻结任务中实际运行验证。
- cluster 5 的失败模式是否对其他 TCR-pMHC 数据集同样成立，正文未给出外部验证。

## Pi 结构化证据摘录

- **baseline：** 与 zero-shot baselines 相比，GNN-based 模型多数优于 FoldX，且在部分 cluster 上也优于 Boltz-2；Rosetta energy 相对稳定，但总体只略高于随机。[doi:10.1038/s44386-026-00064-3, p.3] [doi:10.1038/s44386-026-00064-3, p.4]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.3]；[doi:10.1038/s44386-026-00064-3, p.4]
- **baseline：** NetTCR-2.2 在 cluster 5 上异常更好，作者指出这与训练集 peptide 重叠有关；移除重叠样本后 ROC-AUC 会掉到接近 0.5。[doi:10.1038/s44386-026-00064-3, p.3]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.3]
- **baseline：** EPACT 在 cluster 1/2 还能接近较强 GNN，但在其他 cluster 明显落后，说明结构信息在若干 holdout 场景中仍有优势。[doi:10.1038/s44386-026-00064-3, p.3]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.3]
- **data：** 原始数据来自 Slone et al. 的 STAG_public；正样本来自 McPAS-TCR、VDJdb、IEDB 和 10x Genomics，负样本还通过 TCR-swapping 扩增。[doi:10.1038/s44386-026-00064-3, p.11]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.11]
- **data：** 作者在原始结构集上又生成了 Rosetta-relaxed 的 relaxed struct 和由 TCRmodel2 重新预测的 tcrmodel2 struct；后者因置信度阈值与失败样本删除了 987 条记录。[doi:10.1038/s44386-026-00064-3, p.11]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.11]
- **data：** 比较基线包含 Boltz-2、FoldX-5.1、Rosetta、NetTCR-2.2 和 EPACT，其中 sequence-based 模型沿用已发表模型直接评估。[doi:10.1038/s44386-026-00064-3, p.3] [doi:10.1038/s44386-026-00064-3, p.4] [doi:10.1038/s44386-026-00064-3, p.12]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.3]；[doi:10.1038/s44386-026-00064-3, p.4]；[doi:10.1038/s44386-026-00064-3, p.12]
- **declared_resources：** 论文公开了原始数据集、Rosetta-relaxed 与 TCRmodel2 结构数据，以及实验代码；同时还给出用于 docking/crossing angle 的辅助代码来源。[doi:10.1038/s44386-026-00064-3, p.12]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.12]
- **limitations：** 作者明确承认对 unseen peptides 的泛化仍不稳，尤其 cluster 5 基本无法被现有架构显著拉升，说明问题仍未解决。[doi:10.1038/s44386-026-00064-3, p.3] [doi:10.1038/s44386-026-00064-3, p.10]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.3]；[doi:10.1038/s44386-026-00064-3, p.10]
- **limitations：** 论文指出静态结构难以表达 TCR-pMHC 的动力学、catch-bond 和 CDR 柔性，因此仅靠当前 GNN 仍有建模上限。[doi:10.1038/s44386-026-00064-3, p.10]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.10]
- **limitations：** preference loss 依赖 Rosetta-energy 排序，会引入 sample-specific bias，而且周期性微调有时并不能优于普通 binary classification 训练。[doi:10.1038/s44386-026-00064-3, p.9] [doi:10.1038/s44386-026-00064-3, p.12]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.9]；[doi:10.1038/s44386-026-00064-3, p.12]
- **method：** 作者将 345 个 peptide、19,282 个 TCR-pMHC 样本按 peptide 做成 5 个 holdout clusters，每个 cluster 约 1000 个样本，并在剩余数据上做 10-fold cross-validation 评测。[doi:10.1038/s44386-026-00064-3, p.2] [doi:10.1038/s44386-026-00064-3, p.11]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.2]；[doi:10.1038/s44386-026-00064-3, p.11]
- **method：** TCR-pMHC interface 先按 14Å 邻近残基定义，再以 8Å 建 residue-level graph，节点特征使用 Atchley、Kidera 及 chain-type 编码。[doi:10.1038/s44386-026-00064-3, p.11]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.11]
- **method：** 模型比较了 EGNN 与 EVTConv 两种 encoder，并设计 single encoder、dual encoder、conditional encoding 三类架构；dual encoder 额外用 semantic loss 强化 peptide 相关交互。[doi:10.1038/s44386-026-00064-3, p.11] [doi:10.1038/s44386-026-00064-3, p.12]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.11]；[doi:10.1038/s44386-026-00064-3, p.12]
- **method：** 训练细节包括 Adam、learning rate 1e-4、batch size 256、最多 350 epochs，以及每 5 个 epoch 进行一次基于 Rosetta preference pairs 的周期性微调。[doi:10.1038/s44386-026-00064-3, p.12]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.12]
- **results：** 五个 unseen-peptide holdout cluster 中没有单一 GNN 在所有 cluster 都最优；EGNN 整体比 EVTConv 更稳，但 cluster 5 仍然接近随机表现。[doi:10.1038/s44386-026-00064-3, p.3]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.3]
- **results：** dual encoder 在部分 cluster（尤其 1、2、3）提升 ROC-AUC，但 cluster 5 依旧没有明显突破 random baseline，说明当前结构信号不足以稳定泛化到所有新 peptide。[doi:10.1038/s44386-026-00064-3, p.2] [doi:10.1038/s44386-026-00064-3, p.3]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.2]；[doi:10.1038/s44386-026-00064-3, p.3]
- **results：** mask 掉 peptide 后，cluster 1–3 的性能显著下降；cluster 4 呈现 encoder-dependent 变化；cluster 5 几乎不变，说明该 cluster 对 peptide 信息不敏感。[doi:10.1038/s44386-026-00064-3, p.5]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.5]
- **results：** 只用 TCR-MHC 时，cluster 1/2 基本不差于完整图，但 cluster 3 明显掉点；只用 TCR-peptide 时在 cluster 5 表现很差，说明 MHC 在部分场景里是必要上下文。[doi:10.1038/s44386-026-00064-3, p.6]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.6]
- **results：** Rosetta-relaxed 与 tcrmodel2 struct 会改变性能分布，尤其 cluster 5 下降更明显，说明结构来源与结构质量会显著影响泛化。[doi:10.1038/s44386-026-00064-3, p.6] [doi:10.1038/s44386-026-00064-3, p.7]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.6]；[doi:10.1038/s44386-026-00064-3, p.7]
- **results：** 在 cluster 5 上，引入 HLA one-hot 与 preference data 后有小幅提升，但整体仍接近随机水平，属于有限改进而非彻底解决。[doi:10.1038/s44386-026-00064-3, p.8] [doi:10.1038/s44386-026-00064-3, p.9]
  - 证据：[doi:10.1038/s44386-026-00064-3, p.8]；[doi:10.1038/s44386-026-00064-3, p.9]

## 页码证据

- [doi:10.1038/s44386-026-00064-3, p.1]
- [doi:10.1038/s44386-026-00064-3, p.2]
- [doi:10.1038/s44386-026-00064-3, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
