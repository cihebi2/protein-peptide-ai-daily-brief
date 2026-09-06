# FLOWR.ROOT – A flow matching-based foundation model for joint multi-purpose structure-aware 3D ligand generation and affinity prediction

- **论文 ID：** `EVIW-3AE9D036AE8EC1CB`
- **期刊 / 来源：** Nat Commun
- **发表时间：** 2026 Jul 6
- **DOI：** [10.1038/s41467-026-74130-9](https://doi.org/10.1038/s41467-026-74130-9)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `扩散/生成` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称提出 FLOWR.ROOT，一个 SE(3)-equivariant flow matching foundation model，把 pocket-aware 3D ligand generation、pIC50/pKi/pKd/pEC50 affinity prediction、pLDDT confidence estimation，以及 fragment growing/replacement 和 importance-sampling guidance 统一到单一 backbone 中。

## 创新边界

`相对前作 FLOWR，主要新增点是把多端点 affinity head、confidence head、mixed isotropic-anisotropic priors、three-stage training、LoRA 适配和多目标 steering 组合进同一体系；本文更像是系统性整合与扩展，而不是引入全新的物理原理。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在结构基础药物设计中，同时实现口袋条件化的3D配体生成、binding affinity 预测、局部片段编辑与项目级 SAR 适配，并尽量保持几何合理性与可用的设计效率。

## 方法

- 三阶段预训练/高质量精修/LoRA项目适配，mixed isotropic-anisotropic prior与importance guidance。

## 数据与基准

- 数十亿ligand conformations、数百万混合质量complexes、co-crystal和项目数据。

## 比较基线

- Boltz-2、3D diffusion/flow和affinity模型。

## 结果证据

- 论文报告多任务benchmark与项目适配优势；均为生成/预测，无实验合成活性。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 需已知且最好holo pocket，protein flexibility未建模；公共benchmark不保证新SAR泛化。

## 仍未知

- FEP+/OpenFE 评测与训练语料的重叠程度无法从论文中精确量化。
- 四个内部项目的具体 assay 设计、噪声结构和外部可复现性未公开。
- LoRA 与 importance sampling 在真实前瞻药物项目中的增益还缺少独立复核。

## Pi 结构化证据摘录

- **baseline：** 在 SPINDR 的 pocket-conditional generation 上，FLOWR.ROOT base 相比 PILOT 和 FLOWR 在 PoseBusters-validity、strain energy 与 Vina score 上都更好。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.4]
- **baseline：** 在 affinity prediction 上，论文对比 OpenFE、FEP+、AEV-PLIG 和 Boltz-2；FLOWR.ROOT 的相关性指标整体更强，但作者自己的表格也显示 FEP+ 在 RMSE 上略优。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.5]；[doi:10.1038/s41467-026-74130-9, p.7]
- **baseline：** 在内部项目 zero-shot 测试里，Boltz-2 与 FLOWR.ROOT 都表现很差，作者随后用 LoRA-finetuned FLOWR.ROOT 才恢复了可用的相关性。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.6]；[doi:10.1038/s41467-026-74130-9, p.8]
- **baseline：** 在 PDE10A benchmark 上，论文把结果与 2D3D hybrid 和 Boltz-2 对比，LoRA-FLOWR.ROOT 在四个 split 上都排第一。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.8]
- **data：** Stage 1 预训练数据包括 ZINC3D、PubChem3D、Enamine REAL、OMol25 的海量小分子构象，以及 BindingNet、SAIR、KIBA-3D、Davis-3D、Kinodata-3D、Plinder 和 BindingMOAD 的混合 fidelity protein-ligand complexes。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.2]；[doi:10.1038/s41467-026-74130-9, p.13]
- **data：** 评测覆盖 GEOM-DRUGS、CROSSDOCKED2020、SPINDR、HIQBIND、FEP+/OpenFE IndustryBenchmark、PDE10A，以及 TYK2、ERα、BACE1 和 CK2α/CLK3 等案例。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.4]；[doi:10.1038/s41467-026-74130-9, p.5]；[doi:10.1038/s41467-026-74130-9, p.8]；[doi:10.1038/s41467-026-74130-9, p.9]；[doi:10.1038/s41467-026-74130-9, p.10]；[doi:10.1038/s41467-026-74130-9, p.11]
- **data：** 四个内部 project 数据集分别包含 1,073、730、229 和 618 个化合物，标签为 pIC50 或 pEC50，并用于 LoRA finetuning。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.6]；[doi:10.1038/s41467-026-74130-9, p.8]
- **data：** 作者对所有 protein-ligand 数据集沿用 Plinder 的 train/validation/test split，并用 sequence、pocket Jaccard、PLIP interaction 与 ligand Tanimoto 等相似度指标减少 leakage。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.4]
- **declared_resources：** 作者声明模型约有 33M trainable parameters，训练在单个 NVIDIA H100 节点（8 张 H100 GPUs）上完成。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.13]
- **declared_resources：** 论文声明 source code 已公开在 GitHub，并且精确版本已归档到 Zenodo；源码许可为 MIT licence。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.17]
- **declared_resources：** 论文还声明 curated training data、model checkpoints 和 generated ligand sets 也已托管到 Zenodo/Google Drive。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.17]
- **limitations：** 作者明确承认 public datasets 存在噪声、蛋白家族偏置和化学多样性不均等问题。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.12]
- **limitations：** 高 fidelity 数据规模仍然有限，因此 project-specific adaptation 依赖足够的 assay data，否则容易 overfitting 到窄分布。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.12]
- **limitations：** 模型需要已知 binding pocket，且最好是 holo conformation；pocket flexibility 仍未被显式建模。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.12]
- **limitations：** 作者也强调，FLOWR.ROOT 的预测只是 in silico approximation，不能替代实验验证。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.12]
- **limitations：** FEP+/OpenFE benchmark 可能与训练数据在 ligand 和 target space 上有重叠，因此这些结果不宜被解读为强的 out-of-distribution generalization。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.5]
- **limitations：** 在四个内部项目上，zero-shot generalization 失败，进一步说明模型需要依赖项目级校准而不是单次训练后直接泛化。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.6]；[doi:10.1038/s41467-026-74130-9, p.8]
- **method：** 模型以 SE(3)-equivariant flow matching backbone 为核心，将 pocket encoder、ligand decoder、structure head、四个 affinity heads 和 pLDDT confidence head 统一到一个架构中。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.2]；[doi:10.1038/s41467-026-74130-9, p.15]
- **method：** 训练分三阶段：先在约 1.5B 小分子构象与约 2.5M protein-ligand complexes 上预训练，再用 SPINDR 和 HIQBIND 微调，最后用 LoRA 做项目级适配。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.2]；[doi:10.1038/s41467-026-74130-9, p.13]
- **method：** 生成模式覆盖 de novo、interaction/pharmacophore-conditional、scaffold hopping/elaboration 以及 fragment growing/replacement，并通过 mixed isotropic-anisotropic priors 与 reference-ligand-based prior placement 强化局部编辑。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.3]；[doi:10.1038/s41467-026-74130-9, p.14]
- **method：** 损失函数把坐标 MSE、atom/bond/charge/hybridization CE 与 bond length/angle 监督合并，affinity 头则分别对 pIC50、pKi、pKd 和 pEC50 使用 Huber loss。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.13]；[doi:10.1038/s41467-026-74130-9, p.15]
- **method：** 推理时通过 importance sampling 与 sequential Monte Carlo 对生成轨迹做 steering，从而实现单目标和多目标优化，而不依赖外部 scoring function。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.3]；[doi:10.1038/s41467-026-74130-9, p.16]
- **results：** 在 GEOM-DRUGS 上，non-pretrained FLOWR.ROOT base 达到 0.94 ± 0.02 的 PoseBusters-validity，优于对比方法，并给出 median relaxation energy 3.65 ± 0.2 kcal/mol 和 RMSD 0.07 ± 0.02 Å。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.4]
- **results：** 在 CROSSDOCKED2020 上，FLOWR.ROOT base 的 PoseBusters-validity 为 0.97 ± 0.22，strain energy 为 67.13 ± 53.05 kcal/mol，AutoDock-Vina score 为 -7.76 ± 0.55 kcal/mol。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.4]
- **results：** 在 HIQBIND 上，pIC50 预测的 Pearson 达到 0.92 ± 0.03、R2 达到 0.85 ± 0.06；按 affinity types 取 median 后，Pearson 为 0.76 ± 0.07、RAE 为 0.58 ± 0.06。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.4]；[doi:10.1038/s41467-026-74130-9, p.5]
- **results：** importance-sampling guidance 会把 HIQBIND 上生成分子的 mean predicted pIC50 从 5.60 ± 1.11 推到 6.02（steering duration 0.5），同时样本 diversity 基本保持不变。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.5]
- **results：** 在 FEP+/OpenFE 上，模型报告 RMSE 0.93 ± 0.05 kcal/mol、Pearson 0.86 ± 0.02、Kendall τ 0.65 ± 0.03。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.5]；[doi:10.1038/s41467-026-74130-9, p.7]
- **results：** LoRA finetuning 后，四个内部项目的 R2 提升到 0.73、0.45、0.28 和 0.45，Pearson 分别达到 0.86、0.70、0.56 和 0.69。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.8]
- **results：** 在 PDE10A 上，LoRA-FLOWR.ROOT 于 random split 达到 RMSE 0.32 ± 0.06、Spearman 0.97 ± 0.01；在 temporal 2013 split 上达到 RMSE 0.44 ± 0.16、Spearman 0.95 ± 0.04。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.8]
- **results：** CK2α/CLK3 的 joint optimization 使 off-target CLK3 predicted pIC50 降到 6.03，而 single optimization 为 6.72，同时保留了 CK2α potency。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.8]；[doi:10.1038/s41467-026-74130-9, p.9]
- **results：** TYK2、ERα、BACE1 的 QM validation 显示，FLOWR.ROOT 预测与 GFN2-xTB binding energies 存在中高相关，作者据此认为模型学到了关键 hinge-binding 与 aromatic stacking motif。
  - 证据：[doi:10.1038/s41467-026-74130-9, p.9]；[doi:10.1038/s41467-026-74130-9, p.10]；[doi:10.1038/s41467-026-74130-9, p.11]

## 页码证据

- [doi:10.1038/s41467-026-74130-9, p.12]
- [doi:10.1038/s41467-026-74130-9, p.1]
- [doi:10.1038/s41467-026-74130-9, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
