# AntiFold: improved structure-based antibody design using inverse folding

- **论文 ID：** `EVIW-FC4F98D1EFC1712B`
- **期刊 / 来源：** Bioinform Adv
- **发表时间：** 2025 Mar 21
- **DOI：** [10.1093/bioadv/vbae202](https://doi.org/10.1093/bioadv/vbae202)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白质设计` / `结构预测`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者将通用蛋白 inverse folding 模型 ESM-IF1 微调为抗体特异模型 AntiFold，利用已解析与预测的抗体结构提升 CDR sequence recovery、refolding 后的结构一致性，并在零样本条件下改进 antibody-antigen binding affinity 预测。

## 创新边界

`主要新意在于抗体特异的迁移微调、masking 策略与评测组合，而不是全新的通用逆折叠架构；其创新边界更接近 task-specific adaptation。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在保持抗体 variable domain backbone 结构不变的前提下，如何通过 inverse folding 生成更合适的 CDR/序列变体，并用结构约束分数辅助 antibody optimization 与 affinity maturation。

## 方法

- 以抗体-抗原结构条件生成残基概率，针对CDR进行采样，并与通用逆折叠及抗体专用模型比较。

## 数据与基准

- 主要使用SAbDab 2074个已解析复合物，并按拼接CDR序列90% identity划分训练、验证和测试。

## 比较基线

- ProteinMPNN、ESM-IF1、AbMPNN；IgMPNN因权重和训练数据不可得未直接比较。

## 结果证据

- 论文报告CDR序列恢复优于ProteinMPNN、ESM-IF1和AbMPNN，设计序列对原结构保持较高预测相似度；没有系统湿实验亲和力验证。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 序列恢复偏好天然序列，不等同于功能优化；依赖输入结构和训练抗体分布。

## 仍未知

- 补充材料中的完整超参数、消融与统计检验细节未在主文中展开。
- 主文没有给出 AntiFold 建议序列的独立湿实验验证。
- 对非抗体蛋白或超出 antibody variable domain 的泛化能力未报告。
- antigen context 未显著改进的原因没有进一步分析。

## Pi 结构化证据摘录

- **baseline：** 作者将 AntiFold 与 ESM-IF1、AbMPNN、ProteinMPNN 以及序列模型 ESM-2 进行对比，覆盖 sequence recovery、refolding 与 affinity prediction 三类任务。
  - 证据：[doi:10.1093/bioadv/vbae202, p.3]
- **baseline：** 重折叠部分还使用 ABodyBuilder2 对原始序列建模得到的 native 对照作为基准，以衡量设计序列的结构偏移。
  - 证据：[doi:10.1093/bioadv/vbae202, p.3]
- **baseline：** 作者明确未直接比较 IgMPNN，理由是其模型权重和训练数据不可获得。
  - 证据：[doi:10.1093/bioadv/vbae202, p.2]
- **data：** 训练、验证与测试使用 2074 个来自 SAbDab 的 solved complexes，以及 147,458 个来自 OAS paired database、并由 ABodyBuilder2 建模的结构，按 90% concatenated CDR sequence identity cutoff 划分为 80/10/10。
  - 证据：[doi:10.1093/bioadv/vbae202, p.2]
- **data：** 重折叠评估选取了 56 个由 X-ray crystallography 解析、分辨率低于 2.5 Å 的抗体结构，用于比较设计序列与实验骨架的一致性。
  - 证据：[doi:10.1093/bioadv/vbae202, p.3]
- **data：** 亲和力评估使用 Warszawski et al. 的 anti-lysozyme deep mutational scan，共 2209 个 Fab D44.1 变体；另使用 Hie et al. 的 124 个、覆盖 7 个抗体的 affinity-maturation 变体集合。
  - 证据：[doi:10.1093/bioadv/vbae202, p.3]
- **declared_resources：** 作者将 AntiFold 作为可免费访问的 web server 与 pip-installable package 发布，并声明采用 BSD 3-Clause license。
  - 证据：[doi:10.1093/bioadv/vbae202, p.1]；[doi:10.1093/bioadv/vbae202, p.3]
- **declared_resources：** 主文明确给出代码仓库 GitHub 地址，便于复现与本地部署。
  - 证据：[doi:10.1093/bioadv/vbae202, p.1]；[doi:10.1093/bioadv/vbae202, p.3]
- **limitations：** 主文中的验证主要依赖已有结构测试集、公开 DMS 与既有 affinity-maturation 数据，未见独立湿实验验证 AntiFold 设计序列的真实功能。
  - 证据：[doi:10.1093/bioadv/vbae202, p.2]；[doi:10.1093/bioadv/vbae202, p.3]；[doi:10.1093/bioadv/vbae202, p.4]
- **limitations：** 论文的证据范围集中在 antibody variable domains 与 CDR 级别任务，因此对非抗体蛋白、完整抗体其他部分或超出 backbone-constrained design 场景的泛化仍未被证明。
  - 证据：[doi:10.1093/bioadv/vbae202, p.1]；[doi:10.1093/bioadv/vbae202, p.2]；[doi:10.1093/bioadv/vbae202, p.3]
- **limitations：** 加入 antigen 作为额外上下文并未带来统计显著提升，说明当前 affinity 预测增益并非来自显式 antigen conditioning。
  - 证据：[doi:10.1093/bioadv/vbae202, p.3]
- **method：** AntiFold 以 ESM-IF1 为底座，进一步在抗体 variable domain 结构上微调，用于从结构预测序列，并接受 solved 或 predicted antibody structures 作为输入。
  - 证据：[doi:10.1093/bioadv/vbae202, p.1]；[doi:10.1093/bioadv/vbae202, p.2]
- **method：** 训练阶段结合 span masking、随机残基 masking、对 CDR 残基加权的 masking、layer-wise learning-rate decay，以及来自 OAS 的 predicted structures，这些策略被纳入最终模型。
  - 证据：[doi:10.1093/bioadv/vbae202, p.2]
- **method：** 推理时用户可以指定 IMGT region 与 temperature，模型输出每个残基的 residue probabilities、所选区域的 designed sequences，以及整体的 mutation tolerance/perplexity。
  - 证据：[doi:10.1093/bioadv/vbae202, p.1]；[doi:10.1093/bioadv/vbae202, p.2]
- **results：** 在实验结构测试集上，AntiFold 的 CDRH3 amino acid recovery 达到 60%，优于 ESM-IF1 的 43% 和 AbMPNN 的 56%，且在 predicted structures 上与 solved structures 的表现接近。
  - 证据：[doi:10.1093/bioadv/vbae202, p.3]
- **results：** 对采样并 refold 的 CDR 序列，AntiFold 的平均 CDR RMSD 为 0.95 Å，优于 AbMPNN 0.98 Å、ESM-IF1 1.01 Å 和 ProteinMPNN 1.03 Å。
  - 证据：[doi:10.1093/bioadv/vbae202, p.3]
- **results：** 在 anti-lysozyme DMS 上，AntiFold 的 Spearman 相关为 0.418；在 7 抗体 affinity-maturation 数据上，它对 improved variants 的 median rank score 达到 80%。
  - 证据：[doi:10.1093/bioadv/vbae202, p.3]

## 页码证据

- [doi:10.1093/bioadv/vbae202, p.1]
- [doi:10.1093/bioadv/vbae202, p.2]
- [doi:10.1093/bioadv/vbae202, p.3]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
