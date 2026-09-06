# IgPose: a generative data-augmented pipeline for robust immunoglobulin-antigen binding prediction

- **论文 ID：** `EVIW-C1FE2E1F2F53218E`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2026 Feb 15
- **DOI：** [10.1093/bioinformatics/btag076](https://doi.org/10.1093/bioinformatics/btag076)
- **范围标签：** `Pi 已解析` / `核心相关` / `有静态审计仓库` / `扩散/生成`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 IgPose，一个面向 Ig–Ag pose 识别与 DockQ 评分的生成式数据增强框架；它结合 SIDD 伪样本、ESM-2、EGNN 与自定义 GRU，并在分类、回归与候选筛选任务上声称优于既有物理打分和深度学习基线。

## 创新边界

`冻结证据支持作者提出了一个新的 Ig–Ag 评分/排序框架，但未提供可独立核验的外部 prior-art 证据，因此不把全球新颖性当作已证实结论。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在实验解析的 Ig–Ag 复合物稀缺、Ig 结构预测误差较大、界面构象高度多样的条件下，如何可靠地区分近天然与非天然结合姿态，并对候选复合物进行排序，是本文要解决的核心问题。

## 方法

- 从SAbDab复合物生成不同质量decoy，构建界面残基图；等变图网络与ESM-2特征、GRU残差融合，分别输出binding pose概率和DockQ估计。

## 数据与基准

- SIDD合成decoy、内部Ig-Ag测试集、CASP16；数据归档Zenodo 17431183。

## 比较基线

- 物理打分函数、既有深度界面评分/Ig docking方法及不同pooling/去除ESM-2/GRU消融。

## 结果证据

- 论文报告多个基准AUPRC最高提升约2倍，并在CASP16/内部集优于物理和深度基线；高质量pose与中等/可接受pose的细分仍较弱。

## 可用资源与代码关系

- [https://github.com/arontier/igpose](https://github.com/arontier/igpose)
  - 固定 commit：`caa585f030a60b28cdefe84e18850af8695e6780`
  - 静态复用层级：B_static_partial_shape
  - 许可证边界：license_file_present_spdx_unclassified_reuse_requires_review

## 已知限制

- synthetic decoy分布可能与真实错误pose不同；Ig结构和表位OOD仍难，高质量DockQ分层不足；没有实验结合验证。

## 仍未知

- Supplementary figures/algorithms 未在本次冻结文本中逐项核验。
- GitHub/Zenodo 仓库内容与可运行性未执行检查。
- CASP-16 之外的外部泛化范围仍不明确。
- 作者宣称的数据去泄漏流程未由本次分析独立验证。

## Pi 结构化证据摘录

- **baseline：** 作者将 IgPose 与 MIEnsembles、Prodigy、Rosetta、TRScore、GNN-DOVE、DeepRank-GNN-ESM、ProAffinity-GNN、AbEpiTope-1.0，以及自建的 FastEGNN 和 MACE 变体进行比较。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.5]；[doi:10.1093/bioinformatics/btag076, p.6]；[doi:10.1093/bioinformatics/btag076, p.7]
- **baseline：** 讨论部分指出，物理打分和通用深度学习 baseline 在跨数据集时常出现不稳定或接近失效的情况，而 AbEpiTope 在 CASP-16 上较强、在内部集上较弱。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.5]；[doi:10.1093/bioinformatics/btag076, p.9]
- **data：** 实验数据主要来自 SAbDab：作者整理了 4362 个 Ab 结构和 1137 个 Nb 结构，并按 30% 序列相似度与覆盖率聚类后得到 942 个簇、5499 个 Ig–Ag pair。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.3]
- **data：** 作者还纳入 STCRDab 的 80 个 TCR-pMHC 复合物，并按 MHC class 进行聚类。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.3]
- **data：** SIDD 包含 cognate decoys 与 non-cognate decoys：前者约 9.2×10^3 个结构，后者约 10^5 个负样本结构。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.3]
- **data：** 外部评测使用 CASP-16 的 8 个 Ig–Ag docking targets，共 4352 个预测结构；作者声称在训练截止前已核查未发生数据泄漏。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.3]；[doi:10.1093/bioinformatics/btag076, p.4]
- **declared_resources：** 论文声明代码已在 GitHub 与 Zenodo 发布，数据也可从 Zenodo 获取。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.10]
- **declared_resources：** 文中明确列出本研究使用的公开资源包括 SAbDab、STCRDab 和 CASP-16。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.10]
- **limitations：** 作者明确承认 IgPose 与 DockQ 的 Pearson 相关性仍然只是中等水平。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.9]
- **limitations：** 作者指出模型在 TCR-pMHC 子集上的表现低于抗体-抗原子集，说明该框架尚未充分覆盖不同受体类型的生物物理差异。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.9]
- **limitations：** 作者还担心 CASP-16 只有 8 个 cognate pairs，外部基准仍然偏小，且数据增强可能带来偏置或部分记忆化风险。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.9]
- **method：** 作者把 Ig–Ag 复合物表示为残基图，并用 ESM-2 作为节点特征、EGNN 进行等变消息传递、GRU 做门控残差更新，再通过 selective pooling 读出图表示。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.2]；[doi:10.1093/bioinformatics/btag076, p.4]；[doi:10.1093/bioinformatics/btag076, p.5]
- **method：** 训练前先做 interface-focused 3-hop 子图采样，并把子图规模限制到 600 个节点，以便聚焦结合邻域并控制计算量。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.5]
- **method：** 分类任务学习 native-like 与 non-native pose 的二分类，回归任务直接预测 DockQ；两者都使用任务特异损失，而回归还采用由分类器初始化后的 fine-tuning 策略。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.3]；[doi:10.1093/bioinformatics/btag076, p.5]
- **method：** 数据增强依赖 Chai-1 和 Boltz-2 生成的 SIDD 伪样本，且作者用 DockQ≥0.8 作为正负样本阈值来定义高质量姿态。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.2]；[doi:10.1093/bioinformatics/btag076, p.3]；[doi:10.1093/bioinformatics/btag076, p.4]
- **results：** 在分类任务上，IgPoseClassifier 在 SID-CA、SID-CB 与 CASP-16 上都取得最强或接近最强的 AUC/AP，作者报告其 CASP-16 的 AUC 为 0.914、AP 为 0.747。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.5]；[doi:10.1093/bioinformatics/btag076, p.6]
- **results：** 在回归任务上，IgPoseScore 在 SID-R 上达到最高相关性，作者报告 r=0.653；fine-tuned 版本进一步提升，而 IgPS-AbES ensemble 在 SID-R 与 CASP-16 上分别达到 0.686 和 0.415。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.7]；[doi:10.1093/bioinformatics/btag076, p.8]
- **results：** 在 Top-K 候选筛选中，IgPose 在 SID-R 上表现接近满分，且 ensemble 版本在 CASP-16 上也取得最优或接近最优结果。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.8]
- **results：** 消融结果显示，k-hop 采样、全原子图、selective pooling 与自定义 GRU 都对泛化和 AP/AUC 有正向贡献。
  - 证据：[doi:10.1093/bioinformatics/btag076, p.8]；[doi:10.1093/bioinformatics/btag076, p.9]

## 页码证据

- [doi:10.1093/bioinformatics/btag076, p.10]
- [doi:10.1093/bioinformatics/btag076, p.1]
- [doi:10.1093/bioinformatics/btag076, p.2]
- [doi:10.1093/bioinformatics/btag076, p.4]
- [doi:10.1093/bioinformatics/btag076, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
