# DeepPath: overcoming data scarcity for protein transition pathway prediction using physics-based deep learning

- **论文 ID：** `EVIW-12CFC2FF0F445FBA`
- **期刊 / 来源：** Chem Sci
- **发表时间：** 2026 May 5
- **DOI：** [10.1039/d5sc08253f](https://doi.org/10.1039/d5sc08253f)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称提出 DeepPath：一个把 generative active learning、progressive GAN Explorer、Structure Builder 和 molecular-mechanics oracle 结合起来的闭环框架，可在无需已知路径数据的情况下生成原子级 protein transition pathways，并在 AdK、SHP2、CdiB 与 BAM 四个体系上复现已知中间态并发现新的构象。

## 创新边界

`新意主要在于把 GAL + physics-based oracle 直接用于蛋白转变路径生成的组合式框架；论文自述的是方法设计与流程创新，但没有独立证明其在更广泛蛋白动力学问题上的全局新颖性或最优性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在标注和路径数据极其稀缺时，如何直接从两个给定端态生成可信的蛋白质转变路径，并同时保留原子级几何连续性、能量合理性与可解释的构象变化。

## 方法

- 结构生成器提出中间构象，物理能量评价提供oracle反馈，Energy Critic近似昂贵力场并迭代训练路径。

## 数据与基准

- 验证AdK开闭、SHP2激活、CdiB H1排出和BAM gate四个案例，并与已知瞬态相互作用比较。

## 比较基线

- 分子动力学、增强采样及已有生成/flow protein dynamics方法。

## 结果证据

- 论文报告重现四个系统的关键瞬态相互作用并显著快于直接MD；这是计算路径验证。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 当前structure builder未显式构建水、脂质和核酸；能量近似及有限案例限制泛化。

## 仍未知

- 未见可直接复用的源码仓库链接，只有模型托管地址，实际复现门槛未知。
- 仅四个案例被验证，跨更多蛋白家族、不同构象类型的泛化范围仍未知。
- 部分端态与基线依赖作者选定的 force field、初始轨迹长度和人工构建端点，独立复现结果未知。
- 论文自报的性能指标尚未经过外部审计，结果是否稳定受超参数与实现细节影响仍未知。

## Pi 结构化证据摘录

- **baseline：** AdK 的比较基线主要是既往关于 adenylate kinase 变构转变的 free-energy / transition-path simulations，DeepPath 结果与其报道的 curved manifold 一致。
  - 证据：[doi:10.1039/d5sc08253f, p.4]
- **baseline：** CdiB 直接对照了 earlier SMD 与 2-ms aggregated REUS 结果，作者认为 DeepPath 以更短计算时间再现了相似路径。
  - 证据：[doi:10.1039/d5sc08253f, p.6]；[doi:10.1039/d5sc08253f, p.7]
- **baseline：** BAM 主要对照 SMwST seeded by TMD；论文报告 SMwST 仍保留结构缺陷且历时 14.5 ms，而 DeepPath 在单 GPU 上完成路径搜索。
  - 证据：[doi:10.1039/d5sc08253f, p.8]；[doi:10.1039/d5sc08253f, p.10]
- **data：** SHP2、CdiB 和 BAM 的初始训练数据分别来自端态 equilibrium MD：SHP2 100 ns、CdiB 10 ns、BAM 两端各 500 ns 片段，并抽取固定帧作为初始集。
  - 证据：[doi:10.1039/d5sc08253f, p.13]；[doi:10.1039/d5sc08253f, p.14]
- **data：** CdiB 还额外构造了 100 个 H1 逐步下移的中间结构，步长为 0.35 Å，用来辅助 DeepPath 在缺少完整路径数据时进行探索。
  - 证据：[doi:10.1039/d5sc08253f, p.13]；[doi:10.1039/d5sc08253f, p.14]
- **data：** SHP2 的端态由 PDB 4DGP 与 6CRF 构建，缺失环区由 AlphaFold 补全；CdiB 与 BAM 模型则沿用前人已发表的构建方案。
  - 证据：[doi:10.1039/d5sc08253f, p.14]
- **declared_resources：** 论文声明已提供 trained models，托管于 Hugging Face：https://huggingface.co/andrewytp/deeppath。
  - 证据：[doi:10.1039/d5sc08253f, p.15]
- **declared_resources：** 论文声明了计算资源来自 TACC Frontera、ACCESS 和 Hive cluster，并列出相关 NSF/NIH 支持。
  - 证据：[doi:10.1039/d5sc08253f, p.15]
- **declared_resources：** 实现依赖 OpenMM 7.7、NAMD、TensorFlow 2.14 等软件栈完成 MD、能量最小化与训练。
  - 证据：[doi:10.1039/d5sc08253f, p.13]；[doi:10.1039/d5sc08253f, p.14]；[doi:10.1039/d5sc08253f, p.19]
- **limitations：** 当前实现只评估 protein potential energy，SHP2 与 CdiB 还使用 implicit solvent，未显式表示 water 或 membrane lipids，因此环境效应被简化。
  - 证据：[doi:10.1039/d5sc08253f, p.10]；[doi:10.1039/d5sc08253f, p.13]；[doi:10.1039/d5sc08253f, p.14]
- **limitations：** 作者明确指出模型对 entropy 与 hydrophobic interactions 刻画不足，且 CdiB 的部分疏水接触未被完整恢复。
  - 证据：[doi:10.1039/d5sc08253f, p.10]；[doi:10.1039/d5sc08253f, p.11]
- **limitations：** 当仅有一个实验端态时，第二端态需要人工构建；这使后半段路径对假设端态的准确度非常敏感。
  - 证据：[doi:10.1039/d5sc08253f, p.11]；[doi:10.1039/d5sc08253f, p.14]
- **limitations：** 不同体系需要调整 critic 权重，且 BAM 这类大体系的训练时间显著上升，说明可扩展性仍有实际成本。
  - 证据：[doi:10.1039/d5sc08253f, p.3]；[doi:10.1039/d5sc08253f, p.10]
- **method：** DeepPath 采用双模块设计：Explorer 先在 reduced coordinates 中提出候选 transition pathways，Structure Builder 再把这些表示重建为 all-atom Cartesian 结构，并由 GAL 闭环持续迭代修正。
  - 证据：[doi:10.1039/d5sc08253f, p.2]；[doi:10.1039/d5sc08253f, p.12]；[doi:10.1039/d5sc08253f, p.13]
- **method：** Explorer 以 end-state 间变化显著的 residue–residue Cα pairwise distances 作为 reduced coordinates，并用 progressive GAN 逐步把输出分辨率从 4 个中间态扩展到 32 个中间态。
  - 证据：[doi:10.1039/d5sc08253f, p.2]；[doi:10.1039/d5sc08253f, p.11]；[doi:10.1039/d5sc08253f, p.12]
- **method：** 生成器同时受 WGAN、Energy 和 Path 三个 critics 约束；其中 Energy critic 学习 MM 能量分箱标签，结构选择则借鉴 query-by-committee 风格，把 WGAN 与 Energy 判断冲突的候选送去做更昂贵的能量精修。
  - 证据：[doi:10.1039/d5sc08253f, p.4]；[doi:10.1039/d5sc08253f, p.11]；[doi:10.1039/d5sc08253f, p.13]
- **method：** Structure Builder 的训练结合 FAPE、sidechain angle、bond length、clash，且在 BAM 中可加入 RMSD 项；候选结构随后用 OpenMM 和 CHARMM36m/CHARMM36 做能量最小化与再训练。
  - 证据：[doi:10.1039/d5sc08253f, p.12]；[doi:10.1039/d5sc08253f, p.13]；[doi:10.1039/d5sc08253f, p.14]
- **results：** 在 AdK 上，DeepPath 生成的路径遵循与既往 MD 相同的弯曲 transition manifold，并保持 AMPbd 先于 LID 开启的序列。
  - 证据：[doi:10.1039/d5sc08253f, p.4]
- **results：** 在 SHP2 上，模型恢复了 N-SH2 围绕 PTP 的 hinge-like swing、C-SH2 rotation，以及 Y63-E508 的 partially open intermediate；Top-5 路径平均能量下降并在迭代中填补了早期 gap。
  - 证据：[doi:10.1039/d5sc08253f, p.4]；[doi:10.1039/d5sc08253f, p.5]；[doi:10.1039/d5sc08253f, p.6]
- **results：** 在 CdiB 上，DeepPath 复现了 H1 逐步外排并与 b4-b5 的 transient interaction，且 PSA/PCA 识别出 4 个能量相近的路径簇。
  - 证据：[doi:10.1039/d5sc08253f, p.6]；[doi:10.1039/d5sc08253f, p.7]
- **results：** 在 BAM 上，DeepPath 预测出与实验 hybrid-barrel 相符的 double-open intermediate，整体 Cα RMSD 为 4.35 Å、TM-score 为 0.91，并优于 SMwST 未能恢复该中间态的结果。
  - 证据：[doi:10.1039/d5sc08253f, p.8]；[doi:10.1039/d5sc08253f, p.9]；[doi:10.1039/d5sc08253f, p.10]

## 页码证据

- [doi:10.1039/d5sc08253f, p.10]
- [doi:10.1039/d5sc08253f, p.1]
- [doi:10.1039/d5sc08253f, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
