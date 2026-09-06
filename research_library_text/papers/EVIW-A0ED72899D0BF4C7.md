# Modeling Protein–Protein and Protein–Ligand Interactions by the ClusPro Team in CASP16

- **论文 ID：** `EVIW-A0ED72899D0BF4C7`
- **期刊 / 来源：** Proteins
- **发表时间：** 2025 Oct 20
- **DOI：** [10.1002/prot.70066](https://doi.org/10.1002/prot.70066)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称提出并验证了两条混合流水线：一条用于 protein–protein docking，将 ClusPro FFT/MD 与 AlphaFold 采样及 AF2.3 refinement/rescoring 结合；另一条用于 protein–ligand docking，将 SMARTS 锚定、ETKDG/扩散采样与 ML confidence scoring 结合，以提高 pose prediction accuracy。

## 创新边界

`本稿的创新边界主要在 CASP16 实战中的集成式流程设计、SMARTS anchoring 和 ML 重评分的组合；论文未提供足以独立验证 global novelty 的冻结前沿证据。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在 CASP16 场景下，如何通过物理采样、AlphaFold 与机器学习重评分提升 protein–protein 和 protein–ligand 复合物结构预测精度。

## 方法

- 大规模物理采样后深度模型重排/精修，保留template interaction fragments并局部重采样。

## 数据与基准

- CASP16 blind targets和数千级候选。

## 比较基线

- AF-only、ClusPro server、CASP15 protocol。

## 结果证据

- 产生多例高精度complex，包括AF单独失败案例；说明物理采样的互补价值。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 依赖足够template，采样与各模块贡献尚缺系统消融。

## 仍未知

- 补充信息 Data S1 与 Figure S1–S4 未展开，部分靶点级细节无法逐项核验。
- 正文未提供公开代码仓库或固定版本链接，复现路径不完整。
- 论文没有独立 prior-art 证据，global novelty 不能外推。

## Pi 结构化证据摘录

- **baseline：** 作者将 AF2/AF3 的多次采样与 ClusPro/PIPER 全局搜索并列，指出仅靠 AF 在某些目标上会失败，尤其是 H1223 的 AF3 结果只有 DockQ 0.078。
  - 证据：[doi:10.1002/prot.70066, p.2]；[doi:10.1002/prot.70066, p.5]
- **baseline：** 在 SARS-CoV-2 Mpro 上，作者把自己的 0.78 平均 lDDT-PLI 与第二名 LG262 的 0.67 直接对比，显示模板/SMARTS 策略的优势。
  - 证据：[doi:10.1002/prot.70066, p.6]
- **baseline：** 论文还强调经典 rigid docking 虽可枚举 billions of orientations，但易产生高排名 false positives，作为与 AI 方法互补的基线背景。
  - 证据：[doi:10.1002/prot.70066, p.2]
- **data：** 蛋白-蛋白评测覆盖 CASP16 的 40 个 multimer targets 中的 35 个，作者还特别提交了所有 antibody-antigen 和 virus-host targets。
  - 证据：[doi:10.1002/prot.70066, p.5]
- **data：** 蛋白-配体挑战包含 233 个复合物，涉及 Chymase、Cathepsin G、Autotaxin 和 SARS-CoV-2 Mpro 四个药理相关靶点。
  - 证据：[doi:10.1002/prot.70066, p.2]；[doi:10.1002/prot.70066, p.5]
- **data：** ML confidence 模块的训练/验证采用 PDBBind 的时间切分：约 17,000 个 2018 年前复杂体用于训练/验证，2019 年 363 个复杂体作为测试集，且测试集不与训练集共享 ligand。
  - 证据：[doi:10.1002/prot.70066, p.5]
- **data：** 作者声明数据来自公共领域资源或可按请求获取。
  - 证据：[doi:10.1002/prot.70066, p.8]
- **declared_resources：** 研究资金来自 NIGMS 的 R01GM140098、R35GM118078、RM1GM135136、R01GM140154，另有 CPRIT RR250131 和 NSF 2054251。
  - 证据：[doi:10.1002/prot.70066, p.1]
- **declared_resources：** 作者还使用了 Oak Ridge Leadership Computing Facility 的计算资源，受 DOE Contract DE-AC05-00OR22725 支持。
  - 证据：[doi:10.1002/prot.70066, p.8]
- **limitations：** 蛋白-蛋白方法需要大量采样，作者明确表示仍需系统性 benchmarking 和 ablation studies 来判断误差是否可由更强采样修复。
  - 证据：[doi:10.1002/prot.70066, p.7]
- **limitations：** 蛋白-配体方法对模板数据依赖强；当模板稀缺或化学空间较新时，性能明显下降。
  - 证据：[doi:10.1002/prot.70066, p.7]；[doi:10.1002/prot.70066, p.8]
- **limitations：** 作者承认打分有时无法区分对称或多解构象，导致 top-1 排名失误。
  - 证据：[doi:10.1002/prot.70066, p.7]
- **method：** 蛋白-蛋白流程先以 AlphaFold2.1/2.3/3 及自定义微调版本进行多 seed 采样，再与 ClusPro/PIPER 的 FFT docking 和 MD 采样合并，最后用 AF2.3 对接口做局部 refinement 与重评分。
  - 证据：[doi:10.1002/prot.70066, p.2]；[doi:10.1002/prot.70066, p.3]
- **method：** FFT 部分用 70,000 rotations 配合百万级平移枚举候选构象，并以包含 van der Waals、electrostatics 和 DARS 的物理能量函数打分，随后按 ligand RMSD 3 Å 聚类、保留 10,000 个低能中心。
  - 证据：[doi:10.1002/prot.70066, p.3]
- **method：** 抗体-肽体系额外引入 MD 采样，使用 AmberTools、PME、SHAKE 和 1000 ns production MD，在 CDR 与肽附近保留柔性以处理肽链高柔性。
  - 证据：[doi:10.1002/prot.70066, p.3]
- **method：** 蛋白-配体流程先用 MMseqs2/RCSB API 搜索 ≥50% identity 的 PDB holo template，再以 MCS 与 pharmacophore 识别构造 SMARTS anchoring。
  - 证据：[doi:10.1002/prot.70066, p.4]
- **method：** 随后用 RDKit ETKDG、OpenMM 最小化、torsion-only diffusion model 和 SE(3)-equivariant RMSD predictor 进行构象采样与质量评分，并用 Butina 聚类筛选最终姿势。
  - 证据：[doi:10.1002/prot.70066, p.4]；[doi:10.1002/prot.70066, p.5]
- **results：** 对 H1204、H1215、H1233，作者报告 top 模型分别达到 DockQ 0.827、0.933、0.930，且都被排为 Top 1。
  - 证据：[doi:10.1002/prot.70066, p.5]
- **results：** H1217 的最佳模型为 Top 2，DockQ 0.519；H1223 的 MD 驱动方法得到 Top 1，DockQ 0.716，而此前 AF3 最佳结果仅 0.078。
  - 证据：[doi:10.1002/prot.70066, p.5]
- **results：** 蛋白-配体整体平均 lDDT-PLI 为 0.69；其中 SARS-CoV-2 Mpro 平均 0.78，优于 LG262 的 0.67。
  - 证据：[doi:10.1002/prot.70066, p.5]；[doi:10.1002/prot.70066, p.6]
- **results：** 当模板可用时，Top 1 模型的 median RMSD 为 1.51 Å；模板不足时则升至 9.99 Å。
  - 证据：[doi:10.1002/prot.70066, p.6]
- **results：** Top 5 提交常能挽救 Top 1 失败，说明排名模块仍可改进。
  - 证据：[doi:10.1002/prot.70066, p.6]

## 页码证据

- [doi:10.1002/prot.70066, p.1]
- [doi:10.1002/prot.70066, p.2]
- [doi:10.1002/prot.70066, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
