# Comprehensive evaluation of artificial intelligence-empowered approaches for protein–aptamer complex prediction

- **论文 ID：** `EVIW-EDB6C8BC2C49BED9`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2026 May 4
- **DOI：** [10.1093/bib/bbag206](https://doi.org/10.1093/bib/bbag206)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称建立了首个独立的 protein–aptamer benchmark，并用 AF3、Chai-1、Boltz-2、RF2NA 以及 3dRNA/DNA 对 11 个 PDB 复合物做横向评测，结合 MD、MM/GBSA、iLDDT、PO 和 H-bond 分析给出多维度结论。

## 创新边界

`这是 benchmark 与方法评测，不是新算法或新 wet-lab 发现；创新边界主要在评估框架、对照设计与 specificity-aware 分析。`。这不是全球首创性检索或独立复现结论。

## 研究问题

系统评估现有 AI 结构预测框架在 protein–aptamer complex prediction 中的结构准确性、界面恢复能力、动力学稳定性与能量一致性，并检验其是否能区分 native 与 non-native aptamer 配对。

## 方法

- 统一生成complex structure，再以几何、MD stability和binding free-energy consistency评估。

## 数据与基准

- 独立protein-aptamer复合物benchmark。

## 比较基线

- AF3、Chai-1、Boltz-2、RF2NA及template。

## 结果证据

- 给出各模型强弱和aptamer modeling参考；不是新结构模型。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 现有benchmark规模有限，几何准确不等于能量/特异性正确。

## 仍未知

- 补充材料中的完整数值与图表未逐项展开，部分细节只能依据正文摘要判断。
- GitHub 仓库提供了结构文件与脚本，但仅凭论文正文无法验证端到端复现是否完全一致。
- 对含修饰残基 aptamer 的系统性处理仍未解决，未来扩展性不明。

## Pi 结构化证据摘录

- **baseline：** 本文的横向 baseline 是 AF3、Chai-1、Boltz-2、RF2NA 与传统 template-based 的 3dRNA/DNA，而不是单一模型内部消融。
  - 证据：[doi:10.1093/bib/bbag206, p.1]；[doi:10.1093/bib/bbag206, p.5]
- **baseline：** 界面质量参考使用 DockQ 对应的 23.6% 与 77.6% 阈值，并以实验结构作为 GT 对照。
  - 证据：[doi:10.1093/bib/bbag206, p.9]；[doi:10.1093/bib/bbag206, p.10]
- **baseline：** 作者还用 mismatched negative set 和 AF3 shuffled-sequence control 作为 specificity baseline，直接测试模型是否会对非 native 配对产生“看似合理”的输出。
  - 证据：[doi:10.1093/bib/bbag206, p.5]；[doi:10.1093/bib/bbag206, p.7]
- **data：** 核心数据集来自 11 个 PDB 复合物，涵盖 reverse transcriptase、Fab、thrombin、transferrin receptor、SARS-CoV-2 nucleocapsid 与 nanobody/G-quadruplex 等不同靶类。
  - 证据：[doi:10.1093/bib/bbag206, p.6]
- **data：** 实验参考结构采用 Biological Assembly 1，并移除水、氢、离子、配体及其他非蛋白/非核酸组分后作为 GT。
  - 证据：[doi:10.1093/bib/bbag206, p.5]；[doi:10.1093/bib/bbag206, p.6]
- **data：** 正样本、mismatched negative set 和 AF3 shuffled-sequence control 分别构成 11、11、11 个样本；Boltz-2 其中 6 个复合物落在训练集内，5 个为 unseen。
  - 证据：[doi:10.1093/bib/bbag206, p.5]；[doi:10.1093/bib/bbag206, p.7]；[doi:10.1093/bib/bbag206, p.8]
- **data：** aptamer-only 输入来自同一批复合物中的 aptamer 序列，二级结构用 RNAFold 生成；3dRNA/DNA 还通过 Exclude PDB 避免模板复用。
  - 证据：[doi:10.1093/bib/bbag206, p.5]
- **declared_resources：** 论文第 17 页给出公共 GitHub 仓库，用于 processed structure files 和 selected analysis scripts。
  - 证据：[doi:10.1093/bib/bbag206, p.17]
- **declared_resources：** 作者声明使用的结构来源是 PDB 的 11 个 accession codes：7LRI、7SZU、7V5N、7ZKO、7ZQS、8D29、8BW5、8TFD、8TQS、8ZBF、9GXH。
  - 证据：[doi:10.1093/bib/bbag206, p.17]
- **declared_resources：** 模型与软件资源包括 AF3 v3.0.1、Chai-1 v0.6.1、Boltz-2 v2.2.0、RF2NA v0.2、3dRNA/DNA webserver，以及 CHARMM-GUI、GROMACS、OpenStructure、HBPLUS、RNAFold 和 gmx_MMPBSA。
  - 证据：[doi:10.1093/bib/bbag206, p.5]；[doi:10.1093/bib/bbag206, p.6]；[doi:10.1093/bib/bbag206, p.7]
- **limitations：** 样本量只有 11 个复合物，bootstrap 置信区间较宽，leave-one-out 也显示结果会受单个复杂体显著影响。
  - 证据：[doi:10.1093/bib/bbag206, p.7]；[doi:10.1093/bib/bbag206, p.8]
- **limitations：** 可用的 protein–aptamer 结构本来就稀缺，且含修饰残基的条目被排除，因此 benchmark 覆盖面仍然有限。
  - 证据：[doi:10.1093/bib/bbag206, p.1]；[doi:10.1093/bib/bbag206, p.5]；[doi:10.1093/bib/bbag206, p.16]
- **limitations：** 20 ns MD 可能不足以捕捉更慢的构象调整，作者也指出 100 ns 补充分析表明某些指标对时间窗敏感。
  - 证据：[doi:10.1093/bib/bbag206, p.16]
- **limitations：** 离子环境没有被完全物理化建模，MD 仅用 NaCl 中和；而且预测中的 ion placement 仍常偏离实验坐标。
  - 证据：[doi:10.1093/bib/bbag206, p.15]；[doi:10.1093/bib/bbag206, p.16]
- **method：** 作者从 PDB 选取 11 个在 AF3 cutoff 之后发布的 protein–aptamer complexes，去除同研究近缘变体与含修饰残基条目，作为正样本 benchmark。
  - 证据：[doi:10.1093/bib/bbag206, p.5]
- **method：** 主评测比较 AF3、Chai-1、Boltz-2、RF2NA；aptamer-only 任务额外评估 3dRNA/DNA，并对每个 complex 生成 25 个预测样本。
  - 证据：[doi:10.1093/bib/bbag206, p.5]
- **method：** 负对照由 protein 与下一个 complex 的 aptamer 错配构成，AF3 还额外构造随机打乱序列控制；主分析不显式输入离子。
  - 证据：[doi:10.1093/bib/bbag206, p.5]
- **method：** 结构与稳定性评估结合 20 ns MD、CHARMM36m、GROMACS、MM/GBSA、iLDDT、PO、HBPLUS H-bonds、Rg 和 RMSD 等指标。
  - 证据：[doi:10.1093/bib/bbag206, p.6]；[doi:10.1093/bib/bbag206, p.7]
- **method：** 离子分析单独在 9 个含金属离子的复合物上进行，AF3/Boltz-2 以 CCD 条目输入离子，Chai-1 以 ligand string 输入，RF2NA 不支持显式离子输入。
  - 证据：[doi:10.1093/bib/bbag206, p.14]；[doi:10.1093/bib/bbag206, p.15]
- **results：** 在 ΔGbind 上，正样本整体仅呈中等相关；Boltz-2 在 positive set 的 Pearson 相关最高，但 seen/unseen 划分显示结果对训练集重叠和样本量很敏感。
  - 证据：[doi:10.1093/bib/bbag206, p.7]；[doi:10.1093/bib/bbag206, p.8]
- **results：** mismatched negative set 以及 AF3 的 shuffled controls 仍能给出与正样本相近甚至更高的 ΔGbind 相关性，说明模型难以可靠区分 native 与 non-native aptamer 配对。
  - 证据：[doi:10.1093/bib/bbag206, p.7]；[doi:10.1093/bib/bbag206, p.9]
- **results：** 界面准确性上，Boltz-2 的整体 iLDDT 最高，AF3 次之，Chai-1 和 RF2NA 较低；但在未见训练集的 D2 子集上所有模型都更难恢复正确 interface。
  - 证据：[doi:10.1093/bib/bbag206, p.9]；[doi:10.1093/bib/bbag206, p.10]
- **results：** H-bond precision/recall 大体跟随 iLDDT；RF2NA 通常更弱，而负对照和 shuffled controls 也能维持持续的界面 H-bonds。
  - 证据：[doi:10.1093/bib/bbag206, p.9]；[doi:10.1093/bib/bbag206, p.10]
- **results：** MD 中的 Rg 与 RMSD 显示部分预测结构可维持相对稳定，但许多复杂体仍显著偏离 GT，且 aptamer 部分通常比 protein 更难准确恢复。
  - 证据：[doi:10.1093/bib/bbag206, p.11]；[doi:10.1093/bib/bbag206, p.12]；[doi:10.1093/bib/bbag206, p.13]
- **results：** ipTM 对 Boltz-2 呈现明显过高自信：多个复杂体 ipTM 均很高，但 iLDDT 仍较低，作者据此提醒不要单独依赖 ipTM 判断 protein–aptamer 接口质量。
  - 证据：[doi:10.1093/bib/bbag206, p.13]；[doi:10.1093/bib/bbag206, p.14]
- **results：** 离子输入对 iLDDT 的提升总体有限，AF3 与 Chai-1 无显著变化，Boltz-2 仅有小幅改善；ΔGbind 的总体趋势在有无离子条件下也大体一致。
  - 证据：[doi:10.1093/bib/bbag206, p.14]；[doi:10.1093/bib/bbag206, p.15]

## 页码证据

- [doi:10.1093/bib/bbag206, p.15]
- [doi:10.1093/bib/bbag206, p.1]
- [doi:10.1093/bib/bbag206, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
