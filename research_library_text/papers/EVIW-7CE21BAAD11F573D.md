# Multimodal pretraining for unsupervised protein representation learning

- **论文 ID：** `EVIW-7CE21BAAD11F573D`
- **期刊 / 来源：** Biol Methods Protoc
- **发表时间：** 2024 Jun 18
- **DOI：** [10.1093/biomethods/bpae043](https://doi.org/10.1093/biomethods/bpae043)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `有静态审计仓库` / `结构预测` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出 MPRL（Multimodal Protein Representation Learning）框架，把 ESM-2、VGAE、PAE 与 Auto-Fusion 组合成对称性保持的多模态无监督预训练方案，用于学习统一 protein representation，并在多项下游任务上验证其有效性。

## 创新边界

`新意主要在多模态表征融合与对称性约束下的预训练，不涉及 protein、peptide、binder、enzyme 或 drug 候选的生成、优化、对接或排名。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何在无监督条件下融合 protein sequence、residue-level graph 与 3D point cloud 三种模态，学习同时保留旋转/平移等对称性、且可迁移到多类 protein 表征与性质预测任务的统一表示。

## 方法

- 序列编码器、三维等变/图表示和多模态对齐；Swiss-Prot/AlphaFold结构预训练；下游微调。

## 数据与基准

- Swiss-Prot结构集合；DAVIS、KIBA、PDBbind等下游蛋白-配体数据。

## 比较基线

- 单序列PLM、单结构图模型及监督下游模型。

## 结果证据

- 论文报告在链接预测及若干下游任务具有竞争表现；本轮没有足够页证据支持统一的跨任务SOTA表述。

## 可用资源与代码关系

- [https://github.com/HySonLab/Protein_Pretrain](https://github.com/HySonLab/Protein_Pretrain)
  - 固定 commit：`88b7a1366377318b8ae359eb523dd583a5e39261`
  - 静态复用层级：C_license_or_component_gaps
  - 许可证边界：license_not_found_reuse_blocked

## 已知限制

- AlphaFold结构误差可传递到预训练；不同下游数据可能存在同源/配体泄漏。

## 仍未知

- 公开 GitHub 仓库与论文描述是否完全一致未核验。
- 附录未展开的实现细节（如具体预处理与数据清洗）仍不完全透明。
- 结果是否能在独立复现中稳定达到同等水平，冻结证据无法证明。

## Pi 结构化证据摘录

- **baseline：** 在 binding affinity 上，论文将 MPRL 与 KronRLS、SimBoost、DeepDTA、AttentionDTA、PMN、Pafnucy、TankBind、PSICHIC 等方法比较；作者也承认 MPRL 在 DAVIS、KIBA 和 PDBbind 2020 上未超过最优专门模型。
  - 证据：[doi:10.1093/biomethods/bpae043, p.9]
- **baseline：** 在 SCOPe 1.75 fold classification 上，比较对象包括 InConv 系列、EdgePool、AminoGraph、AtomicGraph 等，其中 AtomicGraph 的结果最强（45.0%、69.7%、98.9%）。
  - 证据：[doi:10.1093/biomethods/bpae043, p.10]
- **baseline：** 在 enzyme identification 与 MSP 上，比较对象分别包括 Hermosilla et al.（85.5%）和 GNN（0.609 AUROC）；MPRL 在 MSP 上略高于 GNN，但在 enzyme identification 上仍低于最优基线。
  - 证据：[doi:10.1093/biomethods/bpae043, p.10]
- **data：** 预训练数据来自 Swiss-Prot structure dataset（来源于 AlphaFold Protein Structure database），共 542,378 个 PDB files，并按 70:20:10 划分为 train/validation/test。
  - 证据：[doi:10.1093/biomethods/bpae043, p.7]
- **data：** binding affinity 评估使用 DAVIS（442 proteins, 68 ligands, 30,056 pairs）、KIBA（229 proteins, 2,111 ligands, 118,254 pairs）与 PDBbind version 2020（19,433 pairs；general/refined split）等数据集。
  - 证据：[doi:10.1093/biomethods/bpae043, p.7]；[doi:10.1093/biomethods/bpae043, p.8]
- **data：** 结构与功能下游任务分别使用 SCOPe 1.75（16,712 proteins, 1,195 folds）、D&D（1,178 proteins）与 Atom3D 的 MSP 任务（4,148 mutant structures 与 316 WT structures；test set 与 train set 序列同一性不超过 30%）。
  - 证据：[doi:10.1093/biomethods/bpae043, p.8]；[doi:10.1093/biomethods/bpae043, p.9]
- **declared_resources：** 论文明确给出 public source code，地址为 https://github.com/HySonLab/Protein_Pretrain。
  - 证据：[doi:10.1093/biomethods/bpae043, p.1]
- **declared_resources：** 实现依赖 Hugging Face Transformers、PyTorch、PyTorch Geometric、GPyTorch 与 XGBoost 等软件栈。
  - 证据：[doi:10.1093/biomethods/bpae043, p.11]
- **declared_resources：** 文中声明使用的主要数据资源包括 AlphaFold Protein Structure database、DAVIS、KIBA、PDBbind 2020、SCOPe 1.75、D&D、Atom3D 与 Leak Proof PDBBind。
  - 证据：[doi:10.1093/biomethods/bpae043, p.7]；[doi:10.1093/biomethods/bpae043, p.8]；[doi:10.1093/biomethods/bpae043, p.13]
- **limitations：** 作者自己的结果说明，PAE 的 validation loss 存在不稳定与较高方差，说明在复杂 protein structure dataset 上训练仍然敏感。
  - 证据：[doi:10.1093/biomethods/bpae043, p.7]
- **limitations：** 论文没有在所有任务上取得最优；例如 binding affinity、fold classification 与 enzyme identification 都落后于部分更强的 specialized baseline。
  - 证据：[doi:10.1093/biomethods/bpae043, p.9]；[doi:10.1093/biomethods/bpae043, p.10]
- **limitations：** VGAE 和 PAE 单模态结果整体弱于 ESM-2，说明性能提升主要来自 multimodal combination，而不是任何单一结构分支本身。
  - 证据：[doi:10.1093/biomethods/bpae043, p.9]；[doi:10.1093/biomethods/bpae043, p.10]
- **method：** 序列分支直接使用预训练的 ESM-2 checkpoint，论文明确说明作者没有自行训练 ESM-2，而是取 150M 参数版本的 last hidden state 作为序列表征。
  - 证据：[doi:10.1093/biomethods/bpae043, p.4]；[doi:10.1093/biomethods/bpae043, p.11]
- **method：** 图分支把每个 residue 当作节点，并用 alpha-carbon 的 KNN（k=5）构图；VGAE 采用 GCN encoder 与 inner-product decoder，以 link prediction/reconstruction loss 学习 residue-level 图表征。
  - 证据：[doi:10.1093/biomethods/bpae043, p.4]；[doi:10.1093/biomethods/bpae043, p.5]
- **method：** 点云分支将每个 atom 表示为 3D point，先做 centering、scaling、padding/trimming，再用 PointNet-based PAE 和 chamfer distance 训练；融合阶段用 Auto-Fusion 对多模态向量做拼接、z-score 标准化与重构学习。
  - 证据：[doi:10.1093/biomethods/bpae043, p.5]；[doi:10.1093/biomethods/bpae043, p.6]；[doi:10.1093/biomethods/bpae043, p.11]
- **method：** 下游任务上，binding affinity 采用 protein 表征与 Morgan fingerprints 拼接后输入 Gaussian Process 回归器；fold classification、enzyme identification 与 MSP 则使用 XGBoost classifier。
  - 证据：[doi:10.1093/biomethods/bpae043, p.8]；[doi:10.1093/biomethods/bpae043, p.11]
- **results：** 在 binding affinity 上，MPRL 在 DAVIS 达到 MSE 0.248、CI 0.699、r_m^2 0.414，在 KIBA 达到 MSE 0.199、CI 0.812、r_m^2 0.471；在 PDBbind 2020 达到 RMSE 1.372、MAE 1.104、Pearson 0.663、Spearman 0.634、r_m^2 0.246、CI 0.726。
  - 证据：[doi:10.1093/biomethods/bpae043, p.9]
- **results：** 在结构/功能分类上，MPRL 在 SCOPe 1.75 的 Fold/Superfamily/Family 三个子集分别取得 43.1%、63.2%、98.4%；在 D&D enzyme identification 上取得 83.9% accuracy；在 MSP 上取得 AUROC 0.612。
  - 证据：[doi:10.1093/biomethods/bpae043, p.10]
- **results：** 对称性消融实验显示，把 protein structure 随机旋转和平移后，DAVIS/KIBA/PDBbind 2020 的 RMSE 仅小幅变化（0.497→0.503、0.446→0.451、1.372→1.380），支持其对旋转/平移扰动的鲁棒性。
  - 证据：[doi:10.1093/biomethods/bpae043, p.12]

## 页码证据

- [doi:10.1093/biomethods/bpae043, p.11]
- [doi:10.1093/biomethods/bpae043, p.1]
- [doi:10.1093/biomethods/bpae043, p.2]
- [doi:10.1093/biomethods/bpae043, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
