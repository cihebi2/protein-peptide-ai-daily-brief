# Deep learning workflow for the inverse design of molecules with specific optoelectronic properties

- **论文 ID：** `EVIW-B9DC20CAB83C85CC`
- **期刊 / 来源：** Sci Rep
- **发表时间：** 2023 Nov 16
- **DOI：** [10.1038/s41598-023-45385-9](https://doi.org/10.1038/s41598-023-45385-9)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `扩散/生成` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出一个迭代式逆向分子设计流程，把 DFTB 生成标签、HydraGNN 预测 surrogate、以及预训练 masked language model 串联起来，并用数据筛选与逐轮重训来扩展训练集、修正泛化误差并生成低 HLG 分子。

## 创新边界

`创新主要在迭代式工作流整合、数据筛选和重训策略，而不是提出全新的分子生成模型架构或新的量子化学理论。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何在巨大的有机化学空间中，借助可迭代的深度学习与生成模型，持续发现具有更低 HOMO-LUMO gap 的新分子，同时保持 surrogate 对不断扩展的化学空间仍然可靠。

## 方法

- 分子表示、property network与latent/generative optimization。

## 数据与基准

- optoelectronic molecule/property datasets。

## 比较基线

- random/forward-screening/generative baselines。

## 结果证据

- 论文报告property-conditioned candidates；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 预测器适用域、合成与实测性质未知。

## 仍未知

- 是否具备湿实验合成与性质验证未报告。
- 代码只能按合理请求获取，外部可复现性不明。
- 与更强公开基线在统一协议下的系统比较有限。

## Pi 结构化证据摘录

- **baseline：** 作者将先前单轮工作作为 baseline：当时已能生成最低 0.75 eV 的分子，但新分子上的 surrogate MAE 从 0.11 eV 升到 0.45 eV，暴露出泛化不足。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.2]
- **baseline：** 本文内部又用 Surrogate0 对 Surrogate5 做对照，明确显示扩展训练集并迭代重训能显著降低误差并覆盖更大的化学空间。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.6]
- **data：** 起始数据集 GDB-9 含 95,735 个分子；六轮迭代后训练集扩展到 203,901 个分子，累计分析的分子规模达到 550,380 个。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.5]；[doi:10.1038/s41598-023-45385-9, p.8]
- **data：** 每轮大约生成 100,000 个候选分子，再按 HLG 和筛选规则决定是否并入下一轮；进入训练集的比例从首轮约 47% 降到后期约 12%。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.5]；[doi:10.1038/s41598-023-45385-9, p.6]
- **data：** GDB-9 的 DFTB HLG 分布范围约为 0.98 到 19.8 eV，并且大多数分子集中在 5 eV 以下。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.7]
- **declared_resources：** 计算资源包括 Oak Ridge Leadership Computing Facility 的 Summit；HydraGNN 在 6 张 Nvidia 16 GB V100 GPU 上用 DDP 训练，MLM 训练则使用了 1000 个 Summit nodes。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.4]
- **declared_resources：** 论文声明数据集 ORNL_AISD_DL−HLgap 共享于 OLCF Data Constellation Facility，代码则仅在合理请求下由通讯作者提供，而未给出公开仓库链接。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.11]
- **limitations：** 作者把 DFTB3/3ob 作为近似 ground truth，并明确表示若资源允许可替换为更高层级的 first principles 或 ab initio 方法，因此标签精度受限于近似量子化学。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.3]
- **limitations：** 部分低 HLG 候选包含 3/4 元环或更大张力环，作者也认为这类结构可能更不稳定，所以仍需要额外的化学合理性筛选。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.9]
- **limitations：** 作者指出仅凭 H/C ratio、aromaticity、DBE 或分子大小等统计量难以精确指导目标分子搜索，说明可解释性和可控性仍有限。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.8]
- **method：** 作者以 GDB-9 为起点，用 MMFF94s 生成三维构型，再用 DFTB3/3ob 优化并计算 HOMO、LUMO 与 HLG，把这些 DFTB 结果作为 ground truth 来训练 surrogate。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.3]；[doi:10.1038/s41598-023-45385-9, p.4]
- **method：** Surrogate 采用 HydraGNN 的 GCNN 结构，包含 6 个 PNA layers 和 3 层全连接层，并以 AdamW、200 epochs、90/10/10 划分和 6 张 V100 GPU 的 DDP 方式训练。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.4]
- **method：** 生成器使用基于 SMILES 的 masked language model，先在 Enamine REAL 上预训练并扩充到约 36 billion molecules，再结合 WordPiece 与 DeepSpeed fused LAMB 进行大规模训练。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.4]
- **method：** 每轮迭代都应用三条数据规则：保留高预测误差分子、去除重复分子、并把少于 20 个非氢原子的分子并入训练集，较大的分子则保留为测试集。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.5]
- **results：** 仅用 GDB-9 训练的 Surrogate0 在新生成分子上的 MAE 随迭代恶化，GEN-5 时升到 0.91 eV；而重训后的 Surrogate5 对各代数据基本稳定在约 0.12 eV，GEN-6 也只有 0.13 eV。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.6]
- **results：** 平均 HLG 从 GDB-9 的 5.91 eV 逐步降到 GEN-6 的 2.74 eV，说明迭代筛选确实把分子分布推向更低 gap 区域。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.8]
- **results：** 低于 GDB-9 最低值 0.98 eV 的分子数从 GEN-1 的 4 个增加到 GEN-6 的 240 个，而且 GEN-3 还出现了 0.67 eV 的最低值。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.9]；[doi:10.1038/s41598-023-45385-9, p.10]
- **results：** 生成的低 HLG 分子通常包含共轭 π 键、羰基、胺以及小张力环或反芳香环，但作者也指出 HLG 与 H/C ratio、aromaticity、DBE、atom count 等简单描述符之间没有强关系。
  - 证据：[doi:10.1038/s41598-023-45385-9, p.8]；[doi:10.1038/s41598-023-45385-9, p.10]

## 页码证据

- [doi:10.1038/s41598-023-45385-9, p.1]
- [doi:10.1038/s41598-023-45385-9, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
