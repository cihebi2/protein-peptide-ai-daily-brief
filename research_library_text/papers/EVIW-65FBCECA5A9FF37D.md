# An in silico molecular docking and simulation study to identify potential anticancer phytochemicals targeting the RAS signaling pathway

- **论文 ID：** `EVIW-65FBCECA5A9FF37D`
- **期刊 / 来源：** PLoS One
- **发表时间：** 2024 Sep 19
- **DOI：** [10.1371/journal.pone.0310637](https://doi.org/10.1371/journal.pone.0310637)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者声称从 340 个去冗余 phytochemicals 中筛出 26 个满足 ADMET 条件的分子，并进一步通过对接、decoy 和 MD 指出 luteolin、hispidulin、isorhamnetin 等是更有希望的 ERK2 抑制候选物。

## 创新边界

`创新主要来自既有数据库与既有工具上的候选物筛选与排序，不是新算法，也没有 wet-lab 验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

评估一组来自 Dr. Duke 数据库的 phytochemicals 是否可作为 ERK2/MAPK/ERK 通路抑制候选物，并用分子对接、decoy screening 与 200 ns MD 判断其结合强度和稳定性。

## 方法

- virtual screening、docking、MD/energy。

## 数据与基准

- RAS target structures与phytochemicals。

## 比较基线

- known inhibitors/controls。

## 结果证据

- 全部为in silico候选。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 无合成/细胞/动物，force field与bioavailability未知。

## 仍未知

- 未见任何 wet-lab 或临床验证。
- 未提供可复用代码仓库或可执行脚本链接。
- 候选物最终优先级更应以哪一组结果为准，文中没有完全统一。

## Pi 结构化证据摘录

- **baseline：** 文中以 co-crystal ligand 的 cross-docking 作为 docking accuracy 基线，RMSD 0.578 Å 说明流程能复现晶体构象。
  - 证据：[doi:10.1371/journal.pone.0310637, p.8]
- **baseline：** Pyrazolylpyrrole、Ulixertinib 与 Ravoxertinib 被当作阳性或已知 ERK inhibitor 对照，用于比较 binding score 与相互作用模式。
  - 证据：[doi:10.1371/journal.pone.0310637, p.3]；[doi:10.1371/journal.pone.0310637, p.8]；[doi:10.1371/journal.pone.0310637, p.10]
- **baseline：** DUD-E decoy molecules 被用作特异性基线，目的是判断候选物是否只是非特异性高打分配体。
  - 证据：[doi:10.1371/journal.pone.0310637, p.5]；[doi:10.1371/journal.pone.0310637, p.11]
- **data：** 初筛共得到 351 个化合物，去重后剩 340 个；ADMET 后仅 26 个进入后续对接。
  - 证据：[doi:10.1371/journal.pone.0310637, p.7]；[doi:10.1371/journal.pone.0310637, p.8]
- **data：** 表 2 显示入选化合物均满足 high GI absorption、0 个 Lipinski rule 5 violation，且 AMES toxicity、hepatotoxicity 与 skin sensitization 均为阴性或不提示风险。
  - 证据：[doi:10.1371/journal.pone.0310637, p.8]
- **data：** 文中使用 Pyrazolylpyrrole (CID 135523966)、Ulixertinib (CID 11719003) 与 Ravoxertinib (CID 71727581) 作为已知对照，并报告 cross-docking 的 RMSD 为 0.578 Å。
  - 证据：[doi:10.1371/journal.pone.0310637, p.3]；[doi:10.1371/journal.pone.0310637, p.8]
- **data：** 表 3 的 docking score 大致落在 -7.5 到 -10.2 Kcal/mol 区间，覆盖了 quercetin、luteolin、hispidulin、isorhamnetin、chrysoeriol 与 rhamnetin 等候选物。
  - 证据：[doi:10.1371/journal.pone.0310637, p.10]；[doi:10.1371/journal.pone.0310637, p.11]
- **declared_resources：** 研究获得 Shahjalal University of Science and Technology Research Center 的部分资助，且作者声明无 competing interests。
  - 证据：[doi:10.1371/journal.pone.0310637, p.2]；[doi:10.1371/journal.pone.0310637, p.24]
- **declared_resources：** 计算与分析资源包括 PyRx、AutoDock Vina、Biovia Discovery Studio Visualizer 2021、PyMol、GROMACS 2020.6、RStudio/ggplot2、CASTp、SwissADME、pkCSM、DUD-E、Open Babel、KEGG 与 STRING。
  - 证据：[doi:10.1371/journal.pone.0310637, p.4]；[doi:10.1371/journal.pone.0310637, p.5]；[doi:10.1371/journal.pone.0310637, p.6]
- **declared_resources：** Data Availability Statement 说明所有相关数据都在正文和 Supporting Information 中，并附有 S1–S3 Fig、S1–S3 Table 与 S1–S3 File。
  - 证据：[doi:10.1371/journal.pone.0310637, p.1]；[doi:10.1371/journal.pone.0310637, p.23]
- **limitations：** 作者明确指出，所有 in silico 发现仍需要 in vitro 和 in vivo 实验验证，当前证据不能单独证明疗效或安全性。
  - 证据：[doi:10.1371/journal.pone.0310637, p.21]
- **limitations：** 并非所有候选都稳定：文中承认除 Complex 3/7/8 外，其余 six complexes 在 MD 中表现较差，rhamnetin 也出现特异性风险。
  - 证据：[doi:10.1371/journal.pone.0310637, p.11]；[doi:10.1371/journal.pone.0310637, p.14]；[doi:10.1371/journal.pone.0310637, p.15]
- **limitations：** 文中对最佳命中的排序存在轻微不一致：摘要和结论突出 luteolin、hispidulin、isorhamnetin，但表 3 中 chrysoeriol 与 quercetin 的 docking score 更低。
  - 证据：[doi:10.1371/journal.pone.0310637, p.1]；[doi:10.1371/journal.pone.0310637, p.10]；[doi:10.1371/journal.pone.0310637, p.21]
- **method：** 研究先以 Dr. Duke’s Phytochemical and Ethnobotanical Databases 检索抗癌、抗癌化与癌症预防相关化合物，去冗余后得到 340 个候选分子；ERK 结构选用 PDB 1TVO（2.50 Å）作为对接靶标。
  - 证据：[doi:10.1371/journal.pone.0310637, p.3]；[doi:10.1371/journal.pone.0310637, p.7]
- **method：** 活性位点用 CASTp v3.0 预测，并与 RCSB PDB 中 1TVO 的配体相互作用残基交叉验证；随后用 SwissADME 和 pkCSM 进行 ADMET 与 toxicity 筛选。
  - 证据：[doi:10.1371/journal.pone.0310637, p.4]；[doi:10.1371/journal.pone.0310637, p.6]
- **method：** 分子对接采用 PyRx 与 AutoDock Vina，按文中给定网格框坐标和 exhaustiveness 参数执行；对接后又用 DUD-E decoys 做特异性验证。
  - 证据：[doi:10.1371/journal.pone.0310637, p.4]；[doi:10.1371/journal.pone.0310637, p.5]
- **method：** MD 在 GROMACS 2020.6 上进行，使用 CHARMM36 和 TIP3P 水模型，模拟 200 ns，并分析 RMSD、RMSF、SASA、Rg 和 hydrogen bond。
  - 证据：[doi:10.1371/journal.pone.0310637, p.5]
- **method：** 另用 KEGG 与 STRING 分析 MAPK1/ERK2 相关通路和 PPI 网络，以解释候选分子可能影响的下游癌症机制。
  - 证据：[doi:10.1371/journal.pone.0310637, p.6]；[doi:10.1371/journal.pone.0310637, p.16]；[doi:10.1371/journal.pone.0310637, p.18]
- **results：** 对接结果中，chrysoeriol (-10.2)、quercetin (-10.1)、luteolin (-10.1)、rhamnetin (-10.0) 和 hispidulin (-9.86) 等分子获得了最强或接近最强的结合分数。
  - 证据：[doi:10.1371/journal.pone.0310637, p.10]；[doi:10.1371/journal.pone.0310637, p.19]
- **results：** Decoy screening 显示 quercetin、luteolin、hispidulin 的活性分子优于各自 decoy，而 rhamnetin 的 decoy 结合更强，提示其特异性较差。
  - 证据：[doi:10.1371/journal.pone.0310637, p.11]；[doi:10.1371/journal.pone.0310637, p.19]
- **results：** MD 中 Complex 3、7、8 的稳定性最好；control 的 RMSD 波动更大，而 Complex 7/8 在 200 ns 内更接近持续稳定。
  - 证据：[doi:10.1371/journal.pone.0310637, p.14]；[doi:10.1371/journal.pone.0310637, p.15]
- **results：** RMSF 大多不超过 0.6 nm，ligand-bound 状态的 SASA 高于 free protein，且 complexes 的 Rg 约为 2.20–2.23 nm，高于 only protein 的约 2.15 nm。
  - 证据：[doi:10.1371/journal.pone.0310637, p.15]；[doi:10.1371/journal.pone.0310637, p.16]；[doi:10.1371/journal.pone.0310637, p.17]
- **results：** KEGG/STRING 分析把 MAPK1/ERK2 连接到多种癌症相关通路，并识别出 TP53、STAT3、JUN、RPS6KA1、DUSP1、PEA15 等 PPI 节点。
  - 证据：[doi:10.1371/journal.pone.0310637, p.16]；[doi:10.1371/journal.pone.0310637, p.18]

## 页码证据

- [doi:10.1371/journal.pone.0310637, p.1]
- [doi:10.1371/journal.pone.0310637, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
