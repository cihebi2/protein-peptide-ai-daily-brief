# HFGuidedDesign: de novo design of cyclic peptide binders via structure-guided discrete diffusion

- **论文 ID：** `EVIW-3A1ACC8879ECFFC5`
- **期刊 / 来源：** Chem Sci
- **发表时间：** 2026 Jun 30
- **DOI：** [10.1039/d6sc02631a](https://doi.org/10.1039/d6sc02631a)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `扩散/生成` / `结构预测`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 HFGuidedDesign：把 sequence-level discrete diffusion 与 HighFold 的实时结构反馈结合，在反向采样中动态引导 cyclic peptide 序列生成；并在 12 个靶标及 MDM2/GABARAP 的实验中展示了可行性。

## 创新边界

`创新点主要在于把结构预测器嵌入扩散反向过程做实时 guidance，而不是只做事后筛选；本次冻结证据未提供独立 prior-art 核验，因此只能确认论文内的相对新颖性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在 cyclic peptide–protein complex 结构数据稀缺、且传统“先骨架后序列”两阶段流程误差容易累积的情况下，如何仅凭目标蛋白序列直接生成兼具结构可行性、界面稳定性和实验可验证结合活性的 cyclic peptide binders。

## 方法

- cyclic peptide discrete diffusion、folding/complex guidance与筛选。

## 数据与基准

- cyclic peptide-protein complexes/candidates。

## 比较基线

- cyclic peptide generators/docking。

## 结果证据

- 论文报告设计/可能实验；只明确assay写实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 环化/合成/膜通透与目标覆盖。

## 仍未知

- MDM2 的可检测结合成功率在 p.10 与 p.13 的表述口径不完全一致，统计方式需要作者进一步澄清。
- GitHub 仓库与数据集仅按正文声明，未在本次纸面审查中核验其可运行性、许可证与实际内容。
- HighFold/HighFold3/Boltz-2 的具体版本、训练细节和与本研究的接口实现未完整展开。

## Pi 结构化证据摘录

- **baseline：** RFpeptides 先生成 cyclic peptide backbone，再用 ProteinMPNN 做序列设计；AfCycDesign 基于 AlphaFold2 反向优化并再经 ProteinMPNN 精修。
  - 证据：[doi:10.1039/d6sc02631a, p.8]
- **baseline：** 三种方法在同一 12 靶标集合上比较，RFpeptides 约 12000 条、AfCycDesign 每靶标 1000 条、HFGuidedDesign 每靶标 20 条，且统一取 top-20 进行对照。
  - 证据：[doi:10.1039/d6sc02631a, p.8]
- **data：** 微调集由 PPIKB 和作者用于训练 PepMLM 的数据合并而来，过滤掉非标准氨基酸、长度超限与重复样本后，保留 9511 个高质量复合物。
  - 证据：[doi:10.1039/d6sc02631a, p.2]
- **data：** 评测集从 HighFold test set 与 RFpeptides 目标集中筛选出 12 个靶标，覆盖 Trypsin、MDM2、KEAP1、GABARAP 等，配体长度约为 6–16 个氨基酸。
  - 证据：[doi:10.1039/d6sc02631a, p.6]；[doi:10.1039/d6sc02631a, p.7]
- **data：** 面向未见靶标，作者额外测试了 CD28 与 SPIRE1，每个靶标生成 20 条候选并进入多轮排序与后续计算验证。
  - 证据：[doi:10.1039/d6sc02631a, p.12]；[doi:10.1039/d6sc02631a, p.13]
- **data：** 论文还报告了生成肽与训练配体的相似度统计，12 个 benchmark target 的平均 identity 约为 31.00%，范围为 21.60%–46.44%。
  - 证据：[doi:10.1039/d6sc02631a, p.13]
- **declared_resources：** 作者在 Data availability 中声明，代码和数据已公开在 GitHub 仓库 https://github.com/hongliangduan/HFGuidedDesign。
  - 证据：[doi:10.1039/d6sc02631a, p.14]
- **declared_resources：** 生成、评估与表征流程中明确使用了 HighFold、HighFold3、Boltz-2、Rosetta Interface Analyzer、Amber/AmberTools 和 Biacore S200 等外部工具/仪器。
  - 证据：[doi:10.1039/d6sc02631a, p.5]；[doi:10.1039/d6sc02631a, p.6]；[doi:10.1039/d6sc02631a, p.9]；[doi:10.1039/d6sc02631a, p.10]；[doi:10.1039/d6sc02631a, p.11]
- **limitations：** 作者明确指出方法强依赖 HighFold 的结构预测质量，而其效果仍受 cyclic peptide–protein complex 数据规模与多样性限制。
  - 证据：[doi:10.1039/d6sc02631a, p.13]；[doi:10.1039/d6sc02631a, p.14]
- **limitations：** 当前框架没有显式接受 hotspot residues 或预定义 pocket residues，靶位点偏好主要是通过结构引导间接实现。
  - 证据：[doi:10.1039/d6sc02631a, p.14]
- **limitations：** 实时结构评估会带来显著计算开销，尤其在大规模设计或更长 peptide 场景下更明显。
  - 证据：[doi:10.1039/d6sc02631a, p.14]
- **method：** 模型采用两阶段训练：先在 UniRef50 中长度不超过 50、且仅含 20 种标准氨基酸的约 194 万条肽单体上预训练，再在 peptide–protein complex 数据上微调。
  - 证据：[doi:10.1039/d6sc02631a, p.2]
- **method：** 反向生成主体是离散去噪扩散模型 D3PM，并用 Transformer、cross-attention 与 FiLM 联合建模当前噪声序列、目标蛋白序列和扩散步嵌入。
  - 证据：[doi:10.1039/d6sc02631a, p.2]；[doi:10.1039/d6sc02631a, p.3]；[doi:10.1039/d6sc02631a, p.4]
- **method：** 结构引导模块在采样中调用 HighFold，基于 iPTM、pLDDTpeptide 和 iPAE 组成复合分数，并用有限差分与 UCB1 选择单点突变来修正反向扩散分布。
  - 证据：[doi:10.1039/d6sc02631a, p.4]；[doi:10.1039/d6sc02631a, p.5]
- **method：** 实验部分使用 Fmoc-SPPS、RP-HPLC、LC-MS 和 Biacore S200 SPR 对候选 cyclic peptide 进行合成、纯化和亲和力测定。
  - 证据：[doi:10.1039/d6sc02631a, p.5]
- **method：** 命中分子的后续表征还包括 Amber/AmberTools 分子动力学、MM/GBSA 以及 Rosetta Interface Analyzer，生产模拟长度为 100 ns。
  - 证据：[doi:10.1039/d6sc02631a, p.6]
- **results：** 在 12 个靶标上，生成复合物的平均 complex pLDDT 为 94.9，peptide pLDDT 为 93.1，iPTM 为 0.92，iPAE 为 0.13，dG_separated/dSASA ×100 为 −1.88。
  - 证据：[doi:10.1039/d6sc02631a, p.7]；[doi:10.1039/d6sc02631a, p.13]
- **results：** 序列层面，生成肽的平均 diversity（Levenshtein）为 76.22%，对 native ligand 的平均 identity 约为 20.78%。
  - 证据：[doi:10.1039/d6sc02631a, p.8]
- **results：** 相较 RFpeptides 与 AfCycDesign，HFGuidedDesign 在 peptide pLDDT、i_pLDDT、iPTM 和 iPAE 等指标上均更优，而且这一优势在 HighFold 与 Boltz-2 两种评估器下都保持一致。
  - 证据：[doi:10.1039/d6sc02631a, p.8]；[doi:10.1039/d6sc02631a, p.9]
- **results：** MDM2 实验中，论文报告三条 head-to-tail 候选里有一条合成失败，其余两条在 SPR 中呈 micromolar 结合；结论部分又将 MDM2 的可检测结合成功率概括为 75%。
  - 证据：[doi:10.1039/d6sc02631a, p.10]；[doi:10.1039/d6sc02631a, p.13]
- **results：** GABARAP 实验中，三条候选里有两条显示可靠的浓度依赖结合，最佳分子对 GABARAP 的 KD 为 1.389 mM。
  - 证据：[doi:10.1039/d6sc02631a, p.11]；[doi:10.1039/d6sc02631a, p.13]
- **results：** 对未见靶标 CD28 与 SPIRE1，MM/GBSA 预测的结合自由能分别落在 −48.82 至 −54.47 kcal mol−1 和 −37.25 至 −58.49 kcal mol−1。
  - 证据：[doi:10.1039/d6sc02631a, p.13]

## 页码证据

- [doi:10.1039/d6sc02631a, p.1]
- [doi:10.1039/d6sc02631a, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
