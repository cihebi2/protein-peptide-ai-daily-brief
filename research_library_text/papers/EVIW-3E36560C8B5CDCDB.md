# PepINVENT: generative peptide design beyond natural amino acids

- **论文 ID：** `EVIW-3E36560C8B5CDCDB`
- **期刊 / 来源：** Chem Sci
- **发表时间：** 2025 Apr 16
- **DOI：** [10.1039/d4sc07642g](https://doi.org/10.1039/d4sc07642g)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `扩散/生成` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 PepINVENT：一个基于 transformer 的肽生成与强化学习框架，使用 CHUCKLES 化学字符串表示，在掩码位置填充自然或非天然氨基酸，并可进一步对环化拓扑、溶解度与膜通透性进行多目标优化。

## 创新边界

`仅能确认其在冻结文献内相对训练集与引用工作的增量；没有独立 prior-art 证据支持全局新颖性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

设计一个能够超越天然氨基酸枚举空间、同时支持多拓扑与多性质约束的肽生成框架，用于候选肽的生成与优化。

## 方法

- peptide tokenization、conditional generative model与property optimization。

## 数据与基准

- 天然/非天然peptide chemical space与benchmark。

## 比较基线

- 天然字母表peptide generators。

## 结果证据

- 论文报告validity/diversity/property控制；主要为计算，实验仅按正文明确部分。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 非天然残基可合成性/活性与训练coverage有限。

## 仍未知

- 生成的 novel amino acids 是否在真实合成路线中普遍可实现，页面未给出实验验证。
- RBP MPO 结果是否能在独立实验中复现，冻结证据未覆盖。
- 外部 prior art 的全局新颖性没有独立检索证据，不能据此下最终 novelty 结论。

## Pi 结构化证据摘录

- **baseline：** 本文的生成骨架与训练超参基本沿用 REINVENT transformer，因此主要基线更像是该框架的迁移式扩展，而非从零构建的新模型族。
  - 证据：[doi:10.1039/d4sc07642g, p.5]；[doi:10.1039/d4sc07642g, p.13]；[doi:10.1039/d4sc07642g, p.14]
- **baseline：** 膜通透性预测器基线为基于 CycPeptMPDB 的 XGBoost 分类器，测试集 balanced accuracy 为 0.78、Matthews correlation coefficient 为 0.59。
  - 证据：[doi:10.1039/d4sc07642g, p.7]
- **baseline：** 实验比较主要发生在 beam search vs multinomial sampling，以及不同 RL score transformations 之间；冻结页面中没有看到新的湿实验对照基线。
  - 证据：[doi:10.1039/d4sc07642g, p.6]；[doi:10.1039/d4sc07642g, p.8]；[doi:10.1039/d4sc07642g, p.11]；[doi:10.1039/d4sc07642g, p.13]
- **data：** 训练语料来自 380,000 个可合成非天然氨基酸的虚拟库，作者据此生成 1,000,000 条 unique peptides，长度主要在 6–18，非天然氨基酸比例约限制在 0 到 0.3。
  - 证据：[doi:10.1039/d4sc07642g, p.2]；[doi:10.1039/d4sc07642g, p.3]
- **data：** 数据集按 90/5/5 划分为 train/validation/test，并另外构建了 400 条 masked peptides 的性能测试集和 40 条 topology-context peptides 的上下文测试集。
  - 证据：[doi:10.1039/d4sc07642g, p.3]；[doi:10.1039/d4sc07642g, p.4]；[doi:10.1039/d4sc07642g, p.6]
- **data：** 用于 MPO 的 Rev-binding peptide 案例以 YPAASYR 为起点，并根据既有工作将部分 alanine 与 glycine 位置设为待修改位点。
  - 证据：[doi:10.1039/d4sc07642g, p.11]；[doi:10.1039/d4sc07642g, p.12]
- **declared_resources：** Semi-synthetic training 和 validation data 公开在 Zenodo。
  - 证据：[doi:10.1039/d4sc07642g, p.14]
- **declared_resources：** GitHub 仓库 https://github.com/MolecularAI/PepINVENT/ 提供测试配置、CHUCKLES demo notebook，以及 supervised learning、sampling 和 RL 代码。
  - 证据：[doi:10.1039/d4sc07642g, p.14]
- **declared_resources：** CAMSOL-PTM intrinsic solubility scorer 以免费学术 web server 形式提供。
  - 证据：[doi:10.1039/d4sc07642g, p.14]
- **limitations：** 非天然氨基酸比例区间 [0, 0.3] 是作者人为设定的，且文中明确指出高比例 NNAAs 会显著影响 synthetic feasibility。
  - 证据：[doi:10.1039/d4sc07642g, p.3]
- **limitations：** 训练数据是 semi-synthetic 的，并非围绕特定性质或特定拓扑构造，因此模型学习到的是较通用的 peptide chemistry，而不是单一任务分布。
  - 证据：[doi:10.1039/d4sc07642g, p.2]；[doi:10.1039/d4sc07642g, p.13]
- **limitations：** 性质优化依赖外部 surrogate，如 CAMSOL-PTM 和 permeability classifier；作者也在讨论中表示后续还要扩展 synthetic feasibility scoring。
  - 证据：[doi:10.1039/d4sc07642g, p.7]；[doi:10.1039/d4sc07642g, p.12]；[doi:10.1039/d4sc07642g, p.14]
- **method：** 作者用 CHUCKLES 将氨基酸按 N-to-C 方向编码为可拼接的化学字符串，并把生成任务表述为 source/target 形式的掩码填空。
  - 证据：[doi:10.1039/d4sc07642g, p.2]；[doi:10.1039/d4sc07642g, p.4]；[doi:10.1039/d4sc07642g, p.5]
- **method：** 半合成训练数据同时包含自然氨基酸与来自虚拟库的非天然氨基酸，并覆盖 linear、head-to-tail、disulphide bridge 和 sidechain-to-tail 四类拓扑，还引入 stereochemical mutation 与 backbone N-methylation。
  - 证据：[doi:10.1039/d4sc07642g, p.2]；[doi:10.1039/d4sc07642g, p.3]；[doi:10.1039/d4sc07642g, p.4]
- **method：** 生成器采用与 REINVENT 相同实现风格的 transformer encoder-decoder，并在 900K masked peptide pairs 上训练 24 epochs，使用 Adam、learning rate 0.0001、batch size 16、4000 warm-up steps 和 NVIDIA V100。
  - 证据：[doi:10.1039/d4sc07642g, p.5]；[doi:10.1039/d4sc07642g, p.6]
- **method：** 强化学习部分复用 REINVENT infrastructure，并以 ring size、CAMSOL-PTM 溶解度、permeability classifier、custom alerts 和 diversity filter 作为 scoring components。
  - 证据：[doi:10.1039/d4sc07642g, p.6]；[doi:10.1039/d4sc07642g, p.7]；[doi:10.1039/d4sc07642g, p.12]
- **results：** 在主测试集上，PepINVENT 的 peptide validity 约为 98–99%，peptide uniqueness 也保持在 98–100% 的高位。
  - 证据：[doi:10.1039/d4sc07642g, p.8]
- **results：** 在 amino-acid 层面，multinomial sampling 比 beam search 生成了更多 unique building blocks；作者报告共生成 91,826 个 novel amino acids。
  - 证据：[doi:10.1039/d4sc07642g, p.8]；[doi:10.1039/d4sc07642g, p.9]；[doi:10.1039/d4sc07642g, p.10]
- **results：** 模型对 topology context 有一定理解：在不完整环化或二硫键输入下，validity 没有明显下降，且各类 topology 的 validity 大致维持在 96–99%。
  - 证据：[doi:10.1039/d4sc07642g, p.10]
- **results：** RL 能把生成过程推向目标拓扑，在约 40 步左右达到目标，整体上少于 50 步即可在 macrocycle、head-to-tail 或 linear 之间切换。
  - 证据：[doi:10.1039/d4sc07642g, p.10]；[doi:10.1039/d4sc07642g, p.11]
- **results：** 在 RBP 的 MPO 演示中，作者报告了 5,146 个满足条件的 soluble macrocyclic peptides（permeability > 0.6），以及 534 个超过 0.7、1 个超过 0.8 的样本。
  - 证据：[doi:10.1039/d4sc07642g, p.13]
- **results：** 生成结果中还出现了训练集中未见的 bicyclic peptides，说明模型可以触及未见拓扑空间。
  - 证据：[doi:10.1039/d4sc07642g, p.11]

## 页码证据

- [doi:10.1039/d4sc07642g, p.1]
- [doi:10.1039/d4sc07642g, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
