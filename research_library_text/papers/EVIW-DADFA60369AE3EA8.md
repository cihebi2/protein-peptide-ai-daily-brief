# t-SMILES: a fragment-based molecular representation framework for de novo ligand design

- **论文 ID：** `EVIW-DADFA60369AE3EA8`
- **期刊 / 来源：** Nat Commun
- **发表时间：** 2024 Jun 11
- **DOI：** [10.1038/s41467-024-49388-6](https://doi.org/10.1038/s41467-024-49388-6)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 t-SMILES，一种基于分子片段、AMT/FBT 与 BFS 编码的多尺度字符串表示框架，并给出 TSSA、TSDY、TSID 三种编码及其重构/生成流程，声称可在 de novo ligand design 中优于 SMILES、DeepSMILES、SELFIES 及若干 fragment/graph 基线。

## 创新边界

`核心新意主要在表示与编码流程，不是新化学任务本身。`。这不是全球首创性检索或独立复现结论。

## 研究问题

现有分子表示在生成任务中常受 SMILES 语法长程依赖、低资源场景过拟合，以及 fragment/graph 方法可扩展性不足的限制，导致难以同时获得高 validity、novelty 与分布拟合。

## 方法

- 片段分解与树编码；共享原子/虚拟原子/ID三变体；多种生成模型与低资源微调；目标导向任务。

## 数据与基准

- 通用分子生成和带标签低资源集合；多种表示在相同模型条件比较。

## 比较基线

- classical SMILES、DeepSMILES、SELFIES和模型/数据增强基线。

## 结果证据

- 论文报告相对SMILES、DeepSMILES、SELFIES及基线在目标导向任务更好，并在低资源中保持新颖性与相似性。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 未测试更复杂分子；片段规则和ring-opening仍有问题；计算指标不证明可合成性。

## 仍未知

- 补充材料中的逐任务超参数、重复实验方差与更多对照细节未在主文完整展开。
- 重构式 goal-directed 结果对碎片切分规则与候选选择策略的敏感性，仍需要外部复现进一步确认。
- 公开代码与数据在文中给出，但我未在本次纸面审查中外部打开验证其可运行性。

## Pi 结构化证据摘录

- **baseline：** 相较 SMILES、DeepSMILES、SELFIES，t-SMILES 更容易在 novelty 与 FCD 之间取得平衡；文中也指出 DeepSMILES 和 SELFIES 往往仍需额外优化才能稳定接近 SMILES 的表现。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.6]；[doi:10.1038/s41467-024-49388-6, p.7]；[doi:10.1038/s41467-024-49388-6, p.8]；[doi:10.1038/s41467-024-49388-6, p.11]
- **baseline：** 与 Graph MCTS、hG2G、MGM、JTVAE、FragDgm、FASMIFRA 等 fragment/graph 基线相比，t-SMILES 在分布学习和片段生成任务中整体更强；其中 Graph MCTS 的 FCD 极低，而 JTVAE 在 Zinc 上的属性拟合能力较弱。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.7]；[doi:10.1038/s41467-024-49388-6, p.8]；[doi:10.1038/s41467-024-49388-6, p.10]；[doi:10.1038/s41467-024-49388-6, p.11]
- **data：** 低资源实验使用 JNK3 的 923 个 active molecules 与 AID1706 的 329 个 active molecules，以模拟真实的稀缺标注场景。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.6]
- **data：** 大规模分布学习与性质拟合主要在 ChEMBL、Zinc 和 QM9 上进行，并报告 validity、uniqueness、novelty、KLD、FCD 及理化性质分布指标。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.8]；[doi:10.1038/s41467-024-49388-6, p.11]
- **data：** goal-directed 评估使用 GuacaMol 风格的子任务，如 T9.MM1、T16.SMPO 和 T18.VS，并通过多轮重构候选中选取最高分分子。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.9]；[doi:10.1038/s41467-024-49388-6, p.10]
- **declared_resources：** 作者在主文给出 GitHub、Zenodo 与 Code Ocean 代码/数据入口，并声明提供 source data。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.13]；[doi:10.1038/s41467-024-49388-6, p.14]；[doi:10.1038/s41467-024-49388-6, p.15]
- **declared_resources：** 论文资助来自 National Natural Science Foundation of China（21874040、22174036、22204049）。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.15]
- **limitations：** 作者明确写到尚未在更复杂分子上做实验，因此对更高难度化学空间的外推仍未验证。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.12]
- **limitations：** 文中也承认 t-SMILES 的 tree structure 是否能被 LLMs 真正学习、以及如何进一步设计更强的 reconstruction/optimization 机制，仍有待后续研究。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.12]；[doi:10.1038/s41467-024-49388-6, p.13]
- **method：** 先将分子图按选定 fragmentation algorithm 切分为合法片段，构成 AMT，再转成 FBT，最后用 BFS 遍历得到 t-SMILES；重构时按逆过程恢复分子。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.12]；[doi:10.1038/s41467-024-49388-6, p.13]
- **method：** 论文定义了三种编码：TSSA 以 shared atom 连接片段，TSDY 与 TSID 以 dummy atom 连接，其中 TSID 还保留 ID；同时引入“&”和“^”作为树节点与片段分隔符。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.12]；[doi:10.1038/s41467-024-49388-6, p.13]
- **method：** 实验体系同时覆盖 JTVAE、BRICS、MMPA、Scaffold 四种 fragmentation 方式，并在 distribution learning、goal-directed 与 physicochemical 三类基准上评估。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.2]；[doi:10.1038/s41467-024-49388-6, p.8]；[doi:10.1038/s41467-024-49388-6, p.10]；[doi:10.1038/s41467-024-49388-6, p.11]
- **method：** 作者把 classical SMILES 作为 TS_Vanilla 纳入 t-SMILES 家族，并通过 hybrid code 组合多种分解策略来增强表示互补性。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.1]；[doi:10.1038/s41467-024-49388-6, p.12]
- **results：** 在 JNK3 与 AID1706 上，SMILES、DSMILES、SELFIES 的 novelty 随训练增加迅速接近 0，而 t-SMILES 维持约 0.8 左右的稳定 novelty，混合模型和 transfer learning 进一步改善 FCD 与 active novelty 的平衡。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.6]；[doi:10.1038/s41467-024-49388-6, p.7]
- **results：** 在 ChEMBL 上，t-SMILES 整体优于 Graph MCTS、hG2G、MGM 及多种 sequence baselines；其中 TSID_B 和 TSID_S 在 FCD 与 novelty 上都超过 SMILES。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.7]；[doi:10.1038/s41467-024-49388-6, p.8]
- **results：** 在 goal-directed reconstruction 中，t-SMILES 在 T9.MM1、T16.SMPO 和 T18.VS 上都给出最强或接近最强表现，且 TSMG 在 T16.SMPO 上尤其突出。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.9]；[doi:10.1038/s41467-024-49388-6, p.10]
- **results：** 在 Zinc 上，t-SMILES 几乎都能达到 100% validity，并在 novelty/FCD 上普遍优于 JTVAE、FragDgm、SMILES、DSMILES、SELFIES 等基线；在 QM9 上也保持很高的 FCD 并优于图基线。
  - 证据：[doi:10.1038/s41467-024-49388-6, p.10]；[doi:10.1038/s41467-024-49388-6, p.11]

## 页码证据

- [doi:10.1038/s41467-024-49388-6, p.12]
- [doi:10.1038/s41467-024-49388-6, p.13]
- [doi:10.1038/s41467-024-49388-6, p.1]
- [doi:10.1038/s41467-024-49388-6, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
