# CycPeptMP: enhancing membrane permeability prediction of cyclic peptides with multi-level molecular features and data augmentation

- **论文 ID：** `EVIW-7D1ADFC98AF15650`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2024 Aug 29
- **DOI：** [10.1093/bib/bbae417](https://doi.org/10.1093/bib/bbae417)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 CycPeptMP，一个面向 cyclic peptides 膜渗透性回归预测的深度学习框架，结合 atom、monomer、peptide 三层特征、辅助损失与数据增强，以提升准确率和泛化性能。

## 创新边界

`创新主要是任务特化的多层特征融合与增强策略，不是新分子生成或候选优化方法。`。这不是全球首创性检索或独立复现结论。

## 研究问题

现有 cyclic peptide 膜渗透性预测方法受限于实验数据稀缺、不同 assay 体系带来的标签噪声，以及常规模型偏向 whole-molecule 特征而忽略 cyclic peptide 的序列与环状结构特性。

## 方法

- 原子级图模型、单体级表示和整肽2D/3D描述符分别编码，再融合回归；多构象平均和三层数据增强；消融分析。

## 数据与基准

- CycPeptMPDB 7,334条环肽，来源45篇论文和2项专利，含PAMPA、Caco-2、MDCK等不同测定；超过99.6%含非天然氨基酸。

## 比较基线

- Morgan指纹RF、2D/3D描述符SVM、MAT、SAT等7个基线及MD方法。

## 结果证据

- 融合模型报告LogPexp MAE 0.355、相关系数0.883；三级特征和增强均有贡献，并在若干MD难例上给出较好预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 不同实验体系造成标签异质；同系列环肽仅少数残基变化，随机拆分可能高估泛化；构象生成与增强可能引入近邻依赖。

## 仍未知

- 不同 assay 条件导致的标签噪声上限未被定量拆分。
- RDKit 生成构象与真实膜环境构象分布的偏差未被独立验证。
- 论文声称代码已开源，但本次只读到论文文本，未核验仓库实现细节。

## Pi 结构化证据摘录

- **baseline：** 传统 baseline 包括 RF、SVM-2D 和 SVM-2D3D，分别基于 Morgan FP 或 2D/3D peptide descriptors。
  - 证据：[doi:10.1093/bib/bbae417, p.6]；[doi:10.1093/bib/bbae417, p.7]
- **baseline：** 深度学习 baseline 包括 MAT、SAT、PharmHGT 和 FinGAT，代表结构感知 transformer 与 heterogeneous graph 路线。
  - 证据：[doi:10.1093/bib/bbae417, p.6]；[doi:10.1093/bib/bbae417, p.7]
- **baseline：** 在 test set 上，SVM-2D3D 是传统方法里最强者，但 MAE=0.418，仍落后于 CycPeptMP。
  - 证据：[doi:10.1093/bib/bbae417, p.7]
- **baseline：** 在 10-fold cross-validation 中，PharmHGT 与 FinGAT 也未超过 CycPeptMP。
  - 证据：[doi:10.1093/bib/bbae417, p.9]
- **data：** 实验数据来自 CycPeptMPDB，作者称其包含 7334 个 cyclic peptides 的结构与膜渗透实验值，来源于 45 篇论文和 2 项专利。
  - 证据：[doi:10.1093/bib/bbae417, p.2]
- **data：** 本研究选用 PAMPA 条目，共 6889 个 peptide，并将低于 -8 的 LogPexp 统一截断到 -8，另将一个高于 -4 的值截断到 -4。
  - 证据：[doi:10.1093/bib/bbae417, p.2]
- **data：** 测试集由 KS 算法按 Morgan fingerprint 最大化距离抽取 344 个样本，另外三次随机抽取各 344 个 validation 样本。
  - 证据：[doi:10.1093/bib/bbae417, p.2]
- **data：** 特征工程依赖 RDKit、MOE 和 Mordred；peptide 与 monomer 先生成单构象 3D 结构，再计算 2D/3D descriptors，并配合 2048-bit Morgan FP。
  - 证据：[doi:10.1093/bib/bbae417, p.3]；[doi:10.1093/bib/bbae417, p.4]；[doi:10.1093/bib/bbae417, p.5]；[doi:10.1093/bib/bbae417, p.6]
- **declared_resources：** 论文声明结构与膜渗透数据来自 CycPeptMPDB，代码已发布于 GitHub。
  - 证据：[doi:10.1093/bib/bbae417, p.10]
- **declared_resources：** 研究获得 JSPS KAKENHI 与 AMED BINDS 资助。
  - 证据：[doi:10.1093/bib/bbae417, p.10]
- **declared_resources：** 实现与特征计算显式使用了 RDKit、MOE、Mordred 与 Optuna 等软件资源。
  - 证据：[doi:10.1093/bib/bbae417, p.3]；[doi:10.1093/bib/bbae417, p.6]
- **limitations：** 作者指出 CycPeptMPDB 来自多种文献和 assay 体系，同一 peptide 的 permeability 记录可能差异很大，标签噪声是重要限制。
  - 证据：[doi:10.1093/bib/bbae417, p.8]
- **limitations：** 对 LogPexp=-10 的条目，作者认为很多是数据库缺少明确测量而被赋值，可靠性较差，可能应当剔除。
  - 证据：[doi:10.1093/bib/bbae417, p.8]
- **limitations：** 作者承认 3D 信息带来的提升并不明显，且 RDKit 生成的构象可能不如更严格的 MD 构象采样。
  - 证据：[doi:10.1093/bib/bbae417, p.9]；[doi:10.1093/bib/bbae417, p.10]
- **limitations：** 数据增强在超过约 20 个 replicas 后收益趋于饱和，说明仅靠重排与单一构象扩增的多样性有限。
  - 证据：[doi:10.1093/bib/bbae417, p.9]
- **method：** 研究以 CycPeptMPDB 中的 cyclic peptide 膜渗透实验数据为基础，先构建回归任务，再用 Kennard–Stone 算法抽取独立测试集并做重复验证集划分。
  - 证据：[doi:10.1093/bib/bbae417, p.2]
- **method：** CycPeptMP 由 atom、monomer 和 peptide 三个子模型组成，最终将三层 latent feature 拼接后送入共享层得到膜渗透性预测值。
  - 证据：[doi:10.1093/bib/bbae417, p.3]；[doi:10.1093/bib/bbae417, p.6]
- **method：** atom 模型使用 transformer，并把 Bond、Graph 和 Conf 三类关系矩阵纳入注意力；monomer 模型使用 CNN 或 CyclicConv；peptide 模型用 descriptors 与 Morgan FP 的 MLP。
  - 证据：[doi:10.1093/bib/bbae417, p.4]；[doi:10.1093/bib/bbae417, p.5]；[doi:10.1093/bib/bbae417, p.6]
- **method：** 训练阶段引入 sub-model loss 与 layer loss 作为 auxiliary loss，以缓解梯度消失并强化中间表示学习。
  - 证据：[doi:10.1093/bib/bbae417, p.6]
- **method：** 数据增强包括 SMILES enumeration、按 cyclic 顺序做 monomer translation/rotation，以及每个 peptide 或 monomer 生成 60 个构象。
  - 证据：[doi:10.1093/bib/bbae417, p.6]
- **results：** 在 test set 上，CycPeptMP 的 MAE=0.355、MSE=0.253、R=0.883、R2=0.772，四项指标都优于所有 baseline。
  - 证据：[doi:10.1093/bib/bbae417, p.7]
- **results：** 在 10-fold cross-validation 上，CycPeptMP 仍然排名第一，MAE=0.352、R=0.786、R2=0.613。
  - 证据：[doi:10.1093/bib/bbae417, p.9]
- **results：** 与 MD-based method 对比时，23 个共享样本上 CycPeptMP 的 MAE=0.107，而该 MD 方法为 1.521。
  - 证据：[doi:10.1093/bib/bbae417, p.9]；[doi:10.1093/bib/bbae417, p.10]
- **results：** 消融实验表明三层特征都对性能有贡献，去掉任一子模型都会降效，辅助损失与数据增强也明显改善结果。
  - 证据：[doi:10.1093/bib/bbae417, p.8]；[doi:10.1093/bib/bbae417, p.9]

## 页码证据

- [doi:10.1093/bib/bbae417, p.10]
- [doi:10.1093/bib/bbae417, p.1]
- [doi:10.1093/bib/bbae417, p.2]
- [doi:10.1093/bib/bbae417, p.3]
- [doi:10.1093/bib/bbae417, p.6]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
