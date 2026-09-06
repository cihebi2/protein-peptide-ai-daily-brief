# VGAE-MCTS: A New Molecular Generative Model Combining the Variational Graph Auto-Encoder and Monte Carlo Tree Search

- **论文 ID：** `EVIW-E055FF023C0B29CB`
- **期刊 / 来源：** J Chem Inf Model
- **发表时间：** 2023 Nov 22
- **DOI：** [10.1021/acs.jcim.3c01220](https://doi.org/10.1021/acs.jcim.3c01220)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `扩散/生成` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

本文提出 VGAE-MCTS：先用 VGAE 学习已知化合物的图表示分布，再用 MCTS 逐步连接原子与键进行分子生成，从而探索此前模型较难覆盖的化学空间，并提升 QED 与 penalized log P 等目标性质。

## 创新边界

`创新边界主要在于将 VGAE 的 latent feature map 与 MCTS 搜索过程直接耦合，并加入芳香环优先生成与结构过滤机制；文中展示了相对所选基线的性能提升，但并未提供独立证据证明其对全部 prior art 的全球首创性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何把分子图的深度生成学习与强化学习式搜索结合起来，在保持分子有效性和新颖性的同时，生成并优化满足目标理化性质的候选分子。

## 方法

- graph VAE学习molecules，MCTS按property reward扩展。

## 数据与基准

- 分子生成benchmarks。

## 比较基线

- VAE/RL/MCTS generators。

## 结果证据

- 论文报告validity/property优势；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- reward bias、无target/实验。

## 仍未知

- 未见湿实验、合成或生物活性验证。
- 未见针对具体靶点的前瞻性设计案例。
- 公开仓库已在文中给出，但本任务未核验其复现质量与依赖环境。

## Pi 结构化证据摘录

- **baseline：** 分布学习基线包括 GraphMCTS 和 VGAE，文中直接引用 Mahmood 等的结果进行对照。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.4]
- **baseline：** QED 与 penalized log P 优化的直接对照基线是 JT-VAE 和 MolDQN，VGAE-MCTS 在两项任务上都被作者报告为更优。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.4]；[doi:10.1021/acs.jcim.3c01220, p.5]
- **baseline：** 化学空间分析还将 JT-VAE 与 MolDQN 作为对照，用于展示不同方法在 ZINC 化学空间中的分布差异。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.5]；[doi:10.1021/acs.jcim.3c01220, p.6]
- **data：** 用于基础生成能力评估的训练集来自 ChEMBL，共 1,352,672 个化合物，并划分为 1,273,104 个训练样本和 79,568 个验证样本。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.2]
- **data：** 用于理化性质优化的训练集来自 ZINC，共 249,456 个化合物，并划分为 199,565 个训练样本和 49,891 个验证样本。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.2]
- **declared_resources：** 作者在文中公开给出 data 和 code 的 GitHub 链接：https://github.com/clinfo/VGAE-MCTS。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.7]
- **declared_resources：** Supporting Information 包含 Supplementary Table 1-3、Supplementary Figure 1-3 及 PDF 附件，可用于复核特征、模型结构和分析结果。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.7]
- **limitations：** MCTS 搜索迭代数被设为 8,000 以平衡计算时间，作者也指出这可能导致生成分子略小，若有更多算力可能生成更大分子。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.6]
- **limitations：** 生成流程依赖 aromatic force cycle mode 和多个硬规则过滤器，说明模型对可探索化学空间施加了较强先验约束。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.3]
- **method：** 作者将分子表示为带节点和边特征的 molecular graph，并用 RDKit 计算特征；VGAE 训练采用 64 维 latent space、learning rate 0.001 和 batch size 64。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.2]；[doi:10.1021/acs.jcim.3c01220, p.3]
- **method：** MCTS 以 VGAE decoder 输出的 feature map 为搜索先验，按 Selection、Expansion、Simulation、Update 逐步连接原子和键；Selection 使用 UCB1 形式，搜索系数 c=1.5。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.3]
- **method：** 模型加入 aromatic force cycle mode，优先生成 5/6 元芳香环，并通过 steric strain filter 和限制大于 7 元环的过滤器来约束生成结构。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.3]
- **method：** 评估包括 GuacaMol Distribution-Learning Benchmarks、QED 与 penalized log P 优化，以及基于 ECFP4+UMAP 的化学空间可视化；QED 与 penalized log P 分别以 1-QED 和 1-sigmoid(penalized log P) 作为 reward。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.3]
- **results：** 在 GuacaMol 分布学习指标上，VGAE-MCTS 的 validity、uniqueness、novelty 均为 1.000，KL divergence 为 0.659，FCD 为 0.009；整体优于或不弱于 GraphMCTS 与 VGAE。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.4]
- **results：** QED 优化时，VGAE-MCTS 生成分子的 QED 均值/中位数为 0.772/0.815，高于 ZINC 及 JT-VAE、MolDQN。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.4]
- **results：** 在 3,000 个 QED-optimized 分子中，VGAE-MCTS 有 432 个 QED > 0.9，而 JT-VAE 为 195 个、MolDQN 为 0 个。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.6]
- **results：** 化学空间映射显示，VGAE-MCTS 生成分子相对 ZINC 仅略有偏移，JT-VAE 更接近训练集，而 MolDQN 偏离更远；作者据此认为 VGAE-MCTS 覆盖了此前模型较少探索的区域。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.5]；[doi:10.1021/acs.jcim.3c01220, p.6]
- **results：** 作者报告 penalized log P 优化下 VGAE-MCTS 的 mean/median 为 0.536/0.606，并称其低值分布更少且优于 JT-VAE、MolDQN；但文中该均值与“高于 ZINC”的文字表述存在数值上的不一致。
  - 证据：[doi:10.1021/acs.jcim.3c01220, p.5]

## 页码证据

- [doi:10.1021/acs.jcim.3c01220, p.1]
- [doi:10.1021/acs.jcim.3c01220, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
