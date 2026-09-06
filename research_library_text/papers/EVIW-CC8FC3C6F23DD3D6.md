# Generalizable compound protein interaction prediction with a model incorporating protein structure aware and compound property aware language model representations

- **论文 ID：** `EVIW-CC8FC3C6F23DD3D6`
- **期刊 / 来源：** Commun Chem
- **发表时间：** 2025 Dec 19
- **DOI：** [10.1038/s42004-025-01844-0](https://doi.org/10.1038/s42004-025-01844-0)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `语言模型` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出 GenSPARC，把 AlphaFold2/FoldSeek 生成的蛋白 structure-aware 表示与 GCN + SPMM 化合物结构/性质表示，通过 MAN 融合到统一框架里，同时覆盖 contact map、binding affinity 和 virtual screening 任务。

## 创新边界

`这是一个以表示学习和预测为主的计算方法创新；论文未提供新的 wet-lab 实验或候选分子生成流程，主要证据来自基准评测。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在缺乏实验结构与高质量标注的情况下，如何让 compound-protein interaction (CPI) 预测对未见蛋白、未见化合物以及预测结构保持稳健泛化。

## 方法

- 结构感知protein LM与compound graph/LM多模态融合，分类/affinity输出。

## 数据与基准

- Davis/KIBA/Metz等多CPI benchmark和virtual screening。

## 比较基线

- 主流sequence/graph CPI方法及representation消融。

## 结果证据

- 论文报告困难拆分与虚拟筛选竞争性能；为计算CPI。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- benchmark靶点偏kinase，预测结构/外部domain仍限制。

## 仍未知

- 补充材料中的完整超参数、数据划分细节与实现细节未在正文页中完全展开。
- 冻结证据未实际运行 GitHub 仓库，无法确认代码与权重的可执行性。
- 论文结果主要来自作者自报基准，没有外部独立复现实验作为佐证。

## Pi 结构化证据摘录

- **baseline：** Karimi 评测的直接基线包括 MONN、Cross-Interaction、PSC-CPI 和 GraphBAN。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.3]；[doi:10.1038/s42004-025-01844-0, p.4]
- **baseline：** Davis/KIBA/Metz 评测的基线覆盖 DeepConvDTI、GraphDTA、HyperattentionDTI、TransformerCPI、PerceiverCPI、Cross-Interaction、PSC-CPI 和 GraphBAN。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.7]
- **baseline：** DUD-E 评测对比了 Glide-SP、AutoDock Vina、RF-score、NNScore、Pafnucy、OnionNet、Planet、DrugCLIP、3D-CNN、GraphCNN、COSP、DrugVQA 和 AttentionSiteDTI。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.7]
- **data：** 主要 CPI 评测集是 Karimi/Cross-Interaction 数据集，含 4446 对 compound-protein pairs、1287 个蛋白和 3672 个化合物，并按 Seen-Both/Unseen-Comp/Unseen-Prot/Unseen-Both 划分。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.3]；[doi:10.1038/s42004-025-01844-0, p.9]
- **data：** 作者进一步构造 sequence-hard 和 structure-hard 划分，对化合物施加 Tanimoto 相似度阈值，并对蛋白使用 sequence alignment 与 structural alignment 约束。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.4]；[doi:10.1038/s42004-025-01844-0, p.9]
- **data：** 补充 affinity 基准包括 Davis、KIBA、Metz；virtual screening 则使用 DUD-E。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.6]；[doi:10.1038/s42004-025-01844-0, p.7]；[doi:10.1038/s42004-025-01844-0, p.9]；[doi:10.1038/s42004-025-01844-0, p.10]
- **declared_resources：** 重复分析所需数据可通过 GitHub 和 Zenodo 获取。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.11]
- **declared_resources：** 论文明确声明代码和 model weights 公开于 GitHub: https://github.com/pfnet-research/GenSPARC。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.11]
- **limitations：** 作者承认 compound encoder 主要依赖 RDKit 的高层分子描述符，若加入更丰富的 3D compound 表示，性能可能还能提升。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.8]
- **limitations：** 将绝对坐标直接喂给模型可能对实验结构过拟合、对 AlphaFold2 预测结构泛化较差，因此结构表示仍存在 accuracy 与 generalization 的权衡。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.8]
- **limitations：** 训练数据中缺少 intrinsically disordered proteins (IDPs)，作者建议未来用 ensemble-based prediction 扩展到这类蛋白。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.8]
- **method：** 蛋白端先用 AlphaFold2 预测结构，再借助 FoldSeek 把 residue 映射为 structure-aware alphabet，交给 SaProt 提取蛋白嵌入。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.1]；[doi:10.1038/s42004-025-01844-0, p.3]；[doi:10.1038/s42004-025-01844-0, p.10]
- **method：** 化合物端把 SMILES 转成 molecular graph，用 3-layer GCN 学习原子表示，并用 SPMM 预训练 property encoder 融合 53 个分子属性。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.1]；[doi:10.1038/s42004-025-01844-0, p.3]；[doi:10.1038/s42004-025-01844-0, p.10]
- **method：** MAN 通过 self-attention 与 cross-attention 细化 protein/compound token 表示；binding affinity 用 MLP 回归，contact map 用 pairwise interaction network 和稀疏正则训练。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.3]；[doi:10.1038/s42004-025-01844-0, p.10]；[doi:10.1038/s42004-025-01844-0, p.11]
- **method：** 作者还定义了 GenSPARC–MT，把 affinity loss 与 interaction loss 联合优化，以同时学习两类 CPI 目标。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.3]；[doi:10.1038/s42004-025-01844-0, p.11]
- **results：** 在原始 Karimi 数据集上，GenSPARC 在 contact prediction 的平均 AUPRC/AUROC 为 22.13/92.29，在 affinity prediction 的平均 RMSE/PCC 为 1.420/0.661，整体优于 MONN、Cross-Interaction、PSC-CPI 和 GraphBAN。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.3]
- **results：** 在 sequence-hard 与 structure-hard 的更严格拆分下，GenSPARC 仍保持较强泛化；例如 contact prediction 的平均分分别为 22.43/92.44 和 21.20/92.04，并在 Unseen-Prot 与 Unseen-Both 上明显优于 PSC-CPI。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.4]；[doi:10.1038/s42004-025-01844-0, p.5]
- **results：** 在 Davis/KIBA/Metz 上，GenSPARC 的 MSE 均为最优，并在 six metrics 中拿到四项最佳，说明其在补充 affinity benchmark 上同样稳健。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.7]
- **results：** 在 DUD-E zero-shot 中，GenSPARC-AF 的 EF 0.5%/1%/5% 为 7.14/6.59/3.47，优于 DrugCLIP-AF 和 Vina-AF；GenSPARC-PDB 也与 DrugCLIP-PDB 处于可比水平。
  - 证据：[doi:10.1038/s42004-025-01844-0, p.7]

## 页码证据

- [doi:10.1038/s42004-025-01844-0, p.1]
- [doi:10.1038/s42004-025-01844-0, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
