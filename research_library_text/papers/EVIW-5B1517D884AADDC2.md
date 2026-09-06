# A new paradigm for applying deep learning to protein-ligand interaction prediction

- **论文 ID：** `EVIW-5B1517D884AADDC2`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2024 Apr 5
- **DOI：** [10.1093/bib/bbae145](https://doi.org/10.1093/bib/bbae145)
- **范围标签：** `Pi 已解析` / `核心相关` / `有静态审计仓库` / `蛋白-配体` / `结构预测` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 IGModel，将蛋白结合口袋图与蛋白-配体几何交互图联合编码，在同一框架中同时预测 docking pose 的 RMSD 和 binding strength（pKd），并声称在多个 docking 与 screening benchmark 上达到或接近 SOTA。

## 创新边界

`这是一个用于 pose scoring 与 property prediction 的 transfer 型方法，不直接生成或优化候选分子；创新点主要在于把 RMSD 与 pKd 放进同一物理可解释框架，而不是 de novo design。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在 structure-based drug design 中，如何让 scoring function 同时对 docking pose 是否接近 native conformation（RMSD）以及与靶标的 binding strength（pKd）给出具有物理意义的预测，并在 redocking、cross-docking 与 screening 场景中保持鲁棒泛化，是本文要解决的核心问题。

## 方法

- 蛋白口袋图和蛋白-配体交互图双输入；EdgeGAT编码距离、二面角和方向角；每个PDBbind复合物用Vina/LeDock生成约15个姿势并联合训练RMSD/pKd。

## 数据与基准

- PDBbind v2019及生成姿势；CASF-2016、PDBbind-CrossDocked-Core、DISCO、无偏集合和AlphaFold2靶结构集合。

## 比较基线

- 传统评分函数、RF-Score/NN-Score/AGL-Score及文中多种深度评分器。

## 结果证据

- CASF-2016中含原生姿势Top1成功率97.5%，排除原生姿势95.1%；论文报告跨对接及预测结构测试有竞争力。

## 可用资源与代码关系

- [https://github.com/zchwang/IGModel](https://github.com/zchwang/IGModel)
  - 固定 commit：`2703fc3a1a2cf45357d990a93141ddeda7f38587`
  - 静态复用层级：C_license_or_component_gaps
  - 许可证边界：license_identified_MIT_terms_require_review

## 已知限制

- 训练标签和测试均大量源自PDBbind/模拟对接；高Top1并非实验亲和力；正文未给出湿实验验证，且完整数据泄漏审计不明确。

## 仍未知

- 补充材料中的完整消融、超参数和数据处理细节未在正文页中完全展开。
- GitHub 仓库已被正文声明，但本次未核验其实现、许可与可复现性。
- 论文的全局新颖性未由冻结证据独立验证。

## Pi 结构化证据摘录

- **baseline：** 论文主要对比了 DeepBSP、DeepRMSD、DeepRMSD+Vina、zPoseScore、GatedGCN ft 1.0、GT ft 1.0、RTMScore、GenScore、PLANET 以及 Vina 等基线。
  - 证据：[doi:10.1093/bib/bbae145, p.5]；[doi:10.1093/bib/bbae145, p.8]；[doi:10.1093/bib/bbae145, p.12]
- **baseline：** 作者明确指出，在 DUD-E 和 DUD-AD 的 screening 任务上，RTMScore、GatedGCN ft 1.0 与 GT ft 1.0 仍在 EF 上优于 IGModel，说明该方法并未在所有虚拟筛选指标上全面领先。
  - 证据：[doi:10.1093/bib/bbae145, p.5]
- **baseline：** 论文也把 DiffDock、DeepDock、GenScore 与一些基于距离似然或 graph transformer 的方法作为相关背景，用来说明现有模型要么缺乏物理可解释性，要么在 docking / screening 间存在权衡。
  - 证据：[doi:10.1093/bib/bbae145, p.2]；[doi:10.1093/bib/bbae145, p.8]
- **data：** 训练数据来自 PDBbind v2019 的 native protein-ligand complexes；作者还为每个复合物平均生成约 15 个 docking poses，并剔除了 CASF-2016、peptide ligands 以及无法被部分工具解析的样本。
  - 证据：[doi:10.1093/bib/bbae145, p.2]
- **data：** 验证集从 refine set 随机抽取 1000 对，其余 general set 样本用于训练；作者强调训练、验证和测试之间没有重叠的 protein-ligand pair。
  - 证据：[doi:10.1093/bib/bbae145, p.2]
- **data：** 评测覆盖 CASF-2016、PDBbind-CrossDocked-Core、DISCO、DUD-E、DUD-AD、unbias-v2019 及其 AlphaFold2 版本 CASF-2016-AF2 和 unbias-v2019-AF2。
  - 证据：[doi:10.1093/bib/bbae145, p.1]；[doi:10.1093/bib/bbae145, p.5]；[doi:10.1093/bib/bbae145, p.6]；[doi:10.1093/bib/bbae145, p.7]
- **declared_resources：** 论文正文明确给出模型代码仓库地址：https://github.com/zchwang/IGModel。
  - 证据：[doi:10.1093/bib/bbae145, p.1]
- **declared_resources：** 作者声明获得了多个基金支持，包括 National Key R&D Program of China、NSFC、Shandong Province、Singapore MOE、Guangdong Province 和 Shenzhen 的相关资助。
  - 证据：[doi:10.1093/bib/bbae145, p.11]
- **declared_resources：** 研究使用了公开基准与工具资源，包括 PDBbind、CASF-2016、CrossDocked-Core、DISCO、DUD-E、DUD-AD、AlphaFold2，以及 RDKit、AutoDock Vina、LeDock 和 SpyRMSD。
  - 证据：[doi:10.1093/bib/bbae145, p.2]；[doi:10.1093/bib/bbae145, p.6]；[doi:10.1093/bib/bbae145, p.7]；[doi:10.1093/bib/bbae145, p.12]
- **limitations：** 作者承认，若依赖共晶配体来定义 pocket，则在真实虚拟筛选场景中会受限，因为许多靶点并没有已知 native ligand；因此他们还测试了 self-ref 变体，但其 redocking 表现下降。
  - 证据：[doi:10.1093/bib/bbae145, p.5]
- **limitations：** 在 screening 任务上，IGModel 的 EF 仍低于部分强基线，说明它虽然在 docking 侧很强，但并非所有场景都达到 SOTA。
  - 证据：[doi:10.1093/bib/bbae145, p.5]
- **limitations：** 作者指出，在 CASF2016-AF2 与 unbias-v2019-AF2 这类基于 AlphaFold2 结构的数据上，整体 top1 success rate 更低，主要因为 docking poses 相对 native poses 的 RMSD 更大。
  - 证据：[doi:10.1093/bib/bbae145, p.7]
- **method：** 模型输入由两部分组成：蛋白结合口袋图和蛋白-配体原子交互图；交互边同时编码距离与方位信息，且蛋白原子只保留距共晶配体 8 Å 内的部分。
  - 证据：[doi:10.1093/bib/bbae145, p.3]
- **method：** 编码器采用两路 EdgeGAT 分别处理口袋图与交互图，再把图表示压缩为 1024 维嵌入，并通过两个解码分支分别输出 RMSD 与 pKd。
  - 证据：[doi:10.1093/bib/bbae145, p.3]；[doi:10.1093/bib/bbae145, p.4]
- **method：** 训练时，作者用 native complex 的 pKd 和 docking pose 的真实 RMSD 构造 pKdlabel = pKdnat - W * RMSDreal，并用 RMSD MSE、pKd MSE 以及一个鼓励 pKd 随 RMSD 下降的正则项联合优化。
  - 证据：[doi:10.1093/bib/bbae145, p.4]
- **results：** 在 CASF-2016 docking power 上，IGModel rmsd 的 top1 success rate 在包含 native poses 时为 97.5%，排除 native poses 时为 95.1%；IGModel pkd 对应为 93.3% 和 90.9%。
  - 证据：[doi:10.1093/bib/bbae145, p.4]
- **results：** 在 CASF-2016 上，IGModel pkd 的 scoring power PCC 为 0.831，ranking power SCC 为 0.723，作者据此称其在多个任务上较为均衡。
  - 证据：[doi:10.1093/bib/bbae145, p.5]
- **results：** 在 PDBbind-CrossDocked-Core 和 DISCO 上，模型在 redocking / cross-docking 的 top1 success rate 保持竞争力；在 unbias-v2019-AF2 上，IGModel rmsd 的 PCC/SCC 达到 0.609/0.552，top1 success rate 在 2 Å 与 3 Å cutoff 下为 0.227/0.296。
  - 证据：[doi:10.1093/bib/bbae145, p.6]；[doi:10.1093/bib/bbae145, p.7]；[doi:10.1093/bib/bbae145, p.8]
- **results：** 作者还展示了 latent space 的 PCA 分层和 attention 可解释性：较高 importance 的原子常对应极性相互作用、hydrogen bonds 与 π-π stacking。
  - 证据：[doi:10.1093/bib/bbae145, p.9]；[doi:10.1093/bib/bbae145, p.10]

## 页码证据

- [doi:10.1093/bib/bbae145, p.1]
- [doi:10.1093/bib/bbae145, p.2]
- [doi:10.1093/bib/bbae145, p.3]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
