# A pharmacophore-guided deep learning approach for bioactive molecular generation

- **论文 ID：** `EVIW-AABC81152A5D218D`
- **期刊 / 来源：** Nat Commun
- **发表时间：** 2023 Oct 6
- **DOI：** [10.1038/s41467-023-41454-9](https://doi.org/10.1038/s41467-023-41454-9)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

论文提出 PGMG：把 pharmacophore 编成带节点/边属性的完全图，用 Gated-GCN 与 transformer encoder-decoder 结合 latent variable，直接按 pharmacophore 生成分子，并声称可在 ligand-based 与 structure-based 场景下灵活生成高质量 bioactive molecules。

## 创新边界

`边界在于：论文主张的是一种 pharmacophore-guided 生成框架与其案例验证，不是新湿实验。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在活性数据稀缺、甚至新靶点家族信息不足的情况下，如何按给定 pharmacophore 约束生成具有目标 bioactivity 的新分子。

## 方法

- 从分子构造含药效团类型和节点间距离的完全图，条件VAE式编码潜变量，Transformer自回归解码随机SMILES；用无条件GuacaMol式指标、药效团匹配、15靶点Vina对接、ADMET代理与案例研究评估。

## 数据与基准

- ChEMBL 24超过125万分子用于主训练；ZINC约22万分子用于消融；从随机药效团生成236,000个分子做匹配分析，并对15个靶点各生成10,000个分子。

## 比较基线

- 无条件生成基线包括VAE、ORGAN、SMILES LSTM、SyntaLinker；靶向生成比较包括RELATION等方法以及Pocket2Mol/Seq2Seq的代码运行结果。

## 结果证据

- PGMG在无条件比较中取得最佳新颖性和可用分子比例，可用分子比例比比较方法提高6.3%；15靶点上生成分子的top-1000 Vina分布与已知活性分子相近，并报告较高药效团匹配、有效性、唯一性和新颖性。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 结合能力主要由AutoDock Vina代理，正文未报告生成分子的合成和生化/细胞验证。 无条件评估通过随机采样药效团近似，对条件模型并非完全等价的任务比较。 训练高度依赖ChEMBL分布与药效团抽取规则，未知靶点的真实外推和负样本偏差未被充分解决。

## 仍未知

- 是否存在可复现的独立实现或稳定运行的公开服务，冻结文本未核实。
- 文中 case study 主要依赖计算与 docking 证据，未见新的湿实验验证。
- 与更广泛 prior-art 相比，该框架的全球新颖性无法仅凭论文自证。

## Pi 结构化证据摘录

- **baseline：** 无条件生成部分对比了 VAE、ORGAN、SMILES LSTM 和 SyntaLinker。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.3]
- **baseline：** bioactive generation 部分对比了 RELATION、Pocket2Mol 和 Seq2Seq，并引用了 RELATIONphar / RELATIONphar-BOdock 的结果。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.4]；[doi:10.1038/s41467-023-41454-9, p.6]
- **baseline：** 论文声称 PGMG 在 novelty、available ratio 和部分 docking 指标上优于这些基线，同时保持较好的 validity 与 uniqueness。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.3]；[doi:10.1038/s41467-023-41454-9, p.6]
- **data：** 训练数据使用 ChEMBL 24，规模超过 1.25 million molecules；消融实验另用 ZINC 数据集 220,000 molecules。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.8]
- **data：** 评估与案例覆盖 15 个靶点结构，包括 FGFR1、ACHE、MDM2-P53、PARP1、NS5B、HSP90、BACE1、PRKCQ、PIM1、CDK2、BRD4、VEGFR2、CDK6、TGFB1 和 AKT1。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.8]
- **data：** 实现与评测依赖 RDKit、AutoDock Vina、ADMETlab 2.0、PDB 结构以及基于 SMILES 的分子表示和 tokenization。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.8]；[doi:10.1038/s41467-023-41454-9, p.9]
- **declared_resources：** 论文声明代码与数据可在 GitHub 仓库和 Zenodo 中获取，并提供了 PGMG web server。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.7]；[doi:10.1038/s41467-023-41454-9, p.9]
- **declared_resources：** Source data、生成分子以及训练/评测所需的数据文件也被声明随论文提供。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.9]
- **declared_resources：** 作者在方法页给出了实现所用的主要依赖：Gated-GCN、transformer、RDKit、AutoDock Vina、ADMETlab 2.0。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.2]；[doi:10.1038/s41467-023-41454-9, p.8]；[doi:10.1038/s41467-023-41454-9, p.9]
- **limitations：** 作者明确说明 PGMG 当前不支持 pharmacophore 的 exclusion volume。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.7]
- **limitations：** 模型也没有显式约束生成分子的整体性质，后续计划引入 exclusion volume 和更多可控特征。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.8]
- **limitations：** 输出质量高度依赖用户构建的 pharmacophore hypothesis，论文也建议用 QSAR 等方法进一步修正 hypothesis。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.7]
- **method：** 将 pharmacophore hypothesis 表示为完全图，节点对应化学特征、边对应空间距离，再用 Gated-GCN 编码这些结构化约束。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.2]；[doi:10.1038/s41467-023-41454-9, p.8]
- **method：** 用 transformer 作为生成骨干，并引入 latent variable z 处理 pharmacophore 与 molecule 之间的 many-to-many 映射。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.2]；[doi:10.1038/s41467-023-41454-9, p.8]
- **method：** 训练时把分子 SMILES 随机化并做 in-filling corruption，联合优化 KL loss、language modelling loss 和 mapping loss。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.2]；[doi:10.1038/s41467-023-41454-9, p.8]；[doi:10.1038/s41467-023-41454-9, p.9]
- **results：** 在无条件生成任务上，PGMG 的 validity 为 0.982、uniqueness 为 0.979、novelty 为 0.976、ratio of available molecules 为 0.938，在 novelty 与 available ratio 上最好。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.3]
- **results：** 用随机 pharmacophore 生成的约 236,000 个分子中，83.6% 的 match score 高于 0.8，78.6% 达到 1.0；随机分子仅 4.91% 达到 1.0。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.3]
- **results：** 在 CDK2 与 AKT1 的对比实验中，PGMG 取得最高或并列最优的 available ratio，并维持较强 docking score 与较低计算时间。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.6]
- **results：** 案例研究显示，PGMG 还能在 SBDD、LBDD 与 scaffold hopping 中生成与参考配体相容、且具新 scaffold 的候选分子。
  - 证据：[doi:10.1038/s41467-023-41454-9, p.4]；[doi:10.1038/s41467-023-41454-9, p.6]；[doi:10.1038/s41467-023-41454-9, p.7]

## 页码证据

- [doi:10.1038/s41467-023-41454-9, p.1]
- [doi:10.1038/s41467-023-41454-9, p.2]
- [doi:10.1038/s41467-023-41454-9, p.3]
- [doi:10.1038/s41467-023-41454-9, p.4]
- [doi:10.1038/s41467-023-41454-9, p.8]
- [doi:10.1038/s41467-023-41454-9, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
