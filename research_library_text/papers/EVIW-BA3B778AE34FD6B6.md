# Accurate Generation of Conformational Ensembles for Intrinsically Disordered Proteins with IDPFold

- **论文 ID：** `EVIW-BA3B778AE34FD6B6`
- **期刊 / 来源：** Adv Sci (Weinh)
- **发表时间：** 2025 Oct 13
- **DOI：** [10.1002/advs.202511636](https://doi.org/10.1002/advs.202511636)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `扩散/生成`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 IDPFold：一个基于 conditional diffusion 的 MSA-free 构象集合生成器，结合 ESM2 序列特征与 IPA-Transformer 去噪模块，并用实验结构与 IDRome MD 轨迹两阶段训练，在 27 个 IDP 系统上声称优于既有深度学习方法、且与传统 MD/实验参考接近。

## 创新边界

`创新点主要是序列驱动的 IDP 构象集合生成与评估，不涉及新的湿实验，也不是蛋白候选序列设计或筛选。`。这不是全球首创性检索或独立复现结论。

## 研究问题

IDP 缺乏稳定结构、实验表征稀少且 MD 采样成本高，如何仅凭序列快速生成可信的构象集合，并同时保留全局紧致性与局部几何统计特征，是本文要解决的核心问题。

## 方法

- generative structure model与ensemble constraints/refinement。

## 数据与基准

- IDP MD/experimental observables。

## 比较基线

- MD/IDP generators。

## 结果证据

- 论文报告ensemble distributions改善；主要计算，明确实验observables为验证数据。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- thermodynamic weighting/跨IDP和实验数据有限。

## 仍未知

- 源码、权重和可复现脚本是否公开，正文未明确说明。
- 多链蛋白复合物或更复杂装配体上的泛化能力尚未评估。
- 对更长 IDP、明显折叠区以及时间自相关特征的稳健性仍不清楚。

## Pi 结构化证据摘录

- **baseline：** 论文将 CALVADOS2、idpGAN、idpSAM、STARLING、a99SB-disp、MD3*、bAIes、AF-cluster、AlphaFlow 和 BioEmu 作为主要对照。
  - 证据：[doi:10.1002/advs.202511636, p.7]
- **baseline：** 作者指出 CALVADOS2 往往只采样全无序态，而 idpGAN 更容易过采样并偏向错误的塌缩主构象。
  - 证据：[doi:10.1002/advs.202511636, p.4]；[doi:10.1002/advs.202511636, p.7]
- **baseline：** 作者还将 a99SB-ILDN、CHARMM36m 等传统力场纳入比较，显示它们在若干局部与全局指标上落后于 a99SB-disp 与 IDPFold。
  - 证据：[doi:10.1002/advs.202511636, p.6]；[doi:10.1002/advs.202511636, p.7]
- **data：** 预训练数据包含 15,051 个分辨率 ≤2.5 Å、冗余 ≤30% 的 X-ray 结构，以及 12,339 个 NMR 条目筛选后得到的 539 个系统、10,454 个结构。
  - 证据：[doi:10.1002/advs.202511636, p.9]
- **data：** IDP 轨迹数据来自 IDRome；作者选取长度超过 256 aa 的 3,880 个系统，经 back-mapping 与 100 步能量最小化后得到 77,600 个全原子构象。
  - 证据：[doi:10.1002/advs.202511636, p.9]
- **data：** 独立评测使用 27 个有完整实验表征且未进入训练集的 IDP 系统，并对这些系统做了 1 μs 的 ESFF1 + OPC3-B 全原子 MD 作为参照。
  - 证据：[doi:10.1002/advs.202511636, p.9]
- **declared_resources：** 模型规模为 17.8M parameters；训练约需 9 GPU days 预训练和 15 GPU days 微调，使用的是 NVIDIA A100。
  - 证据：[doi:10.1002/advs.202511636, p.10]
- **declared_resources：** 原始训练与评测数据来自 PDB 和 IDRome，处理后的数据可按请求共享。
  - 证据：[doi:10.1002/advs.202511636, p.11]
- **limitations：** IDPFold 对较长蛋白容易低估 Rg，且会减少高度伸展构象的比例。
  - 证据：[doi:10.1002/advs.202511636, p.3]；[doi:10.1002/advs.202511636, p.8]
- **limitations：** 在 α-Synuclein 和 drkN-SH3 等例子里，模型会偏向更螺旋化或更折叠的局部状态。
  - 证据：[doi:10.1002/advs.202511636, p.6]；[doi:10.1002/advs.202511636, p.8]
- **limitations：** 当前版本只在单链蛋白上训练和测试，尚未评估复合物或多链组装体。
  - 证据：[doi:10.1002/advs.202511636, p.8]
- **limitations：** 推理平均约 20 分钟，虽然快于传统 MD，但仍慢于部分深度学习方法，且作者承认当前模型无法捕捉时间自相关。
  - 证据：[doi:10.1002/advs.202511636, p.6]；[doi:10.1002/advs.202511636, p.8]
- **method：** IDPFold 采用 conditional diffusion 框架，从序列直接生成蛋白 backbone 构象集合；序列特征由 ESM2 提取，去噪网络由初始化模块和四个 denoising blocks 组成。
  - 证据：[doi:10.1002/advs.202511636, p.1]；[doi:10.1002/advs.202511636, p.2]；[doi:10.1002/advs.202511636, p.10]
- **method：** 扩散与生成过程使用 SE(3)-equivariant 的 backbone frame 参数化，并以 IPA + Transformer 同时建模局部几何和长程相互作用。
  - 证据：[doi:10.1002/advs.202511636, p.9]；[doi:10.1002/advs.202511636, p.10]
- **method：** 训练采取两阶段策略：先在晶体结构与 NMR 结构上预训练，再在 IDRome 的 MD 轨迹上微调；损失由 DSM、backbone 坐标 MSE 和 distance matrix 项共同组成。
  - 证据：[doi:10.1002/advs.202511636, p.9]；[doi:10.1002/advs.202511636, p.10]
- **method：** 评估维度同时覆盖全局 Rg、局部键长/键角/二面角、化学位移、3J 耦合、RDC，以及 validity 指标，用于检验生成构象是否符合实验与几何约束。
  - 证据：[doi:10.1002/advs.202511636, p.10]
- **results：** 在 CALVADOS2 的 58 个测试 IDP 上，IDPFold 的平均 Rg 误差为 −6%，并且多数系统的 Rg 分布与粗粒化轨迹接近。
  - 证据：[doi:10.1002/advs.202511636, p.3]
- **results：** 在 27 个实验系统上，IDPFold 的平均 εRg 为 −0.06，优于 idpGAN 的 −0.12；与模拟轨迹的 0.02 差异不显著（p=0.12），且明显优于 idpGAN（p=0.02）。
  - 证据：[doi:10.1002/advs.202511636, p.3]
- **results：** 与 idpGAN 相比，IDPFold 对 Histatin5、Human Calpastatin 和 β Synuclein 的主构象与占比更接近模拟结果。
  - 证据：[doi:10.1002/advs.202511636, p.4]；[doi:10.1002/advs.202511636, p.5]
- **results：** 在局部指标上，IDPFold 的化学位移、3J 和 RDC 表现达到或接近 a99SB-disp；表 1 给出的整体结果为 validity 0.95、εRg −0.06、Cα RMSD 0.65 ppm、Cβ RMSD 0.53 ppm、RDC 3.27 Hz。
  - 证据：[doi:10.1002/advs.202511636, p.6]；[doi:10.1002/advs.202511636, p.7]

## 页码证据

- [doi:10.1002/advs.202511636, p.1]
- [doi:10.1002/advs.202511636, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
