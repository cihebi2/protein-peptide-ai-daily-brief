# IEV2Mol: Molecular Generative Model Considering Protein-Ligand Interaction Energy Vectors

- **论文 ID：** `EVIW-03ED7DB23F4F78B7`
- **期刊 / 来源：** J Chem Inf Model
- **发表时间：** 2024 Sep 10
- **DOI：** [10.1021/acs.jcim.4c00842](https://doi.org/10.1021/acs.jcim.4c00842)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `扩散/生成`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

论文提出 IEV2Mol：把 docking 计算得到的 interaction energy vector (IEV) 与 SMILES 化学空间表示通过双 VAE 和 Z-DNN 连接起来，从而在给定目标蛋白相互作用能量模式时生成新的分子候选。

## 创新边界

`创新点边界在于把实值 IEV 作为条件信号用于分子生成，而不是仅用二值 interaction fingerprint；但论文本身也依赖既有 IEV/IFP 与 docking 体系，因此更像是面向生成任务的组合式推进，而非冻结证据内可独立证明的全球首创。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在结构基础药物设计中，如何让生成模型不仅复现配体与蛋白的“是否相互作用”，还要保留相互作用强度，并同时生成结构上足够多样的候选分子。

## 方法

- 为蛋白-配体对计算IEV，将其与SMILES VAE潜表示结合，联合优化SMILES重构和交互能条件；对DRD2、AA2AR和AKT1生成并重新对接。

## 数据与基准

- DM-QP-1M、ChEMBL33约227万分子、三靶点活性化合物和对应对接/IEV；每个测试点还抽100个ChEMBL随机分子。

## 比较基线

- JT-VAE、IFP-RNN、Random ChEMBL。

## 结果证据

- 论文报告IEV2Mol相较JT-VAE、IFP-RNN和随机ChEMBL更能保持种子结合模式并获得较高IEV相似，同时结构相似性更低；结果来自生成和对接，无合成/活性实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 需要靶蛋白三维结构和已知配体；IEV依赖对接与能量函数，跨新蛋白泛化未充分验证。

## 仍未知

- 未见独立湿实验或生物活性实测验证。
- 冻结页内没有核验 GitHub 仓库实际内容是否与论文完全一致。
- 对更多靶点与更大化学空间的泛化能力尚未被系统证明。
- IEV 对 docking 构象误差与评分函数偏差的敏感性未被量化。

## Pi 结构化证据摘录

- **baseline：** JT-VAE 作为 unconstrained graph VAE，在这里表现为高度依赖 seed 结构，相似度分布在 IEV cosine 1.0 处有明显峰值，同时 uniqueness 和 diversity 明显较差。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.5]；[doi:10.1021/acs.jcim.4c00842, p.6]；[doi:10.1021/acs.jcim.4c00842, p.7]
- **baseline：** IFP-RNN 以 residue-specific IFP 作为条件，且训练时需要为全部训练数据计算 IFP，因此扩展训练集更困难；它在 joint low-similarity/high-IEV 指标上也落后于 IEV2Mol。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.4]；[doi:10.1021/acs.jcim.4c00842, p.5]；[doi:10.1021/acs.jcim.4c00842, p.6]
- **baseline：** Random ChEMBL 只是从 ChEMBL33 随机抽样的非条件基线，用于给出无条件化学空间参考。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.4]；[doi:10.1021/acs.jcim.4c00842, p.5]
- **data：** DM-QP-1M 来自随机抽取的 DM-QP 数据集，去除重复与多组分条目后得到 981,139 个化合物，用于学习更宽的化学空间。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.2]
- **data：** active compound data set 由 ChEMBL 的 Ki/IC50 数据构建，分别包含 DRD2 8,350、AA2AR 6,640、AKT1 3,576 个化合物，并用 Glide HTVS 与 PDB 结构 6CM4、3EML、3CQW 计算 IEV。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.2]
- **data：** 每个靶点的 active compounds 先在 ECFP4 1024-bit 空间做 100 类 k-means 聚类，再选取最靠近质心的 100 个分子作为 test set，其余作为 training set。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.3]
- **declared_resources：** 论文声明 source code、trained models、数据集和绘图/评估脚本都已在 GitHub 仓库公开，并以 MIT License 发布。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.1]；[doi:10.1021/acs.jcim.4c00842, p.8]
- **declared_resources：** 仓库地址为 https://github.com/sekijima-lab/IEV2Mol，论文还说明其包含面向 DRD2、AA2AR、AKT1 的 IEV2Mol、JT-VAE 与 IFP-RNN 结果资产。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.1]；[doi:10.1021/acs.jcim.4c00842, p.8]
- **declared_resources：** 文中还给出了训练与 docking 的计算环境：一套用于 docking 的 SUSE Linux / Xeon / 4×P100，及一套用于训练与生成的 Ubuntu 22.04 / Xeon Silver 4110 / RTX 4090。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.4]
- **limitations：** 作者明确指出，该方法需要目标蛋白的三级结构以及已知 ligand 数据，因此并不适用于完全无结构或无先验配体的靶点。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.8]
- **limitations：** 整个流程依赖 docking pose 与 Glide 评分来构造 IEV，因此模型性能会继承 docking 近似与构象选择误差。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.2]；[doi:10.1021/acs.jcim.4c00842, p.4]；[doi:10.1021/acs.jcim.4c00842, p.8]
- **method：** 作者使用 Glide 做 docking，并用蛋白准备、LigPrep 和最佳得分构象来计算 IEV；IEV 由 12 Å 范围内残基的 van der Waals、Coulomb 和 hydrogen bond 能量组成。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.2]
- **method：** IEV2Mol 的架构由 SMILES-VAE、IEV-VAE 和 Z-DNN 组成；前两者分别学习 SMILES 和 IEV 的 latent space，Z-DNN 将二者拼接后映射回 SMILES-VAE latent space 以驱动生成。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.3]
- **method：** 训练流程是先用 DM-QP-1M 预训练 SMILES-VAE，再用 active compound data 预训练 IEV-VAE，随后冻结两个 encoder 并端到端训练 decoder 与 Z-DNN。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.3]；[doi:10.1021/acs.jcim.4c00842, p.4]
- **method：** 生成阶段把目标 IEV 编码后，与随机采样的 SMILES latent 连接，经 Z-DNN 和 SMILES-VAE decoder 解码成新 SMILES。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.4]
- **results：** Table 1 显示 IEV2Mol 在三个靶点上的 validity 为 97.5/96.3/94.6，uniqueness 为 0.987/0.979/0.971，diversity 为 0.835/0.855/0.851，整体优于 JT-VAE 和 IFP-RNN。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.5]
- **results：** 在联合指标 IEV Cos ≥ 0.7 且 Tanimoto ≤ 0.5 上，IEV2Mol 对 DRD2、AA2AR、AKT1 分别达到 27.0、66.7、22.7，三者都高于对照方法。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.5]
- **results：** Figure 2 到 Figure 4 表明，IEV2Mol 一方面比 IFP-RNN 产生更低的 Tanimoto 分布、另一方面仍保持较高 IEV similarity，并能覆盖 active compound 的 chemical space。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.6]；[doi:10.1021/acs.jcim.4c00842, p.7]；[doi:10.1021/acs.jcim.4c00842, p.8]
- **results：** Figure 5 给出了 DRD2 的代表性 docking poses，说明在低结构相似度候选中仍可找到与 seed 相近的相互作用模式。
  - 证据：[doi:10.1021/acs.jcim.4c00842, p.8]

## 页码证据

- [doi:10.1021/acs.jcim.4c00842, p.1]
- [doi:10.1021/acs.jcim.4c00842, p.3]
- [doi:10.1021/acs.jcim.4c00842, p.4]
- [doi:10.1021/acs.jcim.4c00842, p.6]
- [doi:10.1021/acs.jcim.4c00842, p.7]
- [doi:10.1021/acs.jcim.4c00842, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
