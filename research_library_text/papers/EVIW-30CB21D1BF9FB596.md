# Multi-View Biomedical Foundation Models for Molecule-Target and Property Prediction

- **论文 ID：** `EVIW-30CB21D1BF9FB596`
- **期刊 / 来源：** Adv Sci (Weinh)
- **发表时间：** 2026 Jan 28
- **DOI：** [10.1002/advs.202517840](https://doi.org/10.1002/advs.202517840)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出 MMELON：把独立预训练的 Graph、Image、Text 编码器通过 late fusion 与 learned gating 组合，并在 120+ tasks、106 个 GPCR 以及 AD 相关虚拟筛选中展示应用。

## 创新边界

`冻结证据支持的创新主要是多视图 late fusion、Betti-number 图预训练和大规模 GPCR 应用；没有湿实验，也未核验全局 prior art。`。这不是全球首创性检索或独立复现结论。

## 研究问题

单一分子表示在药物发现中往往只能覆盖结构、序列或图像中的一部分信息，作者要解决的是如何通过多视图 foundation model 同时提升 molecular property prediction、molecule-target affinity prediction 与可用的虚拟筛选能力。

## 方法

- 各view encoder冻结/微调，late fusion学习任务权重。

## 数据与基准

- >120 tasks，solubility/ADME/GPCR activity等。

## 比较基线

- 单view及早/中fusion模型。

## 结果证据

- 论文报告稳健多任务表现，并用结构建模识别motif；无湿实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 各foundation model数据偏差/计算成本，预测未来需wet-lab。

## 仍未知

- 未独立核验 GitHub/Hugging Face 仓库与权重是否可下载。
- 未有湿实验，因此候选命中能否转化为真实活性未知。
- 与所有 prior art 的全局新颖性无法仅凭冻结 PDF 证明。

## Pi 结构化证据摘录

- **baseline：** 主要 baseline 包括 GCN、ChemBERTa-77M-MLM、ChemBERTa-77M-MTR，以及 Graph/Image/Text 单视图消融；Graph 通常是最强单视图，multi-view 更稳健。
  - 证据：[doi:10.1002/advs.202517840, p.4]；[doi:10.1002/advs.202517840, p.14]
- **baseline：** DTI 部分还对比了一个 SOTA GNN implementation，作者声称 MMELON 优于它。
  - 证据：[doi:10.1002/advs.202517840, p.4]
- **data：** 预训练数据由 PubChem 的 80M drug-like molecules 与 ZINC22 的 120M molecules 组成，且按 MW≤600、HBD≤5、HBA≤10、rotatable bonds≤10 过滤。
  - 证据：[doi:10.1002/advs.202517840, p.10]
- **data：** 评测覆盖 120+ datasets，包括 MoleculeNet、CYP inhibition 和 ComputationalADME；分类多用 scaffold split，部分任务用 random split。
  - 证据：[doi:10.1002/advs.202517840, p.4]；[doi:10.1002/advs.202517840, p.13]
- **data：** GPCR 数据集含 106 个 targets 的 experimental pKI assays，来自 ChEMBL 与 GLASS，并剔除 MW>600 Da 和样本过少的 assay。
  - 证据：[doi:10.1002/advs.202517840, p.6]；[doi:10.1002/advs.202517840, p.13]
- **data：** 虚拟筛选输入是 515 gut metabolites 与 2,504 DrugBank FDA-approved drugs；AD-related targets 由 genetics 与 multi-omics 证据筛出 33 个 GPCRs。
  - 证据：[doi:10.1002/advs.202517840, p.7]；[doi:10.1002/advs.202517840, p.13]
- **declared_resources：** 代码与模型声称已公开在 GitHub 和 Hugging Face；本次仅依据论文自述，未访问仓库内容。
  - 证据：[doi:10.1002/advs.202517840, p.2]；[doi:10.1002/advs.202517840, p.9]
- **declared_resources：** 方法与评测依赖的公开资源包括 PubChem、ZINC22、ChEMBL、GLASS、DrugBank、AlzGPS、AlphaFold2 和 PDB。
  - 证据：[doi:10.1002/advs.202517840, p.6]；[doi:10.1002/advs.202517840, p.7]；[doi:10.1002/advs.202517840, p.10]；[doi:10.1002/advs.202517840, p.13]
- **limitations：** 作者明确写到后续需要 wet-lab experiments 来验证虚拟筛选命中。
  - 证据：[doi:10.1002/advs.202517840, p.9]
- **limitations：** 当前架构仍主要基于 1D/2D representations；3D conformers 和 molecule-in-context 只是未来扩展方向。
  - 证据：[doi:10.1002/advs.202517840, p.9]
- **limitations：** 作者也承认，与其他模型的严格 quantitative comparison 依赖相同 data splits 和可用 code，因此文中的横向比较应谨慎解读。
  - 证据：[doi:10.1002/advs.202517840, p.9]；[doi:10.1002/advs.202517840, p.13]
- **method：** MMELON 用 late fusion aggregator 将 Graph、Image、Text 的 embedding 通过 softmax gating 加权，再送入 MLP，因此可以逐任务读取各视图贡献。
  - 证据：[doi:10.1002/advs.202517840, p.4]；[doi:10.1002/advs.202517840, p.11]；[doi:10.1002/advs.202517840, p.12]
- **method：** Image 分支复用 ImageMol；Graph 分支基于 TokenGT，并增加 masked feature prediction、corrupted edge prediction 和 Betti number prediction；Text 分支基于 MolFormer 的 SMILES MLM。
  - 证据：[doi:10.1002/advs.202517840, p.3]；[doi:10.1002/advs.202517840, p.10]；[doi:10.1002/advs.202517840, p.11]
- **method：** Graph 与 Text 在 200M molecules 上预训练 3 epochs，数据来自 PubChem 与 ZINC22；aggregator 还用 10M molecules 做 embedding reconstruction 预训练。
  - 证据：[doi:10.1002/advs.202517840, p.3]；[doi:10.1002/advs.202517840, p.10]；[doi:10.1002/advs.202517840, p.12]
- **method：** 下游还把 ligand embeddings 与 ESM-1b protein embeddings 拼接，用于 DTI 预测。
  - 证据：[doi:10.1002/advs.202517840, p.4]；[doi:10.1002/advs.202517840, p.12]；[doi:10.1002/advs.202517840, p.13]
- **results：** 在 MoleculeNet/CYP/ComputationalADME 上，MMELON 通常优于 GCN 和 ChemBERTa-77M-MLM/MTR，尤其在 FREESOLV、LIPOPHILICTY、RLM、HLM 等回归任务上更强。
  - 证据：[doi:10.1002/advs.202517840, p.4]
- **results：** CYP2C9 任务 ROC-AUC 达 0.90，且 docking 结果与已知 PDB 8VX0 复合物构象相符。
  - 证据：[doi:10.1002/advs.202517840, p.4]；[doi:10.1002/advs.202517840, p.6]
- **results：** 106 个 GPCR held-out regression 的整体 Pearson 为 0.78、平均 RMSE 为 0.79；33 个 AD-related GPCR 子集则为 Pearson 0.67、平均 RMSE 0.88。
  - 证据：[doi:10.1002/advs.202517840, p.6]；[doi:10.1002/advs.202517840, p.7]
- **results：** 筛选中 acetyl-glutamine/FPR1、GSH/FPR1、fructose 1,6-biphosphate/ADA2A 和 isosorbide dinitrate/ADA2A 被提名为强结合候选，并经 docking 显示可能的 allosteric 或 classic binding mode。
  - 证据：[doi:10.1002/advs.202517840, p.7]；[doi:10.1002/advs.202517840, p.9]

## 页码证据

- [doi:10.1002/advs.202517840, p.1]
- [doi:10.1002/advs.202517840, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
