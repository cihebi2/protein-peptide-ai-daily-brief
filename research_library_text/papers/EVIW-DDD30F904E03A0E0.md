# Prospective de novo drug design with deep interactome learning

- **论文 ID：** `EVIW-DDD30F904E03A0E0`
- **期刊 / 来源：** Nat Commun
- **发表时间：** 2024 Apr 22
- **DOI：** [10.1038/s41467-024-47613-w](https://doi.org/10.1038/s41467-024-47613-w)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 DRAGONFLY：一种由 GTNN 编码、LSTM 解码的 graph-to-sequence 框架，利用 ChEMBL/PDBBind 构建的 drug-target interactome 进行 zero-shot 分子生成；并在 human PPARγ 结构基础设计中前瞻性合成、测试并解析了命中分子的晶体结构。

## 创新边界

`可核验的新意主要是“interactome conditioning + 2D/3D graph-to-sequence generation + prospective PPARγ validation”的组合；冻结页未提供独立 prior-art 搜索，因此只能确认论文内的新方法组合，而不能证明其全局首创。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在药物-靶标 interactome 上训练一个可同时处理 2D ligand 图与 3D binding-site 图的生成模型，以便在不依赖目标特异性 transfer learning 或 reinforcement learning 的前提下，直接生成兼顾活性、选择性、可合成性、新颖性和理化性质的 de novo 小分子，并验证其在 PPARγ 上的前瞻性可行性。

## 方法

- 生成器产生分子，KRR/深度interactome模型按PPAR活性、选择性、物化和可合成性排序；结构基础分支结合口袋信息、QSAR与自由能等计算，选择两个顶级设计合成，并对所得1-3号化合物做报告基因、ITC、选择性和ADME面板。

## 数据与基准

- 大规模药物-靶点interactome和化学语言模型训练语料；前瞻案例使用PPARγ结构PDB 3G9E；最终合成设计1、设计2及其区域异构体3，并在PPARα/γ/δ及其他核受体上表征。

## 比较基线

- 与标准化学语言模型、SMILES和图表示DRAGONFLY版本，以及配体基础/结构基础生成策略比较；论文也讨论强化学习、迁移学习、few-shot和其他结构生成方法。

## 结果证据

- 设计1经ITC测得PPARγ KD=0.8±0.1微摩尔并呈预期PPARγ/δ双活性；设计2的PPARγ EC50=2.3±0.7微摩尔且对PPARδ无明显活性；三者对其他核受体的预期选择性得到实验支持。设计1总收率12%，设计2仅0.6%，显示可合成预测并非等于高收率。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 前瞻湿实验集中于单个PPAR体系，且只合成两个顶级设计和一个异构体，样本不足以估计一般成功率。 作者未设置独立的正式局限章节；广泛零样本泛化仍主要来自计算基准。 设计2的0.6%总收率提示合成可行性评分不能替代路线难度和收率评估。 部分interactome与实验资源可能受企业/合作环境影响，独立复现需检查开放程度。

## 仍未知

- 冻结页未提供独立 prior-art 检索，无法证明全局首创。
- 只给出 PPARγ 前瞻性案例，跨靶点泛化仍需更多实证。
- 合成可行性评分与实际合成复杂度存在偏差，改进空间明显。

## Pi 结构化证据摘录

- **baseline：** 主对照是 fine-tuned RNN/CLM；DRAGONFLY 用相同评价指标与其比较，以评估生成质量。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.4]；[doi:10.1038/s41467-024-47613-w, p.5]
- **baseline：** QSAR 部分还与 gradient boosting 和 XGBoost 等决策树基线比较，KRR 被报告为更优。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.3]
- **baseline：** 对于 novelty 与 similarity 分析，还把 ChEMBL 训练集与外部 PubChem 集合做了对照。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.4]
- **data：** 训练数据来源于 ChEMBL 和 PDBBind；蛋白结合位点只保留距配体 5 Å 内原子，且对 allosteric 与 orthosteric 位点分开编号。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.2]；[doi:10.1038/s41467-024-47613-w, p.13]
- **data：** 前瞻性研究刻意把 PPAR 家族及近缘结构从训练集中排除，最近的相关蛋白仅为 THRβ1 和 LXRβ，序列一致性约 33% 与 30%。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.6]
- **data：** 实验部分合成了 compounds 1–3，并对其做了 reporter gene assay、ITC、ADME、off-target panel、ABFEP 和 X-ray co-crystallization。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.7]；[doi:10.1038/s41467-024-47613-w, p.8]；[doi:10.1038/s41467-024-47613-w, p.14]
- **declared_resources：** 代码资源：作者在 page 15 给出 DRAGONFLY 的 reference implementation，托管于 GitHub，并给出 Zenodo DOI。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.15]
- **declared_resources：** 数据资源：Source data 以 Source_Data.zip 发布在 Figshare，且共晶结构可在 PDB 中以 8PBO 获取。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.15]；[doi:10.1038/s41467-024-47613-w, p.14]
- **declared_resources：** 实验资源：文中明确使用 ChEMBL v29、PDBBind 2020、PDB 3G9E 与 PPARγ LBD 构建体 L204-Y477 等资源。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.13]；[doi:10.1038/s41467-024-47613-w, p.14]
- **limitations：** 作者自己也承认 synthesizability score 不够可靠：两个最优分子合成分别要 10 步和 5 步，且收率偏低。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.8]；[doi:10.1038/s41467-024-47613-w, p.11]
- **limitations：** 结构基础评分仍依赖已知配体活性数据训练的 QSAR，因此并不是完全不借助先验活性标签的独立打分。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.10]；[doi:10.1038/s41467-024-47613-w, p.14]
- **limitations：** 结构基础模型训练数据更少、输入图更大，作者也指出需要进一步测试 apo protein 与 AlphaFold 等预测结构场景。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.10]
- **limitations：** novelty 评估是相对 training set/PubChem 的内部度量，冻结页没有给出能证明全局新颖性的独立证据。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.4]
- **method：** 先以 ChEMBL v29 提取生物活性标注，结合 PDBBind 2020 的结构条目，构建 ligand-based 与 structure-based 两个 drug-target interactome；以 ≤200 nM、最少 10 个化合物/靶标等规则筛选后，得到约 360k ligands/2989 targets/501k bioactivities 与约 208k ligands/726 targets/263k bioactivities 的训练图。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.2]；[doi:10.1038/s41467-024-47613-w, p.13]
- **method：** 模型编码器是 GTNN：2D 图以共价键连边，3D 图以 4 Å 半径连边，3 层 message passing 后经 GMT 压缩，再由 LSTM 逐字符解码成 SMILES 或 SELFIES。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.11]；[doi:10.1038/s41467-024-47613-w, p.12]
- **method：** 评分模块使用 KRR 建立 QSAR，输入 ECFP4、CATS、USRCAT 三类描述符；新颖性由 ECFP Jaccard 距离与 atom/carbon scaffold novelty 共同定义，合成可行性用 RAScore。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.2]；[doi:10.1038/s41467-024-47613-w, p.12]；[doi:10.1038/s41467-024-47613-w, p.13]
- **method：** 前瞻性案例中，先对 human PPARγ binding pocket 生成 300k molecules，再用 MW、RAScore、novelty 和 QSAR 排序，分别做单靶点与 PPARγ/δ 双靶点策略。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.6]
- **results：** 理化性质翻译结果显示，各属性的 Pearson r 都不低于 0.95，说明用户设定性质能较准确地投影到生成分子上。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.2]
- **results：** 在 20 个已知靶标模板上，DRAGONFLY 相比 fine-tuned RNN 在大多数模板和性质上表现更优；而 ligand-based 设计在全部比较场景中又优于 structure-based。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.4]；[doi:10.1038/s41467-024-47613-w, p.5]
- **results：** SELFIES 版生成库更新颖、scaffold 多样性更高，但 SMILES 版在 synthesizability、预测活性和部分理化属性上更准，因此作者最终用于前瞻性实验的是 SMILES 模型。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.4]；[doi:10.1038/s41467-024-47613-w, p.5]
- **results：** PPARγ 案例中，compound 1/2/3 都获得实验支持：compound 1 对 PPARγ/δ 双活性，compound 2 对 PPARγ 选择性，compound 3 为双靶点 partial agonist；compound 1 的共晶结构与 ABFEP 结果也支持其预测结合模式。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.6]；[doi:10.1038/s41467-024-47613-w, p.7]；[doi:10.1038/s41467-024-47613-w, p.8]
- **results：** ADME 与安全性结果总体积极：两化合物具备可接受的 logD、膜通透性、低 CYP 相互作用、较低细胞毒性，且 safety panel 中未见明显 off-target 风险。
  - 证据：[doi:10.1038/s41467-024-47613-w, p.7]

## 页码证据

- [doi:10.1038/s41467-024-47613-w, p.15]
- [doi:10.1038/s41467-024-47613-w, p.1]
- [doi:10.1038/s41467-024-47613-w, p.2]
- [doi:10.1038/s41467-024-47613-w, p.3]
- [doi:10.1038/s41467-024-47613-w, p.4]
- [doi:10.1038/s41467-024-47613-w, p.6]
- [doi:10.1038/s41467-024-47613-w, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
