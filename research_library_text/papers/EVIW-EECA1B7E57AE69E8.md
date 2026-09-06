# A dual diffusion model enables 3D molecule generation and lead optimization based on target pockets

- **论文 ID：** `EVIW-EECA1B7E57AE69E8`
- **期刊 / 来源：** Nat Commun
- **发表时间：** 2024 Mar 26
- **DOI：** [10.1038/s41467-024-46569-1](https://doi.org/10.1038/s41467-024-46569-1)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `扩散/生成`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 PMDM 这一 pocket-conditioned 的双扩散模型，结合语义与空间条件编码、local/global edge 建模和等变生成机制，实现 one-shot 的 3D 分子生成，并在 Mpro 与 CDK2 案例中展示了可用于 lead optimization 的生成与体外验证能力。

## 创新边界

`创新主要在条件扩散框架与口袋几何建模的组合，冻结证据中没有独立 prior-art 证据来验证其全球首创性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在给定目标蛋白口袋的条件下，高效生成三维小分子，并进一步支持 lead optimization、scaffold hopping 与 linker generation，同时兼顾结合亲和力、几何合理性和可合成性。

## 方法

- 在固定蛋白口袋条件下联合扩散原子类型/坐标，双编码器分别处理局部与全局动力学；通过mask固定片段或连接点实现scaffold hopping和macrocycle linker生成。

## 数据与基准

- CrossDocked2020原始22.5 million对接对，经RMSD和30%序列聚类得到100,000训练/100评估对；另用Mpro和CDK2做先导生成/优化并合成少量候选。

## 比较基线

- 比较多种自回归和口袋条件生成方法，正文重点讨论Pocket2Mol等及其误差累积/采样复杂度。

## 结果证据

- 在大多数表格指标上优于基线，但SA与Diversity不是最佳；生成10,000分子比较显示速度/亲和力优势；选定CDK2分子经体外实验均显示改善的CDK2活性及适当CDK1选择性。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 论文未集中列出自述限制；表格显示可合成性和多样性并非领先，且大量结论依赖Vina/MM-PBSA；湿实验只覆盖有限CDK1/2候选，跨靶点泛化仍不足。

## 仍未知

- 冻结证据未提供独立第三方复现实验或更大规模外部基准复核。
- 代码可达性与运行环境未在本次审阅中实际验证。
- 文中只展示 CDK2 的体外结果，Mpro case 主要是计算评估。

## Pi 结构化证据摘录

- **baseline：** CrossDocked 评测基线包括 CVAE、AR-SBDD 与 DiffSBDD，其中 CVAE/AR-SBDD 是 autoregressive，DiffSBDD 是 diffusion model。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.4]；[doi:10.1038/s41467-024-46569-1, p.15]
- **baseline：** 与基线相比，PMDM 在 Vina Score 上优于 AR-SBDD 和 DiffSBDD，并且在采样速度上明显快于 autoregressive 方法与 DiffSBDD。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.4]；[doi:10.1038/s41467-024-46569-1, p.5]
- **data：** 主实验数据来自 CrossDocked，文中按 RMSD<1 Å 和 30% sequence identity 聚类后得到 100,000 对训练样本和 100 对评测样本。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.11]
- **data：** 案例结构使用 PDB 7L11 的 SARS-CoV-2 Mpro 和 PDB 8H6T 的 CDK2 复合物，分别服务于 lead generation、scaffold hopping 与 linker generation。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.10]；[doi:10.1038/s41467-024-46569-1, p.15]
- **data：** 作者把生成数据与处理后的训练/测试数据公开到 Zenodo，并在文中同时给出 GitHub 与 Zenodo 的代码地址。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.15]
- **declared_resources：** 论文公开了生成数据、处理后的训练/测试数据，并提供 GitHub 与 Zenodo 代码仓库链接。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.15]
- **declared_resources：** 研究获得 NSFC、HK RGC、CityU 与 ITC 等资助，并声明部分工作在 Tencent AI Lab 实习期间完成。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.15]
- **limitations：** 作者的验证主要集中在 CrossDocked 与 Mpro/CDK2 两类案例，冻结证据中没有更大规模的独立外部 wet-lab 泛化测试，因此推广范围仍需谨慎。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.4]；[doi:10.1038/s41467-024-46569-1, p.10]；[doi:10.1038/s41467-024-46569-1, p.11]
- **limitations：** 生成后的化学键依赖 OpenBabel 按距离重建，说明模型并非完全端到端地直接输出最终分子图。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.3]；[doi:10.1038/s41467-024-46569-1, p.14]
- **method：** PMDM 先分别用两个 SchNet 编码 ligand 与 pocket 的 3D 原子特征，再通过 cross-attention 将口袋语义上下文注入生成过程。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.12]
- **method：** 模型把分子视为 3D point cloud，并按阈值构造 local edges（<3 Å）与 global edges（3–6 Å）来区分共价键与远程作用。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.13]
- **method：** 双 equivariant encoder 采用 EGNN，只更新 ligand 坐标、保持 protein 位置固定，以维持 SE(3) 等变性与口袋约束。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.13]
- **method：** 训练目标来自 diffusion 的 ELBO/score matching；采样支持 from scratch、given fragments 和 linker generation 三种流程，最后用 OpenBabel 按原子距离重建键。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.12]；[doi:10.1038/s41467-024-46569-1, p.14]；[doi:10.1038/s41467-024-46569-1, p.3]
- **results：** 在 CrossDocked 总体指标上，PMDM 的 Vina Score 为 -7.572±2.50，High Affinity 为 0.628，QED 为 0.594±0.12，Lipinski 为 4.975±0.16，采样时间为 906±110 s，整体优于 baseline。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.5]
- **results：** 局部几何上，PMDM 仅有 2% 分子含 three-atom rings，远低于 CVAE/AR-SBDD/DiffSBDD 的 36.1%/48.4%/44.4%，且 bond angle 与 dihedral angle 的 KL divergence 最低。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.5]
- **results：** 化学空间分析显示 PMDM 在 Morgan、RDKit、USRCAT 以及 PMI/PBF 形状分布上更接近 test set，同时还能探索更广的 3D 形状范围。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.6]；[doi:10.1038/s41467-024-46569-1, p.7]
- **results：** Mpro lead generation 中，40,000 个候选筛出 10,627 个高亲和分子；CDK2 scaffold hopping 中，4 个候选都提升了 CDK2 活性且至少约 44-fold 选择 CDK1。
  - 证据：[doi:10.1038/s41467-024-46569-1, p.10]；[doi:10.1038/s41467-024-46569-1, p.11]

## 页码证据

- [doi:10.1038/s41467-024-46569-1, p.11]
- [doi:10.1038/s41467-024-46569-1, p.14]
- [doi:10.1038/s41467-024-46569-1, p.1]
- [doi:10.1038/s41467-024-46569-1, p.4]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
