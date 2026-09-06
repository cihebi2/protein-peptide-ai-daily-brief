# Identification of Novel Extracellular-Signal-Regulated Kinase 2 Inhibitors Through Machine Learning-Driven De Novo Design, Molecular Docking, and Free-Energy Perturbation

- **论文 ID：** `EVIW-7C59FBCE9E2F9366`
- **期刊 / 来源：** Pharmaceuticals (Basel)
- **发表时间：** 2026 Feb 20
- **DOI：** [10.3390/ph19020337](https://doi.org/10.3390/ph19020337)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者声称用 DeLA-Drug 从已知 ERK2 活性分子出发生成并筛选新化合物，最终得到 Ek1–Ek4，并通过 docking、ADMET、DiffDock、MD、MM-GBSA 与 FEP 证明其具有作为 ERK2 候选抑制剂的潜力。

## 创新边界

`新意主要在生成式扩增已知活性骨架并做多层级计算筛选；文中未见实验验证，因此不能据此确认全球新颖性或真实成药性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

围绕 ERK2 ATP-binding site 的新型小分子抑制剂发现，目标是缓解现有 ERK1/2 抑制剂在选择性、耐药、毒性与药代性质上的局限。

## 方法

- 生成、virtual screening、FEP ranking。

## 数据与基准

- ERK2 ligands/structure与generated molecules。

## 比较基线

- known ERK2 inhibitors和生成baselines。

## 结果证据

- 候选来自计算；无明确实验不写抑制剂实证。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- FEP/force field/无合成IC50。

## 仍未知

- 是否能在生化和细胞实验中真正抑制 ERK2 活性
- 对更广泛 kinase panel 的脱靶谱与选择性尚未证明
- 未提供可直接复现的代码仓库或参数包
- 全球新颖性只能基于文内数据库检索，未见独立 prior-art 证据

## Pi 结构化证据摘录

- **baseline：** 与共晶配体 1473242 相比，作者认为四个候选在 ERK2 上具有更强或更一致的口袋占据能力。
  - 证据：[doi:10.3390/ph19020337, p.8]；[doi:10.3390/ph19020337, p.15]
- **baseline：** 与 PubChem91899270 相比，Ek1–Ek4 在对接能量、MM-GBSA 和 FEP 中总体表现更优或相近。
  - 证据：[doi:10.3390/ph19020337, p.8]；[doi:10.3390/ph19020337, p.15]；[doi:10.3390/ph19020337, p.16]；[doi:10.3390/ph19020337, p.17]
- **baseline：** 与临床试验分子 LY3214996、BVD-523、MK-8353 相比，作者报告其候选物在 ADV 与 ADMET 上具有竞争力。
  - 证据：[doi:10.3390/ph19020337, p.10]
- **data：** 筛选链条为 298 个文献化合物→78 个活性分子→10,316 个生成分子→3000 个相似分子→1818 个高于共晶阈值的分子→26 个通过 ADMET 的分子→4 个最终候选 Ek1–Ek4。
  - 证据：[doi:10.3390/ph19020337, p.3]；[doi:10.3390/ph19020337, p.6]；[doi:10.3390/ph19020337, p.7]
- **data：** 最终四个候选的分子量约为 440.54–499.57，GI permeability 为 90.91–93.13，BBB permeability 为 -0.93 到 -1.30，synthetic accessibility score 为 3.6–3.9。
  - 证据：[doi:10.3390/ph19020337, p.7]
- **data：** 用于对照的结构包括 ERK2 PDB 2OJG 的共晶配体 19A/PubChem 1473242，以及标准分子 PubChem91899270。
  - 证据：[doi:10.3390/ph19020337, p.5]；[doi:10.3390/ph19020337, p.7]；[doi:10.3390/ph19020337, p.19]
- **declared_resources：** 计算资源明确写到使用 Gromacs2023.4、NVIDIA GeForce RTX 2070、10th-gen Intel Core i9-10885H，以及 Linux 环境。
  - 证据：[doi:10.3390/ph19020337, p.21]；[doi:10.3390/ph19020337, p.22]
- **declared_resources：** 方法链条依赖 DeLA-Drug、RDKit、AutoDock Vina 1.2.0、Deep-PK、DiffDock、KDEEP、SwissADME、PLIP 与 gmx_MMPBSA 等现成工具。
  - 证据：[doi:10.3390/ph19020337, p.3]；[doi:10.3390/ph19020337, p.5]；[doi:10.3390/ph19020337, p.6]；[doi:10.3390/ph19020337, p.8]；[doi:10.3390/ph19020337, p.9]；[doi:10.3390/ph19020337, p.15]；[doi:10.3390/ph19020337, p.20]；[doi:10.3390/ph19020337, p.21]
- **declared_resources：** 资助来自 King Saud University 的 Ongoing Research Funding Program (ORFFT-2025-001-1)。
  - 证据：[doi:10.3390/ph19020337, p.23]
- **limitations：** 作者明确指出 CHARMM36、SwissParam 与 100 ns MD 带来近似性，可能不足以捕捉更慢的构象变化。
  - 证据：[doi:10.3390/ph19020337, p.18]；[doi:10.3390/ph19020337, p.22]
- **limitations：** 作者也承认 MM/GBSA 不含显式熵项，因此需要用 FEP 进行补充，而非完全替代。
  - 证据：[doi:10.3390/ph19020337, p.18]；[doi:10.3390/ph19020337, p.16]
- **limitations：** 文中强调仍需 biochemical、cellular 以及 in vivo 实验验证抑制活性、选择性与安全性。
  - 证据：[doi:10.3390/ph19020337, p.18]；[doi:10.3390/ph19020337, p.23]
- **method：** 先以 ERK2 结构 PDB 2OJG 为受体，并从文献汇编 78 个 Ki 为 0.4–5 nM 的活性抑制剂作为 DeLA-Drug 的输入集合。
  - 证据：[doi:10.3390/ph19020337, p.4]；[doi:10.3390/ph19020337, p.19]
- **method：** DeLA-Drug 生成 10,316 个新分子后，作者使用 RDKit 做 Tanimoto≥0.6 的相似性筛选，保留 3000 个候选进入后续分析。
  - 证据：[doi:10.3390/ph19020337, p.3]；[doi:10.3390/ph19020337, p.19]
- **method：** 对 3000 个分子进行 AutoDock Vina 对接，并用 self-docking 和 15 个 active / 750 个 decoy 的验证集检验流程，报告自对接 RMSD 为 0.87 Å、ROC-AUC 为 0.944。
  - 证据：[doi:10.3390/ph19020337, p.5]；[doi:10.3390/ph19020337, p.20]
- **method：** 对接后再用 Deep-PK、SwissADME、DiffDock、PLIP 和 ERK1 交叉对接做复筛，最终对 4 个候选实施 100 ns MD、MM-GBSA 与 17 个 λ windows 的 FEP。
  - 证据：[doi:10.3390/ph19020337, p.6]；[doi:10.3390/ph19020337, p.7]；[doi:10.3390/ph19020337, p.9]；[doi:10.3390/ph19020337, p.11]；[doi:10.3390/ph19020337, p.12]；[doi:10.3390/ph19020337, p.15]；[doi:10.3390/ph19020337, p.16]；[doi:10.3390/ph19020337, p.21]；[doi:10.3390/ph19020337, p.22]
- **results：** ADV 对 Ek1–Ek4 的结合能分别为 -10.50、-10.20、-9.50、-9.50 kcal/mol，KDEEP 分别为 -6.14、-5.67、-5.23、-6.38 kcal/mol。
  - 证据：[doi:10.3390/ph19020337, p.8]
- **results：** Ek1 与 Tyr34、Lys52、Asp109、Gln103 等残基形成氢键/π相互作用，Ek2–Ek4 也与 Tyr34、Leu154、Asp165 等关键位点形成稳定接触。
  - 证据：[doi:10.3390/ph19020337, p.8]；[doi:10.3390/ph19020337, p.9]
- **results：** DiffDock 的 confidence score 为 Ek1 -1.32、Ek2 -1.49、Ek3 -2.21、Ek4 -1.93，支持这些分子处于 ERK2 活性口袋。
  - 证据：[doi:10.3390/ph19020337, p.9]；[doi:10.3390/ph19020337, p.10]
- **results：** ERK1 选择性对接能量为 -7.40、-7.30、-7.10、-8.10 kcal/mol，低于 ERK2 对应结果，作者据此推断其更偏向 ERK2。
  - 证据：[doi:10.3390/ph19020337, p.11]
- **results：** MD 中 Ek2 与 Ek4 的 backbone RMSD 更低；Table 4 显示其平均 backbone RMSD 分别为 0.14 和 0.13 nm，平均 ligand RMSD 分别为 0.23 和 0.12 nm。
  - 证据：[doi:10.3390/ph19020337, p.11]；[doi:10.3390/ph19020337, p.12]
- **results：** MM-GBSA 显示 Ek4 最强（-26.81 kcal/mol），FEP 显示 Ek1 最强（-26.85 kJ/mol），两者都优于 PubChem91899270。
  - 证据：[doi:10.3390/ph19020337, p.15]；[doi:10.3390/ph19020337, p.16]；[doi:10.3390/ph19020337, p.17]
- **results：** PCA 与 free-energy landscape 结果被作者解释为 Ek1/Ek2 及参考分子形成较紧密聚类，并呈现相对稳定的能量谷。
  - 证据：[doi:10.3390/ph19020337, p.13]；[doi:10.3390/ph19020337, p.14]

## 页码证据

- [doi:10.3390/ph19020337, p.1]
- [doi:10.3390/ph19020337, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
