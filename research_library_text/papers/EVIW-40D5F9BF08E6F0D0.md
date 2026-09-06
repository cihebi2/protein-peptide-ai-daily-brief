# Biophysics-based protein language models for protein engineering

- **论文 ID：** `EVIW-40D5F9BF08E6F0D0`
- **期刊 / 来源：** Nat Methods
- **发表时间：** 2025 Sep 11
- **DOI：** [10.1038/s41592-025-02776-2](https://doi.org/10.1038/s41592-025-02776-2)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 METL（mutational effect transfer learning），先用 Rosetta 生成的大规模模拟 biophysical attributes 预训练 transformer，再用实验 sequence–function 数据 fine-tune；并给出 METL-Local、METL-Global 与 function-specific 的 METL-Bind，最后还演示了低-N GFP 设计与湿实验验证。[doi:10.1038/s41592-025-02776-2, p.1] [doi:10.1038/s41592-025-02776-2, p.6] [doi:10.1038/s41592-025-02776-2, p.7]

## 创新边界

`新意主要在“用模拟 biophysics 做预训练信号、再接实验 fine-tuning”的框架本身，以及把这一框架用于蛋白性质预测和 GFP 候选设计；它不是从头生成蛋白的通用生成器，也没有仅凭正文就证明对所有 assay 都全面优于 evolutionary PLMs。[doi:10.1038/s41592-025-02776-2, p.1] [doi:10.1038/s41592-025-02776-2, p.3] [doi:10.1038/s41592-025-02776-2, p.8]`。这不是全球首创性检索或独立复现结论。

## 研究问题

该文要解决的问题，是如何在蛋白工程里把稀疏实验数据与已知的 biophysics 结合起来，以提升小样本学习、位置/突变外推和候选序列设计能力，而不是只依赖 evolutionary signals 或纯实验监督。[doi:10.1038/s41592-025-02776-2, p.1] [doi:10.1038/s41592-025-02776-2, p.3]

## 方法

- METL-Local/Global从模拟结构能量及属性学习表征，再迁移到热稳定、催化活性、荧光等任务；另探索功能特异模拟。

## 数据与基准

- 全局模型覆盖约3000万模拟结构，来源于148个基础蛋白；下游含多种实验测定数据，并有仅64个训练样本的GFP设计案例。

## 比较基线

- 进化序列PLM、MSA方法及其他蛋白变体效应模型。

## 结果证据

- 作者报告METL在小样本和位置外推任务有优势，并用64个样本训练后设计出有功能的GFP变体；但进化信号模型在许多常规测定上仍很强。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- METL-Global对148个基础蛋白过拟合：作者报告Rosetta总分预测的域内平均Spearman 0.85、域外0.16；模拟力场偏差会传入模型。

## 仍未知

- 补充材料中的更多 ablation 和细节未读，可能影响对某些次级结论的判断。
- 未做外部核验，无法独立确认代码、数据和实验复现的实际执行结果。
- global novelty 只基于冻结论文正文判断，没有独立 prior-art 证据。

## Pi 结构化证据摘录

- **baseline：** 零样本或 standalone baseline 包括 Rosetta total score、EVE 和 RaSP；其中 RaSP 通过对单点突变分数做加和来扩展到 multi-mutants。[doi:10.1038/s41592-025-02776-2, p.3] [doi:10.1038/s41592-025-02776-2, p.16]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.3]；[doi:10.1038/s41592-025-02776-2, p.16]
- **baseline：** 监督基线包括 Linear、Linear-EVE、ProteinNPT、ESM-2，以及 FCN、CNN 和随机初始化的 transformer；作者还把 Rosetta total score 作为额外特征构成 Linear-RTS。[doi:10.1038/s41592-025-02776-2, p.3] [doi:10.1038/s41592-025-02776-2, p.16] [doi:10.1038/s41592-025-02776-2, p.17]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.3]；[doi:10.1038/s41592-025-02776-2, p.16]；[doi:10.1038/s41592-025-02776-2, p.17]
- **baseline：** GFP 设计还设置了同约束条件下的 random variants baseline，以区分模型引导搜索与随机采样的差异。[doi:10.1038/s41592-025-02776-2, p.7] [doi:10.1038/s41592-025-02776-2, p.17]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.7]；[doi:10.1038/s41592-025-02776-2, p.17]
- **data：** 评估数据覆盖 11 个实验数据集，包括 GFP、DLG4、GRB2、GB1、Pab1、PTEN、TEM-1 和 Ube4b 等，原始数据来自 manuscript supplements、MaveDB 和 GEO。[doi:10.1038/s41592-025-02776-2, p.14] [doi:10.1038/s41592-025-02776-2, p.19]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.14]；[doi:10.1038/s41592-025-02776-2, p.19]
- **data：** 局部预训练结构来自 RCSB PDB 和 AlphaFold Protein Structure Database；全局预训练从 150 个候选中保留 148 个结构，排除了 1J3A 和 1JBE。[doi:10.1038/s41592-025-02776-2, p.13]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.13]
- **data：** GFP 湿实验使用 mKate2-GFP fusion 体系，20 个设计与 20 个 random baselines 一并测试，relative brightness 定义为 GFP/mKate2 比值并归一到 wild-type avGFP。[doi:10.1038/s41592-025-02776-2, p.7] [doi:10.1038/s41592-025-02776-2, p.18]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.7]；[doi:10.1038/s41592-025-02776-2, p.18]
- **declared_resources：** 作者公开提供了 METL 预训练模型、Rosetta simulation datasets、支持代码与数据，以及用于 pretraining/fine-tuning、Rosetta scoring 和 pretrained inference 的多个 GitHub 仓库；正文还声明代码采用 MIT license。[doi:10.1038/s41592-025-02776-2, p.8] [doi:10.1038/s41592-025-02776-2, p.18]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.8]；[doi:10.1038/s41592-025-02776-2, p.18]
- **declared_resources：** 他们还提供了 Hugging Face 模型与 demo、Google Colab notebooks，以及在 Open Science Pool 上批量生成 Rosetta 数据的 notebook。[doi:10.1038/s41592-025-02776-2, p.8]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.8]
- **declared_resources：** 计算资源和协作基础设施来自 University of Wisconsin-Madison Center for High Throughput Computing、OSG Consortium 和 Open Science Pool。[doi:10.1038/s41592-025-02776-2, p.19]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.19]
- **limitations：** METL-Global 对其 148 个预训练 base proteins 有明显 overfitting；in-distribution 的 Rosetta total score Spearman 约 0.85，而 out-of-distribution 只有 0.16。[doi:10.1038/s41592-025-02776-2, p.2]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.2]
- **limitations：** 作者也明确指出，existing evolutionary-based methods 对很多实验 assay 仍然很强，因此 METL 并非在所有任务上都占优。[doi:10.1038/s41592-025-02776-2, p.1] [doi:10.1038/s41592-025-02776-2, p.3] [doi:10.1038/s41592-025-02776-2, p.8]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.1]；[doi:10.1038/s41592-025-02776-2, p.3]；[doi:10.1038/s41592-025-02776-2, p.8]
- **limitations：** score extrapolation 是最难的设定之一，很多数据集上所有模型的 Spearman 都低于 0.3，说明高分区预测仍受限。[doi:10.1038/s41592-025-02776-2, p.4]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.4]
- **limitations：** Rosetta 不能自动建模 disulfide bond，作者也说模拟只是对真实物理的近似，因此某些 epistasis 和设计场景会失准。[doi:10.1038/s41592-025-02776-2, p.6] [doi:10.1038/s41592-025-02776-2, p.8]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.6]；[doi:10.1038/s41592-025-02776-2, p.8]
- **limitations：** 作者承认 GB1 曾用于方法开发，尽管做了 held-out 设计，结果仍可能对 GB1 略偏乐观；另外，他们后来还调整了 GFP 数据归一化流程。[doi:10.1038/s41592-025-02776-2, p.15]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.15]
- **limitations：** 在 GFP 实验中，没有一个设计超过 wild-type brightness，说明当前方法更像是提升可测功能或稳定性，而非直接超越 wild type。[doi:10.1038/s41592-025-02776-2, p.9]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.9]
- **method：** 先用 Rosetta 为局部序列空间或全局 fold space 生成大量变体，并计算 55 个 biophysical score 作为预训练监督信号；局部数据约 2,000 万变体/蛋白，全局数据约 3,000 万变体、来自 148 个 base proteins。[doi:10.1038/s41592-025-02776-2, p.13]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.13]
- **method：** 用带 1D 或 3D relative positional embedding 的 transformer encoder 预训练 METL-Local/METL-Global，再在实验序列-功能数据上训练 target model 的 backbone + head 结构。[doi:10.1038/s41592-025-02776-2, p.14]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.14]
- **method：** target model 采用 feature extraction 或 dual-phase fine-tuning；评估时使用随机 train/validation/test 切分，以及 position、mutation、regime 和 score extrapolation 的专门 split。[doi:10.1038/s41592-025-02776-2, p.15] [doi:10.1038/s41592-025-02776-2, p.16]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.15]；[doi:10.1038/s41592-025-02776-2, p.16]
- **method：** 在 GFP 设计中，作者用 64 个实验样本微调 METL-L-GFP，再通过 simulated annealing 搜索 5/10-mutant、Observed/Unobserved 两类约束下的 20 个候选，并送去湿实验验证。[doi:10.1038/s41592-025-02776-2, p.17] [doi:10.1038/s41592-025-02776-2, p.18]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.17]；[doi:10.1038/s41592-025-02776-2, p.18]
- **results：** 小训练集下，METL-Local、Linear-EVE 和 ProteinNPT 通常优于 METL-Global 和 ESM-2；其中 METL-Local 在 GFP 与 GB1 上表现尤其强。[doi:10.1038/s41592-025-02776-2, p.3]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.3]
- **results：** 在 position extrapolation 上，ProteinNPT 与 METL-Local 最强；regime extrapolation 中监督模型普遍可到 0.75 以上，而 score extrapolation 对所有模型都很难。[doi:10.1038/s41592-025-02776-2, p.3] [doi:10.1038/s41592-025-02776-2, p.4]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.3]；[doi:10.1038/s41592-025-02776-2, p.4]
- **results：** GB1 的数据效率分析显示，模拟数据与实验数据可互相替代一部分信息量，约 29 条 simulated examples 的增益相当于 1 条 experimental example，且在约 16k 到 128k simulated samples 后出现递减收益。[doi:10.1038/s41592-025-02776-2, p.4] [doi:10.1038/s41592-025-02776-2, p.5]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.4]；[doi:10.1038/s41592-025-02776-2, p.5]
- **results：** 预训练后的注意力图能贴近 GB1 的 residue distance matrix，且能识别已知 epistasis 位点和 G41L/V54G 的负 epistasis；不过对二硫键驱动的正 epistasis 有低估。[doi:10.1038/s41592-025-02776-2, p.5] [doi:10.1038/s41592-025-02776-2, p.6]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.5]；[doi:10.1038/s41592-025-02776-2, p.6]
- **results：** METL-Bind 在 GB1 binding 任务上，以更少训练数据优于标准 METL-Local，尤其在 GB1–IgG interface 附近误差更低。[doi:10.1038/s41592-025-02776-2, p.6] [doi:10.1038/s41592-025-02776-2, p.7]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.6]；[doi:10.1038/s41592-025-02776-2, p.7]
- **results：** 低-N GFP 设计中，20 个设计里有 16 个产生可测 fluorescence；Observed 约束下 5-mutant 与 10-mutant 都是 5/5 成功，Unobserved 约束下分别是 4/5 和 2/5。[doi:10.1038/s41592-025-02776-2, p.7]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.7]
- **results：** 随机 baseline 大多没有 fluorescence，说明 METL 设计并非纯随机命中，而是与模型学到的 GFP landscape 有关。[doi:10.1038/s41592-025-02776-2, p.7]
  - 证据：[doi:10.1038/s41592-025-02776-2, p.7]

## 页码证据

- [doi:10.1038/s41592-025-02776-2, p.18]
- [doi:10.1038/s41592-025-02776-2, p.1]
- [doi:10.1038/s41592-025-02776-2, p.2]
- [doi:10.1038/s41592-025-02776-2, p.6]
- [doi:10.1038/s41592-025-02776-2, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
