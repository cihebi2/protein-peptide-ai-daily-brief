# Enabling target-aware molecule generation to follow multi objectives with Pareto MCTS

- **论文 ID：** `EVIW-9A5BE8BC839DD39C`
- **期刊 / 来源：** Commun Biol
- **发表时间：** 2024 Sep 2
- **DOI：** [10.1038/s42003-024-06746-w](https://doi.org/10.1038/s42003-024-06746-w)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 ParetoDrug，一种把预训练 target-aware autoregressive 生成模型与 Pareto MCTS 结合的分子生成方法，用于在单一靶点与多靶点场景中同步优化多个分子性质，并通过 ParetoPUCT 与全局 Pareto pool 提升搜索质量。[doi:10.1038/s42003-024-06746-w, p.1] [doi:10.1038/s42003-024-06746-w, p.11] [doi:10.1038/s42003-024-06746-w, p.12]

## 创新边界

`创新边界主要是多目标 target-aware molecule generation 的搜索框架，而不是新的湿实验发现或新的靶点生物学机制。[doi:10.1038/s42003-024-06746-w, p.1] [doi:10.1038/s42003-024-06746-w, p.11]`。这不是全球首创性检索或独立复现结论。

## 研究问题

在已知蛋白靶点条件下，如何同时优化结合亲和力与药物样性质（如 LogP、QED、SA、NP-likeness），并在大而稀疏的化学空间中稳定搜索到满足多目标的候选小分子。[doi:10.1038/s42003-024-06746-w, p.1]

## 方法

- 自回归生成分子，MCTS扩展化学序列；用多个目标奖励维护非支配解并搜索Pareto前沿。

## 数据与基准

- 训练/测试数据来自BindingDB和PDBbind，并在多目标基准和两个疾病靶点案例上评价。

## 比较基线

- AlphaDrug、TargetDiff及单目标/标量化多目标生成方法。

## 结果证据

- 论文报告可生成兼具对接分数和drug-likeness的Pareto候选；案例仍是计算生成和评分。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 性能依赖代理评分和稀疏终局奖励；作者提出未来兼容扩散生成器，未做候选合成/活性实验。

## 仍未知

- 候选分子是否能在真实合成与生物测定中保持优势尚未知。
- 多靶点/多目标任务的泛化性仅由少量案例支撑。
- 公开代码与数据是否可完整复现全部图表与案例仍需进一步核查。

## Pi 结构化证据摘录

- **baseline：** 基准比较覆盖 Known ligands、LiGANN、SBMolGen、SBDD-3D、Pocket2Mol、CProMG、BeamLmser、TargetDiff、REINVENT 4 与 AlphaDrug；其中 AlphaDrug 与 ParetoDrug 共用同一预训练 Lmser Transformer 与 IT=150 设定。[doi:10.1038/s42003-024-06746-w, p.3] [doi:10.1038/s42003-024-06746-w, p.4]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.3]；[doi:10.1038/s42003-024-06746-w, p.4]
- **baseline：** 案例研究的对照包括 LigBuilder V3、Pocket2Mol-screen 与 TargetDiff-screen；论文也指出 CProMG 的 uniqueness 仅 26.9%，而 ParetoDrug 明显更高。[doi:10.1038/s42003-024-06746-w, p.6] [doi:10.1038/s42003-024-06746-w, p.7] [doi:10.1038/s42003-024-06746-w, p.4]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.6]；[doi:10.1038/s42003-024-06746-w, p.7]；[doi:10.1038/s42003-024-06746-w, p.4]
- **data：** 基准实验从 BindingDB 采样 100 个 protein targets，每个靶点生成 10 个候选分子，共评估 1000 个分子；训练/测试数据来源于 BindingDB 和 PDBbind。[doi:10.1038/s42003-024-06746-w, p.3] [doi:10.1038/s42003-024-06746-w, p.13]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.3]；[doi:10.1038/s42003-024-06746-w, p.13]
- **data：** 案例研究使用 RCSB PDB 提供的 7D42、5G2N、3A2O、4G1Q、1XKK、3BBT 等复合物结构与配体文件作为靶点与分析对象。[doi:10.1038/s42003-024-06746-w, p.5] [doi:10.1038/s42003-024-06746-w, p.6] [doi:10.1038/s42003-024-06746-w, p.7] [doi:10.1038/s42003-024-06746-w, p.13]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.5]；[doi:10.1038/s42003-024-06746-w, p.6]；[doi:10.1038/s42003-024-06746-w, p.7]；[doi:10.1038/s42003-024-06746-w, p.13]
- **data：** 评估指标包括 docking score、Uniqueness、LogP、QED、SA、NP-likeness，案例中还加入 MM-GBSA 与 PLIP 交互分析。[doi:10.1038/s42003-024-06746-w, p.2] [doi:10.1038/s42003-024-06746-w, p.3] [doi:10.1038/s42003-024-06746-w, p.6] [doi:10.1038/s42003-024-06746-w, p.13]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.2]；[doi:10.1038/s42003-024-06746-w, p.3]；[doi:10.1038/s42003-024-06746-w, p.6]；[doi:10.1038/s42003-024-06746-w, p.13]
- **declared_resources：** 论文声明使用 Python 3.7、Biopython、Pandas、MMseqs2、RDKit、PyTorch、Openbabel、PyMOL、AMBER22、PLIP、smina、Matplotlib、Seaborn 和 SciPy 完成数据处理、结构分析与统计检验。[doi:10.1038/s42003-024-06746-w, p.13]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.13]
- **declared_resources：** 代码公开在 GitHub，论文还提供 Google Colab 版本；数值源数据与 codes/data 也放在 Figshare，并明确说明训练/测试数据来自 BindingDB 与 PDBbind。[doi:10.1038/s42003-024-06746-w, p.13]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.13]
- **declared_resources：** 经费支持来自 Hong Kong Innovation and Technology Fund（ITS/241/21）与 National Natural Science Foundation of China（22377111）。[doi:10.1038/s42003-024-06746-w, p.15]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.15]
- **limitations：** 作者明确承认，这些计算上看起来有前景的分子仍“far from being drugs”，现有指标不能完全反映真实药物所需性质，因此结论主要仍是 in silico 证据。[doi:10.1038/s42003-024-06746-w, p.6]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.6]
- **limitations：** 验证主要依赖 docking 与 MM-GBSA 等代理指标，且文中也提示 MM-GBSA 可能遗漏某些相互作用；缺少湿实验或体内验证来确认真实活性与可成药性。[doi:10.1038/s42003-024-06746-w, p.6] [doi:10.1038/s42003-024-06746-w, p.8]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.6]；[doi:10.1038/s42003-024-06746-w, p.8]
- **limitations：** 作者将后续方向限定为适配更多 autoregressive / diffusion 模型，并扩展到 protein、polypeptide 和 nucleic acid drugs，说明当前框架的外推范围仍有限。[doi:10.1038/s42003-024-06746-w, p.13]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.13]
- **method：** ParetoDrug 以预训练的蛋白-配体自回归模型为先验，在给定蛋白序列和当前分子片段的条件下预测下一原子符号，再用 MCTS 逐步展开完整分子。[doi:10.1038/s42003-024-06746-w, p.11] [doi:10.1038/s42003-024-06746-w, p.12]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.11]；[doi:10.1038/s42003-024-06746-w, p.12]
- **method：** 其多目标版本维护全局 Pareto optimal molecules 池，并用按维度构造的 reward vector 在 Backup 阶段更新搜索树统计量。[doi:10.1038/s42003-024-06746-w, p.12]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.12]
- **method：** 选择阶段提出 ParetoPUCT：先对候选子节点的向量分数构建 Pareto Front，再从非支配节点中随机选取；多靶点时用 M-ParetoPUCT 对多个靶点的 next-atom 分布做 mean-pooling 融合。[doi:10.1038/s42003-024-06746-w, p.12] [doi:10.1038/s42003-024-06746-w, p.13]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.12]；[doi:10.1038/s42003-024-06746-w, p.13]
- **results：** 在基准测试中，ParetoDrug 的 docking score 为 10.9 ± 0.1，QED 为 0.6，SA 为 2.4，NP 为 -0.4；相较 AlphaDrug，它显著改善了 QED、SA、NP，并把 LogP 约束满足率提升到 96.5%。[doi:10.1038/s42003-024-06746-w, p.3] [doi:10.1038/s42003-024-06746-w, p.4]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.3]；[doi:10.1038/s42003-024-06746-w, p.4]
- **results：** 在 FXR 案例中，ParetoDrug 找到 4 个 Pareto Dominate Tropifexor 的分子，且 MM-GBSA 显示它们与已知药物处于相近的结合自由能水平。[doi:10.1038/s42003-024-06746-w, p.5] [doi:10.1038/s42003-024-06746-w, p.6]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.5]；[doi:10.1038/s42003-024-06746-w, p.6]
- **results：** 在 PI3K-γ、HIV 双靶点和 Lapatinib 的多目标案例中，ParetoDrug 继续找到优于已知药物或双抑制剂的候选分子，并展示了可解释的结合构象与相互作用。[doi:10.1038/s42003-024-06746-w, p.6] [doi:10.1038/s42003-024-06746-w, p.7]
  - 证据：[doi:10.1038/s42003-024-06746-w, p.6]；[doi:10.1038/s42003-024-06746-w, p.7]

## 页码证据

- [doi:10.1038/s42003-024-06746-w, p.1]
- [doi:10.1038/s42003-024-06746-w, p.4]
- [doi:10.1038/s42003-024-06746-w, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
