# G Protein-Coupled Receptor-Ligand Pose and Functional Class Prediction

- **论文 ID：** `EVIW-3CDA35EC397C9E5E`
- **期刊 / 来源：** Int J Mol Sci
- **发表时间：** 2024 Jun 22
- **DOI：** [10.3390/ijms25136876](https://doi.org/10.3390/ijms25136876)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

论文声称提出了一条面向 class A GPCR 的筛选流程：先用 PDB 复合物构建并评估 global/state-specific ligand interaction fingerprints，再基于 1820 个 GPCR-ligand complexes 的逐残基特征训练 random forest classifier，并在 GPR31/TAAR2 外部集上验证；最终通过 merged active 与 majority rule 获得可用于筛选富集的 hit rate。

## 创新边界

`创新主要在特征组织、训练/后处理流程和筛选评估方式，不是新 docking engine，也没有 wet-lab 结果；作者自己也把 fingerprint 作为口袋选择工具的收益描述为有限，最终转而使用 automated SiteFinder。`。这不是全球首创性检索或独立复现结论。

## 研究问题

作者要解决 GPCR 虚拟筛选中的两个核心问题：一是 ligand interaction fingerprints 是否能比自动口袋选择更好地支持 classical docking 的 pose 预测；二是能否仅凭 docked 或实验复合物中的逐残基 interaction profile，用 random forest 预测配体是否为 active，以及 active 进一步属于哪种功能类。

## 方法

- docking/pose features与classifier。

## 数据与基准

- GPCR complexes/ligands/functional labels。

## 比较基线

- docking scores/ML models。

## 结果证据

- 论文报告pose/classification性能；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- GPCR conformations/biased labels，无实验。

## 仍未知

- 前瞻性 virtual screening 中对真实新化合物的富集效果仍未知。
- 对更多 GPCR 亚家族、非 orthosteric 口袋或全新的配体化学空间的泛化能力未知。
- 论文公开的 GitHub 代码是否能在当前环境无缝复现，未被独立核验。

## Pi 结构化证据摘录

- **baseline：** 相对 SiteFinder，fingerprint guidance 只有 modest improvement，且作者明确指出在最终 top-ranked poses 上没有 substantial advantage，因此改用自动选口袋来训练分类器。
  - 证据：[doi:10.3390/ijms25136876, p.6]；[doi:10.3390/ijms25136876, p.8]
- **baseline：** 相对四分类初始输出，merged active 明显更稳；外部集初始四分类 accuracy/precision/recall 只有 0.03，majority rule 下也只有 0.04。
  - 证据：[doi:10.3390/ijms25136876, p.15]；[doi:10.3390/ijms25136876, p.16]
- **baseline：** 作者还把结果与 TAAR5 相关虚拟筛选工作做了语境比较，强调自己的 hit rate 更有希望，但这只是论文内的定性比较，不是同一基准下的严格对照。
  - 证据：[doi:10.3390/ijms25136876, p.28]
- **data：** 内部数据集总计 1820 个复合物，其中 342 个是公开 PDB 中的实验结构 actives，342 个是 self-docked actives，326 个是 cross-docked actives。
  - 证据：[doi:10.3390/ijms25136876, p.10]；[doi:10.3390/ijms25136876, p.24]
- **data：** 内部数据集另外包含 285 个 DUD-E inactives into experimental structures、285 个 inactives into homology models，以及 240 个 actives into homology models。
  - 证据：[doi:10.3390/ijms25136876, p.10]；[doi:10.3390/ijms25136876, p.24]
- **data：** 外部验证集由 120 个 docked complexes 构成，来自 6 个 ligand 在 GPR31 与 TAAR2 的 4 种模型来源中各自 docking 的结果。
  - 证据：[doi:10.3390/ijms25136876, p.11]；[doi:10.3390/ijms25136876, p.12]；[doi:10.3390/ijms25136876, p.24]
- **data：** 用于 homology modeling 的 DUD-E targets 为 AA2AR、ADRB1、ADRB2、CXCR4 和 DRD3；外部集模型则来自 in-house homology models、GPCRdb active/inactive template models 与 AlphaFold models。
  - 证据：[doi:10.3390/ijms25136876, p.8]；[doi:10.3390/ijms25136876, p.9]；[doi:10.3390/ijms25136876, p.11]；[doi:10.3390/ijms25136876, p.24]
- **declared_resources：** 论文显式使用了 PDB、RING Server、MOE 2019、DUD-E、GPCRdb、IUPHAR/BPS Guide to Pharmacology 和 AlphaFold Protein Structure Database 等资源。
  - 证据：[doi:10.3390/ijms25136876, p.5]；[doi:10.3390/ijms25136876, p.9]；[doi:10.3390/ijms25136876, p.11]；[doi:10.3390/ijms25136876, p.21]；[doi:10.3390/ijms25136876, p.23]；[doi:10.3390/ijms25136876, p.24]
- **declared_resources：** 实现层面使用 Python 3.9.7 和 scikit-learn 0.24.2，classifier 的核心参数包括 n_estimators=500、class_weight=balanced_subsample、bootstrap=False、max_depth=30。
  - 证据：[doi:10.3390/ijms25136876, p.26]
- **declared_resources：** 文末声明 classifier 已公开到 GitHub：https://github.com/gszwabowski/GPCR_DB_project。
  - 证据：[doi:10.3390/ijms25136876, p.29]
- **limitations：** fingerprint 对 docking site selection 的增益有限，且对最终 top 5 scoring 不能稳定超越 SiteFinder，所以它没有成为后续 classifier 的必要输入。
  - 证据：[doi:10.3390/ijms25136876, p.6]；[doi:10.3390/ijms25136876, p.8]；[doi:10.3390/ijms25136876, p.27]
- **limitations：** 外部验证集很小，而且只有 1 个 inactive ligand，因此模型识别 inactive 的能力并没有被充分测试。
  - 证据：[doi:10.3390/ijms25136876, p.19]
- **limitations：** 分类器目前只适用于 orthosteric site；作者明确说 allosteric site classifier 在现有公开 GPCR-allosteric complexes 数量下还不可行。
  - 证据：[doi:10.3390/ijms25136876, p.28]
- **limitations：** 模型在 homology models 上的表现弱于实验结构，说明结构误差会直接传递到 docked pose 与功能预测中。
  - 证据：[doi:10.3390/ijms25136876, p.9]；[doi:10.3390/ijms25136876, p.18]；[doi:10.3390/ijms25136876, p.28]
- **method：** 作者先从 PDB 提取已解析的 GPCR-ligand complexes，用 RING Server 和 Ballesteros–Weinstein 编号构建 global 以及按 activation state 划分的 ligand interaction fingerprints，并拿这些 fingerprints 与 MOE 的 SiteFinder 做 docking site selection 对比。
  - 证据：[doi:10.3390/ijms25136876, p.5]；[doi:10.3390/ijms25136876, p.6]；[doi:10.3390/ijms25136876, p.21]；[doi:10.3390/ijms25136876, p.22]
- **method：** 内部训练/测试集由 1820 个 class A GPCR-ligand complexes 组成，分成实验结构、self-docked、cross-docked、DUD-E 的 inactive into experimental structures、inactive into homology models、active into homology models 六类。
  - 证据：[doi:10.3390/ijms25136876, p.9]；[doi:10.3390/ijms25136876, p.10]；[doi:10.3390/ijms25136876, p.22]；[doi:10.3390/ijms25136876, p.24]
- **method：** 每个复合物按 BW 残基位点提取 interaction energy sum、最有利与次有利 interaction type/energy；缺失位点记为 NA/NA，存在但不相互作用记为 0/None，最后保留 63 个足够常见的 BW 位点作为特征。
  - 证据：[doi:10.3390/ijms25136876, p.12]；[doi:10.3390/ijms25136876, p.13]；[doi:10.3390/ijms25136876, p.25]；[doi:10.3390/ijms25136876, p.26]
- **method：** 分类器用 Python 3.9.7 和 scikit-learn 0.24.2 的 RandomForestClassifier 实现，采用 75/25 train-test split、10-fold cross-validation 和参数调优；外部验证集则来自 GPR31 与 TAAR2 的已知配体在 in-house、GPCRdb 与 AlphaFold 模型中的 docking。
  - 证据：[doi:10.3390/ijms25136876, p.11]；[doi:10.3390/ijms25136876, p.14]；[doi:10.3390/ijms25136876, p.23]；[doi:10.3390/ijms25136876, p.24]；[doi:10.3390/ijms25136876, p.26]
- **method：** 为了处理同一 ligand 的多个 docked poses，作者把四分类输出后处理为 merged active 二分类，并在 external dataset 上再用 majority rule 把每个 GPCR model–ligand pairing 汇总为单一预测。
  - 证据：[doi:10.3390/ijms25136876, p.15]；[doi:10.3390/ijms25136876, p.16]；[doi:10.3390/ijms25136876, p.26]；[doi:10.3390/ijms25136876, p.27]
- **results：** fingerprint 作为 docking site selection 工具只带来有限收益：global fingerprints 的 sampling 成功率为 35.0%，高于 SiteFinder 的 30.0%，但 top 5 scoring 的成功率并未稳定优于自动方法。
  - 证据：[doi:10.3390/ijms25136876, p.6]；[doi:10.3390/ijms25136876, p.7]
- **results：** activation-state-specific fingerprints 也只是轻微降低了 sampling 失败率，例如 inactive 与 intermediate fingerprints 的 unsuccessful sampling 均为 25%，但对 top 5 scoring 没有形成决定性优势。
  - 证据：[doi:10.3390/ijms25136876, p.7]；[doi:10.3390/ijms25136876, p.8]
- **results：** 四分类 random forest 在内部测试集上的 cross-validation score 为 0.80，testing accuracy/precision/recall 均为 0.76。
  - 证据：[doi:10.3390/ijms25136876, p.14]；[doi:10.3390/ijms25136876, p.15]
- **results：** 把 agonist、antagonist、inverse agonist 合并为 active 后，内部测试集的 accuracy、precision、recall 都升到 0.85，hit rate 达到 95.4%。
  - 证据：[doi:10.3390/ijms25136876, p.17]；[doi:10.3390/ijms25136876, p.27]
- **results：** 对实验结构子集，merged active 的 accuracy/precision/recall 为 0.96，hit rate 为 97.6%；对 modeled structure 子集，三项指标降到 0.60，hit rate 为 80.6%。
  - 证据：[doi:10.3390/ijms25136876, p.17]；[doi:10.3390/ijms25136876, p.18]
- **results：** 外部验证集在 merged active + majority rule 后达到 accuracy/precision/recall 0.79，binder hit rate 82.6%，且不同模型来源的 hit rate 大致在 80.0%–83.3% 之间。
  - 证据：[doi:10.3390/ijms25136876, p.19]；[doi:10.3390/ijms25136876, p.20]

## 页码证据

- [doi:10.3390/ijms25136876, p.1]
- [doi:10.3390/ijms25136876, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
