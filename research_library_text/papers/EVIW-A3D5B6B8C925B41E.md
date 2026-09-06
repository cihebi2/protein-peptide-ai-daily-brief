# Geometric deep learning improves generalizability of MHC-bound peptide predictions

- **论文 ID：** `EVIW-A3D5B6B8C925B41E`
- **期刊 / 来源：** Commun Biol
- **发表时间：** 2024 Dec 19
- **DOI：** [10.1038/s42003-024-07292-1](https://doi.org/10.1038/s42003-024-07292-1)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `图与几何学习`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

论文提出三类 supervised structure-based 模型（3D-CNN、GNN、EGNN）以及一个 self-supervised 的 3D-SSL-EGNN，在 allele-clustered 设定下提升对未见 allele 的泛化；同时用 HBV vaccine case study 展示结构信息可缓解序列方法继承的数据偏差，并强调结构式学习的数据效率优势。

## 创新边界

`冻结材料只支持作者声称的局部方法组合与评估框架；未见独立 prior-art 证据，因此不能把全球首创视为已验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

作者要解决的是 MHC-bound peptide prediction 在未见 HLA allele、低数据情境和数据偏差下泛化不足的问题，并比较 structure-based GDL 是否能比传统 sequence-based 方法更稳健。

## 方法

- 以pMHC三维模型构建残基图，采用等变/几何网络和3D自监督预训练，再进行结合预测与HLA簇划分评估。

## 数据与基准

- 覆盖多等位基因结合/非结合肽、3D模型、HLA簇，并以乙肝疫苗免疫肽组案例检验数据偏差。

## 比较基线

- 序列MLP、MHCFlurry及无3D自监督/不同几何组件的模型。

## 结果证据

- 论文报告无结合亲和力标签预训练的3D-SSL超过使用约90倍更多数据的序列方法，并在未见HLA上更稳健；属于计算预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 作者指出临床案例队列有限且需更大队列验证；三维模型误差和HLA覆盖仍限制泛化。

## 仍未知

- 外部独立队列上的泛化性能未在冻结材料中得到验证。
- AUPRC 在更强类别不平衡下的表现不清楚。
- 3D-SSL 对其他 PPI 场景的迁移效果仍未知。
- 代码与数据虽已声明可得，但静态可用不等于已成功复现。

## Pi 结构化证据摘录

- **baseline：** 主要 sequence-based baseline 是 MLP 和重训的 MHCFlurry 2.0，作者用它们对照 supervised structure-based 模型。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.2]；[doi:10.1038/s42003-024-07292-1, p.8]
- **baseline：** HBV vignette 的外部对照方法是 NetMHCpan4.1b 与 MHCFlurry 2.0 official release。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.6]；[doi:10.1038/s42003-024-07292-1, p.9]
- **baseline：** 论文还把 3pHLA、Wilson et al. 的 electrostatic CNN 和 MHCfold 作为既有 structure-based 工作背景，用来定位自身方法。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.2]
- **data：** 主数据集来自 100,178 条 human BA measurements，覆盖 110 个 HLA alleles，阈值 500 nM 划分 binders 与 non-binders，其中 44,102 为 binders、56,076 为 non-binders。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.6]
- **data：** Allele-clustered 划分中，作者按 HLA-A / -B / -C 分别取约 10% / 11% / 12% 的远端 cluster 作为 test set，HLA-E 的 37 个 case 因无法聚类而留在 train/validation。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.8]
- **data：** 3D-SSL 的训练资源来自 1,245 个 X-ray structures：517 个 pMHC 结构与 731 个 TCR-peptide 结构，均从 ProtCID 与 Propedia 交叉提取。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.8]
- **data：** HBV case study 的实验数据来自 6 名健康供体的 LC-MS/MS immunopeptidomics，供体 DCs 接触 12 条 HBV synthetic long peptides。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.9]
- **declared_resources：** 作者声明 BA data、3D models、allele clusters、trained networks 和 network outputs 已发布到 Zenodo。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.10]
- **declared_resources：** Methods 中还明确列出了 PANDORA、GradPose、DeepRank / DeepRank2、scipy、PyTorch 等工具链，用于结构建模、对齐、featurization 与训练。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.7]；[doi:10.1038/s42003-024-07292-1, p.8]；[doi:10.1038/s42003-024-07292-1, p.9]
- **declared_resources：** 代码可用性部分声明 data generation、featurization 和 training 的代码在 GitHub 与 Zenodo，且论文注明了对应记录。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.11]
- **declared_resources：** 作者还致谢了 NVIDIA Academic Hardware Grant Program 与 SurfSara GPU/CPU supercomputing grants 作为计算资源。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.12]
- **limitations：** 作者明确提示 AUPRC 在真实世界的高度类别不平衡场景下可能不同，因此文中指标不能直接外推到稀有阳性率任务。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.4]
- **limitations：** 3D-SSL 若只在 3D models 上训练而不是 X-ray structures，上限明显下降到 AUC 0.56±0.01，说明它依赖高质量结构。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.5]
- **limitations：** HBV case study 只用了 6 名供体，作者也承认需要更大 cohort 才能支持更广泛泛化。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.10]
- **limitations：** 3D-SSL 目前只在 pMHC complexes 上验证，对其他 protein-protein interfaces 的效果仍未证实。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.5]；[doi:10.1038/s42003-024-07292-1, p.12]
- **method：** 作者先从 MHCFlurry 2.0 下载并筛选 human pMHC binding affinity 数据，再按 HLA pseudosequence 做 allele clustering，构造 shuffled 与 allele-clustered 两种评估划分。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.2]；[doi:10.1038/s42003-024-07292-1, p.8]
- **method：** 每个 pMHC 复合物都通过 PANDORA 生成 3D models，并分别送入 3D-CNN、residue-level GNN 与 EGNN；其中 EGNN 以 residue type、xyz coordinates 和 cross-chain 标记作为核心输入。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.6]；[doi:10.1038/s42003-024-07292-1, p.7]；[doi:10.1038/s42003-024-07292-1, p.8]
- **method：** 论文以 MLP 和重训的 MHCFlurry 2.0 作为 sequence-based baseline；MLP 使用 BLOSUM62、HLA pseudosequence 与 15-mer peptide encoding。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.2]；[doi:10.1038/s42003-024-07292-1, p.8]
- **method：** 3D-SSL 采用 masked residue prediction 训练 EGNN，再把 masked residue 的概率经 Boltzmann distribution 转成 statistical potential，用作 binding affinity 预测分数。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.4]；[doi:10.1038/s42003-024-07292-1, p.5]
- **method：** HBV case study 中，作者把训练好的 structure-based 模型用于 HLA-A*02:01 条件下的 HL/HG peptide 评分，并与 NetMHCpan4.1b 和 MHCFlurry 2.0 作比较。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.6]；[doi:10.1038/s42003-024-07292-1, p.9]
- **results：** 在 shuffled split 上，所有方法都表现较好；MLP 的 AUC 达到 0.91，EGNN 约 0.87，说明高相似度测试集会让序列方法看起来很强。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.3]
- **results：** 在 allele-clustered split 上，所有模型都明显退化，但 structure-based 方法整体比 sequence-based 方法高出约 5–11% AUC，EGNN 在 AUC/AUPRC 上领先约 8–11%。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.4]
- **results：** 3D-SSL 只用约 1,245 个 X-ray complexes、且未见任何 BA data，就能超过训练于 >90K BA points 的 sequence-based 方法；而 supervised EGNN 约需 10,000 条 BA 数据才可稳定超过 3D-SSL。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.4]；[doi:10.1038/s42003-024-07292-1, p.5]
- **results：** 把 peptide-TCR structures 加入 3D-SSL 预训练后，AUC 从 0.640±0.011 提升到 0.668±0.005，显示竞争性结合环境信息可能有帮助。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.5]
- **results：** 在 HBV case study 中，作者的 StrB 模型成功把 HL 与 glycine-extended 的 HG 都判为 binder，而 NetMHCpan4.1b 和 MHCFlurry 2.0 只判了 HL。
  - 证据：[doi:10.1038/s42003-024-07292-1, p.6]

## 页码证据

- [doi:10.1038/s42003-024-07292-1, p.10]
- [doi:10.1038/s42003-024-07292-1, p.1]
- [doi:10.1038/s42003-024-07292-1, p.4]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
