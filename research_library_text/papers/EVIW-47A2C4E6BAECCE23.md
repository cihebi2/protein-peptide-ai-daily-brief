# CoDNet: controlled diffusion network for structure-based drug design

- **论文 ID：** `EVIW-47A2C4E6BAECCE23`
- **期刊 / 来源：** Bioinform Adv
- **发表时间：** 2025 Feb 19
- **DOI：** [10.1093/bioadv/vbaf031](https://doi.org/10.1093/bioadv/vbaf031)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `扩散/生成`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出 CoDNet，把 ControlNet 式控制块接入 EDM，并结合 rEGNN、E3Norm 与零卷积条件注入机制，实现对 3D 坐标、atom types、charges 和 bonds 的联合去噪生成，目标是直接产出带完整键结构的 drug-like 分子。

## 创新边界

`作者声称这是 ControlNet 在 diffusion-based drug development 中的首次应用；但冻结材料未提供独立 prior-art 证据，只能按论文主张记录，不能视为已验证的全球首创。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何在结构化蛋白口袋条件下，联合利用3D分子几何与分子图，生成化学有效、连通且多样的候选小分子。

## 方法

- 以等变扩散生成原子类型和三维坐标，条件网络注入目标/设计约束并保持基础生成器表示。

## 数据与基准

- 主要在QM9及相关分子生成基准上评价有效性、原子价和分子性质。

## 比较基线

- EDM、GSchNet及其他三维分子生成/扩散模型。

## 结果证据

- 论文报告QM9有效率99.02%并超过比较模型；这主要证明通用小分子生成有效性，不充分证明目标蛋白结合。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- QM9较小且不代表药物化学空间；对具体蛋白靶点的亲和力、合成与活性验证不足。

## 仍未知

- 是否存在与论文完全一致的公开训练脚本和超参数配置，冻结页面未充分展开。
- 模型在真实受体口袋上的条件生成性能未知。
- 与其他 pocket-conditioned 方法在统一协议下的公平比较未知。
- 生成分子的可合成性、ADMET 与实验结合活性未知。

## Pi 结构化证据摘录

- **baseline：** 对照基线包括 GSchNet、EDM、EDM+OBabel、MiDi (uniform) 和 MiDi (adaptive)，CoDNet 在 validity 99.02 和 connected components 99.902 上被报告为最佳。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.7]
- **baseline：** 论文还把 Open Babel 后处理视为一种对照背景，强调 CoDNet 目标是在生成阶段直接产出稳定分子，而不是依赖后处理修复结构。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.1]；[doi:10.1093/bioadv/vbaf031, p.3]；[doi:10.1093/bioadv/vbaf031, p.7]
- **data：** 实验使用 QM9 作为基准，作者将其描述为约 134,000 个由 H、C、N、O、F 组成、最多 9 个非氢原子的有机分子集合。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.3]；[doi:10.1093/bioadv/vbaf031, p.4]
- **data：** 论文采用 Faber et al. 的预处理版本，去除了 3000 个 InChI consistency check 失败分子和 612 个 RDKit 不可读分子，最终得到 130,217 个分子。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.4]
- **data：** 数据被划分为 70% 训练集、20% 验证集和 10% 测试集。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.4]
- **declared_resources：** 论文给出的 Availability and implementation 链接是 https://github.com/CoDNet1/EDM_Custom。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.1]
- **declared_resources：** Supplementary data 被声明可在 Bioinformatics Advances online 获取。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.9]
- **declared_resources：** 数据资源来源于 QM9 及其 Faber 预处理版本，属于论文实验所依赖的核心公开基准。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.3]；[doi:10.1093/bioadv/vbaf031, p.4]
- **limitations：** 评测主要限于 QM9，而该基准是小分子集合，不是真实蛋白口袋或受体特异的 SBDD 场景，因此对实际 pocket-conditioned drug design 的外推有限。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.3]；[doi:10.1093/bioadv/vbaf031, p.4]；[doi:10.1093/bioadv/vbaf031, p.8]
- **limitations：** 冻结材料没有报告 wet-lab 验证或真实 docking 实验；讨论部分只是建议后续做 energy minimization、biological activity testing 和 docking。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.8]；[doi:10.1093/bioadv/vbaf031, p.9]
- **limitations：** 作者自己把这些结果描述为 preliminary，说明当前证据主要是生成质量指标，而不是药效、可合成性或真实靶点结合验证。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.8]；[doi:10.1093/bioadv/vbaf031, p.9]
- **method：** CoDNet 以 EDM 作为无条件生成骨干，再复制并冻结主干，在前后加入 zero convolution 形成控制分支，用于把条件信息注入分子生成过程。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.3]；[doi:10.1093/bioadv/vbaf031, p.6]
- **method：** 模型同时处理连续坐标与离散属性：坐标在 zero center-of-mass 子空间内加 Gaussian noise，atom types、charges 和 bonds 通过 categorical transition 注入噪声。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.4]
- **method：** CoDNet 使用自适应噪声 scheduler，以 cosine 形式调节不同变量的噪声强度，从而平衡连续与离散通道的腐蚀速率。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.5]
- **method：** 去噪器被设计为 SE(3)-equivariant graph transformer，包含 self-attention、rEGNN、E3Norm 和 position-based MLP，用来在保持等变性的同时恢复分子结构。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.5]；[doi:10.1093/bioadv/vbaf031, p.6]
- **method：** 训练目标对坐标使用 MSE，对离散变量使用 categorical cross-entropy，并通过总损失联合优化重建的分子图与3D构型。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.6]
- **results：** 在 QM9 上，CoDNet 报告的指标为 validity 99.02%、connected components 99.902%、novelty 73.00%、uniqueness 99.51%、valency 0.47、bond length 0.12、bond angles 2.33。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.6]
- **results：** 作者在图 3 和图 4 中声称，CoDNet 在 validity 与 connected components 上优于 GSchNet、EDM、EDM+OBabel、MiDi (uniform) 和 MiDi (adaptive)，并在 novelty/uniqueness 上保持竞争力。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.7]
- **results：** 图 5 仅展示数据库分子与 CoDNet 生成分子的可视化对照，作者据此推断生成样本具有较强的 drug-like 相似性。
  - 证据：[doi:10.1093/bioadv/vbaf031, p.8]；[doi:10.1093/bioadv/vbaf031, p.9]

## 页码证据

- [doi:10.1093/bioadv/vbaf031, p.1]
- [doi:10.1093/bioadv/vbaf031, p.7]
- [doi:10.1093/bioadv/vbaf031, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
