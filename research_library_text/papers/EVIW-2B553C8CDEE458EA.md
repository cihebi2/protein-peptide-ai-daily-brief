# Generalizable and scalable protein stability prediction with rewired protein generative models

- **论文 ID：** `EVIW-2B553C8CDEE458EA`
- **期刊 / 来源：** Nature Communications（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1038/s41467-025-67609-4](https://doi.org/10.1038/s41467-025-67609-4)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `扩散/生成`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 SPURS：通过 Adapter 将 ESM2 与 ProteinMPNN 重编排为结构增强的序列表示，再用大规模 thermostability 数据微调，实现单次前向预测全蛋白所有单点突变的 ∆∆G，并扩展到双突变 epistasis 以及若干下游蛋白组学应用。

## 创新边界

`创新主要在模型重编排与大规模监督微调，不是新的湿实验或新的候选蛋白生成任务。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何把序列生成模型与结构逆折叠模型结合起来，提升蛋白单点与高阶突变的稳定性变化（∆∆G）预测泛化，并把稳定性信号扩展到功能位点、低-N fitness 和致病性分析。

## 方法

- 融合ESM-2序列表示与ProteinMPNN结构条件表示，在大规模热稳定性数据上监督训练，并将稳定性得分迁移到低样本适应度和功能位点任务。

## 数据与基准

- 使用megascale thermostability及多个外部稳定性/突变基准，并评估ProteinGym、Domainome和临床变异场景。

## 比较基线

- ESM-2、ProteinMPNN及ThermoMPNN、GeoStab等稳定性预测方法。

## 结果证据

- 论文报告SPURS在跨蛋白稳定性预测、稳定突变识别及若干零/低样本下游任务上优于比较模型；全部核心稳定性结论为计算评估。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 融合模型依赖结构输入与大规模已测稳定性数据；罕见突变、结构误差和真实工程命中率仍需验证。

## 仍未知

- 正文对 Megascale 规模与独立测试集数量存在口径差异，后续应以补充表和原始数据再核对。
- AlphaFold2 结构用于无实验结构场景，但对 intrinsically disordered regions 与某些界面解释仍有不确定性。
- 冻结证据无法独立验证 GitHub 仓库是否可直接复现全部实验流程。

## Pi 结构化证据摘录

- **baseline：** 稳定性主 benchmark 的对照包括 ThermoMPNN、ESM/ProteinMPNN 的 zero-shot 版本、FT-ESM、FT-ProteinMPNN，以及简单 concatenation 融合。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.6]；[doi:10.1038/s41467-025-67609-4, p.31]
- **baseline：** 跨独立稳定性数据集还比较了 FoldX、Rosetta、PROSTATA、RASP、Stability Oracle、ThermoNet 等方法。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.6]
- **baseline：** 高阶突变比较使用 DDGun、MutateEverything 和把单点模型做 additive 外推的基线。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.7]；[doi:10.1038/s41467-025-67609-4, p.31]
- **baseline：** 低-N fitness 部分将 SPURS-augmented 模型与 Augmented-{ESM1b, EVMutation, Evotuned UniRep, DeepSequence} 对比。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.9]；[doi:10.1038/s41467-025-67609-4, p.31]
- **baseline：** 致病性与功能位点分析对照了 AlphaMissense、EVE、rSASA 以及依赖 docking 或 supervised labels 的既有思路。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.7]；[doi:10.1038/s41467-025-67609-4, p.8]；[doi:10.1038/s41467-025-67609-4, p.11]
- **data：** 训练主数据来自 Megascale；正文在不同位置分别将其描述为覆盖 479 个 domain、超过 770,000 条 ∆∆G 测量，或单突变子集 272,721 个变体、298 个 protein。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.3]；[doi:10.1038/s41467-025-67609-4, p.6]
- **data：** 高阶突变扩展另使用 122,278 个双突变变体进行训练，验证集和测试集均来自 Megascale 的固定划分。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.16]；[doi:10.1038/s41467-025-67609-4, p.19]
- **data：** 稳定性泛化评估覆盖多个独立集合，方法部分列出 Fireprot(HF)、Ssym-direct、Ssym-inverse、S669、S783、S2648、S4611、S8754、S4346 和 S571。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.19]
- **data：** Domainome 数据集包含 563,534 个变体、522 个 protein，其中 239 个 protein 具备 residue-level functional annotations。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.7]；[doi:10.1038/s41467-025-67609-4, p.19]
- **data：** 人类 proteome 分析覆盖 19,652 个 protein 的 178,987,201 个 missense variants，其中 696,736 个 ClinVar 变体可映射到 16,997 个 protein，另加入 15,820 个 gnomAD 变体。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.8]；[doi:10.1038/s41467-025-67609-4, p.18]；[doi:10.1038/s41467-025-67609-4, p.19]
- **declared_resources：** 模型检查点明确使用了 esm2_t33_650M_UR50D、v_48_020 的 ProteinMPNN，以及 esm1v_t33_650M_UR90S_1。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.17]
- **declared_resources：** 训练与评估数据来自 Megascale、ThermoMPNN 预处理划分、GeoStab、Domainome、ClinVar 和 COSMIC 等公开来源。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.19]；[doi:10.1038/s41467-025-67609-4, p.20]
- **declared_resources：** 实现基于 Python / PyTorch v1.12.0，并在 NVIDIA A40 GPU 上训练，另使用 Delta GPU Supercomputer 与 Microsoft Azure 资源。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.13]；[doi:10.1038/s41467-025-67609-4, p.30]
- **declared_resources：** 论文给出了 GitHub 源码仓库 https://github.com/luo-group/SPURS，并在引用中附带 Zenodo 代码归档。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.20]；[doi:10.1038/s41467-025-67609-4, p.30]
- **limitations：** 模型主要在 ∆∆G 上训练，因此迁移到 ∆Tm 时作者也承认更适合相对排序而非绝对值预测，绝对稳定性指标仍需 dataset-specific fine-tuning。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.13]
- **limitations：** 在人类 proteome 的 IDR 分析中，作者明确提醒 AlphaFold2 预测结构可能并不可靠，这会影响解释。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.11]；[doi:10.1038/s41467-025-67609-4, p.18]
- **limitations：** SPURS-augmented fitness 模型被作者定位为补充性 prior，而不是要取代现有低-N SOTA 的独立预测器。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.10]
- **limitations：** 篇中部分数字口径在不同章节并不完全一致，尤其是 Megascale 与独立测试集的计数，读者需要结合原始数据表再核对。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.3]；[doi:10.1038/s41467-025-67609-4, p.6]；[doi:10.1038/s41467-025-67609-4, p.19]
- **method：** SPURS 以 ESM2 作为序列编码器、ProteinMPNN 作为结构编码器，并通过 Adapter 把结构特征注入序列表示，形成 structure-enhanced evolutionary features。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.4]；[doi:10.1038/s41467-025-67609-4, p.14]；[doi:10.1038/s41467-025-67609-4, p.15]
- **method：** 模型以 wild-type 序列和结构为条件，在一次前向传播中同时输出所有单点突变的 ∆∆G，把逐突变推断压缩为 O(1) 级别。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.5]；[doi:10.1038/s41467-025-67609-4, p.15]
- **method：** 对高阶突变，SPURS 将单点效应求和并加入由独立 epistasis MLP 估计的非加性项，训练时使用 Megascale 的双突变数据。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.6]；[doi:10.1038/s41467-025-67609-4, p.16]
- **method：** 功能位点识别中，作者把 SPURS 的 −∆∆G 与 ESM1v 的 delta log-likelihood 通过 sigmoid 拟合残差构造 per-site function score。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.8]；[doi:10.1038/s41467-025-67609-4, p.17]
- **method：** 低-N fitness 预测把 SPURS 的 ∆∆G 作为额外特征，和 one-hot 序列及 evolutionary density score 一起输入 Ridge regression。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.9]；[doi:10.1038/s41467-025-67609-4, p.18]
- **method：** 致病性分析将 SPURS 的 ∆∆G 与 rSASA 线性插值，并结合 ClinVar、OMIM、gnomAD 和 COSMIC 注释做分层比较。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.10]；[doi:10.1038/s41467-025-67609-4, p.11]；[doi:10.1038/s41467-025-67609-4, p.18]；[doi:10.1038/s41467-025-67609-4, p.19]
- **results：** 在 Megascale test set 上，SPURS 的 median Spearman 为 0.83，优于 ThermoMPNN 的 0.77，并在 28 个 protein 中的 24 个上占优。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.6]
- **results：** 在外部稳定性 benchmark 上，SPURS 对 7/8 个测试集给出更高或相当的相关性，并把 Domainome 的 correlation 提升到 0.54，对比 ThermoMPNN 的 0.49。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.6]
- **results：** 对 double mutants，SPURS 优于 DDGun 和 MutateEverything，也明显优于把单突变分数直接相加的 additive baselines。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.7]；[doi:10.1038/s41467-025-67609-4, p.31]
- **results：** 稳定化突变优先排序上，SPURS 在 1,178 个 stabilizing 与 27,139 个 destabilizing 变体的检索中，precision 和 recall 都优于 ThermoMPNN。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.7]
- **results：** 功能位点识别上，239 个 domain 的平均 AUROC 为 0.69，且功能位点与非功能位点的分布差异极显著。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.8]
- **results：** 低-N fitness 预测中，SPURS-augmented DeepSequence 在 141 个 DMS 数据集里的 115 个上优于原始 Augmented DeepSequence，总体 Spearman 提升约 15%。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.9]；[doi:10.1038/s41467-025-67609-4, p.10]
- **results：** 致病性分析中，pathogenic variants 比 benign variants 更易 destabilizing；结合 ∆∆G 与 rSASA 的简单分类器最高 AUROC 达到 0.84。
  - 证据：[doi:10.1038/s41467-025-67609-4, p.10]；[doi:10.1038/s41467-025-67609-4, p.11]

## 页码证据

- [doi:10.1038/s41467-025-67609-4, p.12]
- [doi:10.1038/s41467-025-67609-4, p.2]
- [doi:10.1038/s41467-025-67609-4, p.4]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
