# Assessing the Interactions between Snake Venom Metalloproteinases and Hydroxamate Inhibitors Using Kinetic and ITC Assays, Molecular Dynamics Simulations and MM/PBSA-Based Calculations

- **论文 ID：** `EVIW-7587EFB3DB8AABCA`
- **期刊 / 来源：** ACS Omega
- **发表时间：** 2024 Dec 10
- **DOI：** [10.1021/acsomega.4c08439](https://doi.org/10.1021/acsomega.4c08439)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称把酶动力学、ITC、分子对接、显式溶剂 MD 与多种 MM/PBSA 类评分系统整合起来，解析 6 个 hydroxamate 抑制剂与 Atr-I/Leuc-a 的相互作用，筛选出与实验亲和力最相关的 scoring functions，并指出在小 QM 区域下的 DFTB/PBSA、DFTB3/PBSA、PM6/PBSA 表现最佳；同时给出首批非重组 metalloproteases 的 ITC 结果。[doi:10.1021/acsomega.4c08439, p.1][doi:10.1021/acsomega.4c08439, p.11][doi:10.1021/acsomega.4c08439, p.16][doi:10.1021/acsomega.4c08439, p.17]

## 创新边界

`新意主要在实验-计算一体化比较与评分函数系统筛选，不在新抑制剂骨架、新靶点或通用算法提出。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在蛇咬伤局部组织损伤难以被抗毒素充分阻断的背景下，作者要评估一组 hydroxamate 广谱金属蛋白酶抑制剂对两种代表性 SVMP（Atr-I 与 Leuc-a）的抑制能力、结合模式与可用于亲和力排序的计算评分函数。[doi:10.1021/acsomega.4c08439, p.1][doi:10.1021/acsomega.4c08439, p.2][doi:10.1021/acsomega.4c08439, p.3]

## 方法

- 酶动力学、ITC、MD、MM/PBSA。

## 数据与基准

- SVMPs与hydroxamate inhibitor panel。

## 比较基线

- 不同inhibitors/controls。

## 结果证据

- kinetic/ITC为明确实验，MD/MM-PBSA为解释性计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 体外体系、force-field和体内抗毒未知。

## 仍未知

- 仅覆盖两种 SVMP，外推到其他 metalloproteases 仍不确定。
- ITC 只测了 3 个抑制剂，且受样品量与溶解度限制。
- 未见晶体复合物，结合模式仍是计算推断。
- Km 未测出，IC50→Ki 的近似会引入不确定性。

## Pi 结构化证据摘录

- **baseline：** 原始 AutoDock 分数对不同 pose 的区分度有限，作者明确指出即使配位/口袋接触不同，AutoDock 打分也常给出相近结果。[doi:10.1021/acsomega.4c08439, p.12]
  - 证据：[doi:10.1021/acsomega.4c08439, p.12]
- **baseline：** 作者把纯 interaction energy 的 ΔG_int、传统 MM/PBSA/MM/GBSA，以及多种 QM/MM-PB(GB)SA 组合并列比较，作为评分基线来检验是否需要 distortion 与 entropy 修正。[doi:10.1021/acsomega.4c08439, p.7][doi:10.1021/acsomega.4c08439, p.8][doi:10.1021/acsomega.4c08439, p.15][doi:10.1021/acsomega.4c08439, p.16]
  - 证据：[doi:10.1021/acsomega.4c08439, p.7]；[doi:10.1021/acsomega.4c08439, p.8]；[doi:10.1021/acsomega.4c08439, p.15]；[doi:10.1021/acsomega.4c08439, p.16]
- **baseline：** 文中还把 DFTB 的 small QM region 与 large QM region 对照，结论是只把 hydroxamate 头基纳入 QM 更平衡，也更容易得到更好的相关性。[doi:10.1021/acsomega.4c08439, p.8][doi:10.1021/acsomega.4c08439, p.16][doi:10.1021/acsomega.4c08439, p.17]
  - 证据：[doi:10.1021/acsomega.4c08439, p.8]；[doi:10.1021/acsomega.4c08439, p.16]；[doi:10.1021/acsomega.4c08439, p.17]
- **data：** 实验与计算对象包括 Atr-I、Leuc-a 两种 SVMP，以及 BAT、CP4、MAR、PRI、COL、MMP 六个 hydroxamate 抑制剂；文中还说明了部分蛋白与抑制剂的来源是已纯化蛋白和商业购买化合物。[doi:10.1021/acsomega.4c08439, p.4][doi:10.1021/acsomega.4c08439, p.5]
  - 证据：[doi:10.1021/acsomega.4c08439, p.4]；[doi:10.1021/acsomega.4c08439, p.5]
- **data：** 用于计算的构象数据来自两条先前 250 ns 的 MD 轨迹，各自抽取 50 个 snapshot；后续又为每个蛋白构建了 13 种不同结合/电荷配置来做 MD。[doi:10.1021/acsomega.4c08439, p.5][doi:10.1021/acsomega.4c08439, p.12]
  - 证据：[doi:10.1021/acsomega.4c08439, p.5]；[doi:10.1021/acsomega.4c08439, p.12]
- **data：** 作者声明将对接、MD 输入输出、相互作用分析、自由能与熵计算结果放在 Zenodo，并在 Supporting Information 中补充 Zn 环境参数、聚类与评分比较。[doi:10.1021/acsomega.4c08439, p.6][doi:10.1021/acsomega.4c08439, p.17][doi:10.1021/acsomega.4c08439, p.18]
  - 证据：[doi:10.1021/acsomega.4c08439, p.6]；[doi:10.1021/acsomega.4c08439, p.17]；[doi:10.1021/acsomega.4c08439, p.18]
- **declared_resources：** 作者声明 Zenodo 公开了对接与 MD 的 inputs/outputs、毒素/抑制剂相互作用、自由能与熵计算结果；这属于可复核的数据归档，不等于源码仓库。[doi:10.1021/acsomega.4c08439, p.17]
  - 证据：[doi:10.1021/acsomega.4c08439, p.17]
- **declared_resources：** Supporting Information 还包含 Zn 环境参数、MD 额外分析、聚类细节与 scoring functions 性能比较，用于复现主要计算流程。[doi:10.1021/acsomega.4c08439, p.18]
  - 证据：[doi:10.1021/acsomega.4c08439, p.18]
- **declared_resources：** 文中另称 QM/MM 优化后的几何结构与导出的电荷也已上传 Zenodo，属于附加的计算资源。[doi:10.1021/acsomega.4c08439, p.6]
  - 证据：[doi:10.1021/acsomega.4c08439, p.6]
- **limitations：** 动力学部分无法可靠测出 Km，因此 IC50 只是 Ki 的近似，这会限制绝对亲和力解释的严谨性。[doi:10.1021/acsomega.4c08439, p.4][doi:10.1021/acsomega.4c08439, p.11]
  - 证据：[doi:10.1021/acsomega.4c08439, p.4]；[doi:10.1021/acsomega.4c08439, p.11]
- **limitations：** ITC 只对 Atr-I 与 CP4、MAR、PRI 做了测量，因为纯化毒素和抑制剂溶解度都有限，BAT 还被排除在外。[doi:10.1021/acsomega.4c08439, p.11]
  - 证据：[doi:10.1021/acsomega.4c08439, p.11]
- **limitations：** 作者没有晶体复合物来直接验证预测的结合模式，并明确写到需要 crystallographic complex structures 才能最终确认。[doi:10.1021/acsomega.4c08439, p.17]
  - 证据：[doi:10.1021/acsomega.4c08439, p.17]
- **limitations：** 作者也承认目前只覆盖两种 SVMP 和少数抑制剂，相关 scoring patterns 是否能推广到其他医学相关酶仍未证明。[doi:10.1021/acsomega.4c08439, p.17]
  - 证据：[doi:10.1021/acsomega.4c08439, p.17]
- **method：** 作者用 FRET 肽底物对 Atr-I 和 Leuc-a 做酶学抑制实验，抑制剂浓度覆盖 0.1 nM 到 75 μM，IC50 由非线性回归得到；因 Km 无法可靠测出，IC50 被近似当作 Ki。[doi:10.1021/acsomega.4c08439, p.4][doi:10.1021/acsomega.4c08439, p.11]
  - 证据：[doi:10.1021/acsomega.4c08439, p.4]；[doi:10.1021/acsomega.4c08439, p.11]
- **method：** 作者对 Atr-I 进行 ITC，25 °C 下用 CP4、MAR、PRI 做滴定，采用独立位点模型拟合，获得结合常数、ΔH、ΔS 和化学计量数 N。[doi:10.1021/acsomega.4c08439, p.4][doi:10.1021/acsomega.4c08439, p.11]
  - 证据：[doi:10.1021/acsomega.4c08439, p.4]；[doi:10.1021/acsomega.4c08439, p.11]
- **method：** 对接阶段使用 50 个来自既往 250 ns MD 轨迹的受体快照，AutoDock 4.0 每个复合物生成 500 个 pose，并通过 Zn 电荷与羟肟酸配位参数调整提高金属配位表现。[doi:10.1021/acsomega.4c08439, p.5][doi:10.1021/acsomega.4c08439, p.6]
  - 证据：[doi:10.1021/acsomega.4c08439, p.5]；[doi:10.1021/acsomega.4c08439, p.6]
- **method：** 作者随后用 SCC-DFTB 为核心的 QM/MM、PBSA 重新评分对接构象，QM 区域包含 Zn 配位壳层与 hydroxamate 头基，并据此选择最可能的结合模式。[doi:10.1021/acsomega.4c08439, p.5][doi:10.1021/acsomega.4c08439, p.6]
  - 证据：[doi:10.1021/acsomega.4c08439, p.5]；[doi:10.1021/acsomega.4c08439, p.6]
- **method：** 显式溶剂 MD 在 Amber14 中以 ff14SB/GAFF、TIP3P 和带键合 Zn 表示进行，生产期为 250 ns；之后还做了聚类、接触统计、MM/PBSA、QM/MM-PBSA、熵与去畸变能分析。[doi:10.1021/acsomega.4c08439, p.6][doi:10.1021/acsomega.4c08439, p.7][doi:10.1021/acsomega.4c08439, p.8][doi:10.1021/acsomega.4c08439, p.9][doi:10.1021/acsomega.4c08439, p.10]
  - 证据：[doi:10.1021/acsomega.4c08439, p.6]；[doi:10.1021/acsomega.4c08439, p.7]；[doi:10.1021/acsomega.4c08439, p.8]；[doi:10.1021/acsomega.4c08439, p.9]；[doi:10.1021/acsomega.4c08439, p.10]
- **results：** 动力学结果显示 6 个抑制剂都能抑制两种毒素；Atr-I 上多数 IC50 在 20–160 nM，只有 COL 约 8 μM，而 Leuc-a 上多数在 20–690 nM，BAT 例外地降到约 12 μM。[doi:10.1021/acsomega.4c08439, p.10][doi:10.1021/acsomega.4c08439, p.11]
  - 证据：[doi:10.1021/acsomega.4c08439, p.10]；[doi:10.1021/acsomega.4c08439, p.11]
- **results：** ITC 显示 Atr-I 对 PRI 亲和力最高（ΔG 约 -13.0 kcal/mol），其次是 MAR 和 CP4；同时化学计量数接近 1，支持 1:1 结合模型。[doi:10.1021/acsomega.4c08439, p.11]
  - 证据：[doi:10.1021/acsomega.4c08439, p.11]
- **results：** MD 表明 Zn 配位环境整体稳定、平均 RMSD 约 0.9 Å，但 Atr-I 的 Ω-loop，尤其 154–162 区段，较 Leuc-a 更灵活，这被作者联系到出血活性差异。[doi:10.1021/acsomega.4c08439, p.12]
  - 证据：[doi:10.1021/acsomega.4c08439, p.12]
- **results：** 相互作用分析显示，主链氢键与 S1′ pocket 的疏水接触在两种毒素中模式相近，解释了这些 hydroxamate 抑制剂的 broad-spectrum 行为。[doi:10.1021/acsomega.4c08439, p.13]
  - 证据：[doi:10.1021/acsomega.4c08439, p.13]
- **results：** 在 216 个 scoring combinations 中，最佳相关性来自加入 distortion energy 与 entropy 的 SQM/MM-PBSA 方案，最高 Pearson r 可到 0.83；作者还指出 BAT 的最优结合模式在两种毒素间会不同。[doi:10.1021/acsomega.4c08439, p.16][doi:10.1021/acsomega.4c08439, p.17]
  - 证据：[doi:10.1021/acsomega.4c08439, p.16]；[doi:10.1021/acsomega.4c08439, p.17]

## 页码证据

- [doi:10.1021/acsomega.4c08439, p.1]
- [doi:10.1021/acsomega.4c08439, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
