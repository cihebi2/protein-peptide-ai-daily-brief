# Complex-based Ligand-Binding Proteins Redesign by Equivariant Diffusion-based Generative Models

- **论文 ID：** `EVIW-42DB157D2A2CDE0F`
- **期刊 / 来源：** bioRxiv preprint（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1101/2024.04.17.589997](https://doi.org/10.1101/2024.04.17.589997)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `扩散/生成` / `图与几何学习` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出 ProteinReDiff，将 AF2 风格表示学习模块（SRA、OPU、triangle multiplicative updates）嵌入 equivariant diffusion 生成框架，在序列与结构两个空间联合去噪，实现仅基于蛋白序列与 ligand SMILES 的 ligand-binding protein redesign，并在计算评估中提升 binding affinity、sequence diversity 与 structure preservation。

## 创新边界

`创新边界主要是计算生成与重设计，不包含湿实验验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在缺少已知结合口袋与详细结构信息时，如何仅凭初始蛋白序列与 ligand SMILES 重新设计能够更好结合配体的 ligand-binding proteins。

## 方法

- 蛋白/配体双域加噪去噪，outer-product、single representation attention和triangle update融合pair特征。

## 数据与基准

- PDBBind及扩展蛋白-配体数据，受限于配对结构数量和多样性。

## 比较基线

- DPL、ProteinMPNN、CARP及相关设计模型。

## 结果证据

- 论文报告结合评分/结构/多样性优于所选模型；全部为计算生成与预测，无实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 配体配对训练数据有限、binding-site不确定，需高分辨率结构和结合实验验证；为预印本。

## 仍未知

- 未见湿实验或真实 binding assay。
- 未见独立第三方复现结果。
- 公开代码仓库是否完整包含可运行训练与评测流水线，单靠论文页内无法确认。

## Pi 结构化证据摘录

- **baseline：** 对照方法包括 CARP、MIF、MIF-ST、ESMIF、ProteinMPNN、LigandMPNN、Protein Generator 和 DPL。
  - 证据：[doi:10.1101/2024.04.17.589997, p.25]；[doi:10.1101/2024.04.17.589997, p.26]；[doi:10.1101/2024.04.17.589997, p.29]
- **baseline：** 作者强调 LigandMPNN 需要 binding pocket information，而 ProteinReDiff 只依赖 protein sequence 与 ligand SMILES，因此比较重点放在无 pocket 条件下的 redesign 能力。
  - 证据：[doi:10.1101/2024.04.17.589997, p.26]；[doi:10.1101/2024.04.17.589997, p.3]
- **data：** 训练数据主要来自 PDBBind v2020 与 CATH 4.2；前者提供 ligand-bound complexes，后者提供大量 protein structures。
  - 证据：[doi:10.1101/2024.04.17.589997, p.18]
- **data：** 作者使用 MMseqs2 做 protein clustering，并按 Morgan fingerprint 的 Tanimoto similarity 对 ligand 做聚类，PDBBind v2020 的划分为 9430/552/207，CATH 4.2 为 15261/939/-。
  - 证据：[doi:10.1101/2024.04.17.589997, p.18]；[doi:10.1101/2024.04.17.589997, p.19]
- **data：** CATH 4.2 只保留少于 400 aa 且 sequence similarity 低于 90% 的蛋白，训练和验证阶段的 ligand 以 '*' 作为 masked token。
  - 证据：[doi:10.1101/2024.04.17.589997, p.19]
- **declared_resources：** Protein featurization 使用 ESM-2，作者注明其为 650M parameters、预训练于近 65M UniRef sequences。
  - 证据：[doi:10.1101/2024.04.17.589997, p.9]
- **declared_resources：** 结构预测与打分分别使用 Omegafold 和 AutoDock Vina。
  - 证据：[doi:10.1101/2024.04.17.589997, p.24]
- **declared_resources：** 训练与划分依赖 PDBBind v2020、CATH 4.2、MMseqs2 以及 Morgan/Tanimoto clustering。
  - 证据：[doi:10.1101/2024.04.17.589997, p.18]；[doi:10.1101/2024.04.17.589997, p.19]
- **limitations：** 评估链条依赖 Omegafold 预测结构和 AutoDock Vina docking score，因而主要是计算代理评估，而不是直接的实验 binding assay。
  - 证据：[doi:10.1101/2024.04.17.589997, p.24]；[doi:10.1101/2024.04.17.589997, p.25]
- **limitations：** CATH 4.2 没有对应 ligands，因此被排除在 test set 之外，说明数据扩展并未覆盖完整的 ligand-conditioned 测试场景。
  - 证据：[doi:10.1101/2024.04.17.589997, p.19]
- **limitations：** 作者自己的结果也显示 masking ratio 与 affinity、diversity、structure preservation 之间存在明显权衡，过高 masking 会迅速损害结构保真。
  - 证据：[doi:10.1101/2024.04.17.589997, p.28]；[doi:10.1101/2024.04.17.589997, p.29]；[doi:10.1101/2024.04.17.589997, p.31]
- **method：** 模型以 masked protein sequence 和 ligand SMILES 作为输入，并构建单体表示、配对表示以及蛋白-配体联合表示。
  - 证据：[doi:10.1101/2024.04.17.589997, p.12]；[doi:10.1101/2024.04.17.589997, p.13]
- **method：** Residual feature update 中引入 Single Representation Attention、Outer Product Update 和 Triangle Multiplicative Updates，以增强蛋白与配体之间的长程依赖和几何约束建模。
  - 证据：[doi:10.1101/2024.04.17.589997, p.14]；[doi:10.1101/2024.04.17.589997, p.15]；[doi:10.1101/2024.04.17.589997, p.16]
- **method：** 最终的 equivariant denoising 通过 pair representation 生成噪声预测，并保持对旋转和平移的 SE(3)-equivariance。
  - 证据：[doi:10.1101/2024.04.17.589997, p.17]；[doi:10.1101/2024.04.17.589997, p.10]；[doi:10.1101/2024.04.17.589997, p.12]
- **method：** 训练目标由 L_WS、L_KL 和 L_CE 组成，分别约束结构去噪、序列分布匹配与 amino acid 分类。
  - 证据：[doi:10.1101/2024.04.17.589997, p.20]；[doi:10.1101/2024.04.17.589997, p.21]
- **results：** 在 Table 4 中，ProteinReDiff 的 15% masking 取得最佳 LBA，达到 -6.803 ± 0.329 kcal/mol，优于 reference cases 的 -5.847 ± 0.263 和 DPL 的 -5.551 ± 0.459。
  - 证据：[doi:10.1101/2024.04.17.589997, p.29]
- **results：** 15% masking 在 sequence diversity 与 structure preservation 之间形成最优折中；其 TM Score 为 0.845、RMSD 为 3.690 Å、CO 为 0.935，不是所有结构指标的绝对最优，但整体表现最好。
  - 证据：[doi:10.1101/2024.04.17.589997, p.29]；[doi:10.1101/2024.04.17.589997, p.28]
- **results：** 5% masking 更偏向结构保真（TM 0.864、RMSD 3.197、CO 0.942），而 60% 到 70% masking 会显著恶化结构指标。
  - 证据：[doi:10.1101/2024.04.17.589997, p.29]
- **results：** 作者还用 Gaussian Process 在 PDBBind v2020 上验证其 complex representation，报告 RMSE 1.443、MAE 1.168、Pearson 0.721、Spearman 0.639。
  - 证据：[doi:10.1101/2024.04.17.589997, p.33]

## 页码证据

- [doi:10.1101/2024.04.17.589997, p.1]
- [doi:10.1101/2024.04.17.589997, p.3]
- [doi:10.1101/2024.04.17.589997, p.7]
- [doi:10.1101/2024.04.17.589997, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
