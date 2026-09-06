# S-PLM: Structure-Aware Protein Language Model via Contrastive Learning Between Sequence and Structure

- **论文 ID：** `EVIW-593480AEBAE04B3E`
- **期刊 / 来源：** Adv Sci (Weinh)
- **发表时间：** 2024 Dec 12
- **DOI：** [10.1002/advs.202404212](https://doi.org/10.1002/advs.202404212)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `有静态审计仓库` / `语言模型` / `结构预测`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

本文提出 S-PLM：通过 sequence 与 3D structure 的 multi-view contrastive learning，把结构信息注入基于 ESM2 的 sequence encoder；同时配套提供 fine-tuning top layers、adapter tuning 和 LoRA 等 lightweight tuning 工具箱，用于多种下游蛋白预测任务。[doi:10.1002/advs.202404212, p.1][doi:10.1002/advs.202404212, p.3][doi:10.1002/advs.202404212, p.14]

## 创新边界

`边界在于表示学习与下游 transfer prediction，不是蛋白候选生成、优化或 wet-lab 验证；其主张是把结构蒸馏进 sequence-only inference 的表示中。`。这不是全球首创性检索或独立复现结论。

## 研究问题

作者要解决的问题是：现有 protein language models 主要只从 sequence 学表示，缺少关键 3D structure 信息，因而在强依赖结构的蛋白任务上受限；同时，许多 joint-embedding 方法又要求推理时额外输入结构，增加了实际使用成本。[doi:10.1002/advs.202404212, p.1][doi:10.1002/advs.202404212, p.2]

## 方法

- ESM-2编码序列，Swin Transformer编码由AlphaFold结构得到的接触图，NT-Xent式损失对齐两视图；下游支持顶层微调、LoRA和adapter。

## 数据与基准

- 从Swiss-Prot随机选50万蛋白训练、4.15万验证，结构来自AlphaFold；下游含CATH、折叠、酶反应、GO、EC和二级结构任务。

## 比较基线

- ESM-2、ProtBert等序列PLM及需要序列+结构的SOTA方法。

## 结果证据

- 作者报告S-PLM在所测聚类/分类任务上优于序列PLM，并接近同时使用序列和结构的强方法。

## 可用资源与代码关系

- [https://github.com/duolinwang/S-PLM](https://github.com/duolinwang/S-PLM)
  - 固定 commit：`6fa9398d59b0408a24f1db5109406e167305b6ee`
  - 静态复用层级：B_static_partial_shape
  - 许可证边界：license_identified_MIT_terms_require_review

## 已知限制

- 输入结构来自AlphaFold，误差会进入表征；训练和验证序列未去相似，长度超过512残基时截断，可能高估泛化。

## 仍未知

- GitHub 仓库当前是否仍可访问且与 PDF 版本一致
- 公开代码的许可证与可复用边界是否完整
- 是否存在独立复现实验或外部验证
- structure-aware 效果在更长序列上的泛化幅度

## Pi 结构化证据摘录

- **baseline：** 论文在结构聚类、fold、GO/EC/SS 与 PROBE 中对比了 sequence-only baselines，包括 ESM2、PromptProtein、ProstT5、ESM-S、TAPE、ProteinBERT、ESM-1b 和 DML。[doi:10.1002/advs.202404212, p.5][doi:10.1002/advs.202404212, p.8][doi:10.1002/advs.202404212, p.9]
  - 证据：[doi:10.1002/advs.202404212, p.5]；[doi:10.1002/advs.202404212, p.8]；[doi:10.1002/advs.202404212, p.9]
- **baseline：** 论文也比较了多种 structure-aware 或 sequence+structure 方法，包括 GVP、GearNet、GearNet-Edge、CoupleNet、ESM-GearNet、PST 和 SaProt。[doi:10.1002/advs.202404212, p.8]
  - 证据：[doi:10.1002/advs.202404212, p.8]
- **baseline：** 在 PROBE 部分，还使用 ProtALBERT、ProtT5-XL、PFAM 与 Mut2Vec 作为 representation baselines。[doi:10.1002/advs.202404212, p.9][doi:10.1002/advs.202404212, p.10]
  - 证据：[doi:10.1002/advs.202404212, p.9]；[doi:10.1002/advs.202404212, p.10]
- **data：** 预训练数据来自 Swiss-Prot：随机抽取 500,000 条蛋白用于训练、41,500 条用于验证；长度超过 512 的序列在预训练中被截断。[doi:10.1002/advs.202404212, p.12]
  - 证据：[doi:10.1002/advs.202404212, p.12]
- **data：** 结构分析使用 CATH v4_3_0 的 CATHS40 数据集，并从 class、architecture、topology 三个层级挑选代表性 superfamily 序列。[doi:10.1002/advs.202404212, p.13]
  - 证据：[doi:10.1002/advs.202404212, p.13]
- **data：** fold classification 数据集包含 16,712 proteins 和 1,195 个 fold classes，并设置 Fold、Superfamily、Family 三个测试集合。[doi:10.1002/advs.202404212, p.13]
  - 证据：[doi:10.1002/advs.202404212, p.13]
- **data：** enzyme reaction classification 数据集包含 37,428 proteins 和 384 个四级 EC numbers；GO 与 EC 任务沿用既有划分，而 secondary structure 使用 Klausen 训练集与 CB513 测试集。[doi:10.1002/advs.202404212, p.13]
  - 证据：[doi:10.1002/advs.202404212, p.13]
- **declared_resources：** 训练与实验使用单张 A100 GPU，在 University of Missouri 的计算设施上运行，采用 mixed precision、SGD、cyclical learning rate、batch size 20 等配置。[doi:10.1002/advs.202404212, p.12][doi:10.1002/advs.202404212, p.14]
  - 证据：[doi:10.1002/advs.202404212, p.12]；[doi:10.1002/advs.202404212, p.14]
- **declared_resources：** 论文正文给出 GitHub 仓库与轻量调参工具链接，声称代码、configs 与可复现实验流程已公开。[doi:10.1002/advs.202404212, p.1][doi:10.1002/advs.202404212, p.14]
  - 证据：[doi:10.1002/advs.202404212, p.1]；[doi:10.1002/advs.202404212, p.14]
- **declared_resources：** 数据部分既包含可从 GitHub 下载的任务数据，也包含 CATH、Swiss-Prot 与 AlphaFold2 相关资源；作者同时声明支持性数据可按合理请求获取。[doi:10.1002/advs.202404212, p.13][doi:10.1002/advs.202404212, p.14]
  - 证据：[doi:10.1002/advs.202404212, p.13]；[doi:10.1002/advs.202404212, p.14]
- **limitations：** 作者明确指出，S-PLM 并不能在所有任务上都胜过其他 PLM；在 PROBE 上，像 ProtT5-XL 这类更大模型仍能在部分指标上领先。[doi:10.1002/advs.202404212, p.11]
  - 证据：[doi:10.1002/advs.202404212, p.11]
- **limitations：** 作者还指出，约 32% 的 PROBE 序列长度超过预训练时使用的 512 上限，这可能削弱模型对长序列的效果。[doi:10.1002/advs.202404212, p.11]
  - 证据：[doi:10.1002/advs.202404212, p.11]
- **limitations：** 文中承认 residue-level 表示仍需加强，并建议未来把最大序列长度提高到 1024 之类的设置。[doi:10.1002/advs.202404212, p.11]
  - 证据：[doi:10.1002/advs.202404212, p.11]
- **limitations：** 训练仅使用 AlphaFold2-SwissProt 的约 0.5M proteins，作者认为更广泛的 structure repositories 可能继续提升性能。[doi:10.1002/advs.202404212, p.11]
  - 证据：[doi:10.1002/advs.202404212, p.11]
- **method：** 预训练时同时输入 amino acid sequence 与 backbone Cα contact map；sequence 侧用 ESM2 + Structure-Aware Module，structure 侧用 Swin-Transformer，并各自投影到 256D protein-level embedding。[doi:10.1002/advs.202404212, p.3][doi:10.1002/advs.202404212, p.12]
  - 证据：[doi:10.1002/advs.202404212, p.3]；[doi:10.1002/advs.202404212, p.12]
- **method：** 对比学习目标改写自 NT-Xent / SimCLR：把同一 protein 的 sequence embedding 与 structure embedding 拉近，同时把不同 protein 的同模态与跨模态 embedding 推远。[doi:10.1002/advs.202404212, p.3][doi:10.1002/advs.202404212, p.12]
  - 证据：[doi:10.1002/advs.202404212, p.3]；[doi:10.1002/advs.202404212, p.12]
- **method：** 结构输入来自 AlphaFold2 预测结构生成的 Cα-Cα contact map，并采用 22 Å 阈值把 raw contact map 转成连续 similarity matrix。[doi:10.1002/advs.202404212, p.12]
  - 证据：[doi:10.1002/advs.202404212, p.12]
- **method：** 下游适配提供 fine-tuning top layers、adapter tuning 和 LoRA 三种 lightweight tuning 策略，用于 protein-level 与 residue-level 任务。[doi:10.1002/advs.202404212, p.3][doi:10.1002/advs.202404212, p.13]
  - 证据：[doi:10.1002/advs.202404212, p.3]；[doi:10.1002/advs.202404212, p.13]
- **results：** contrastive learning 后，同一 protein 的 sequence/structure embedding 在 t-SNE 中明显对齐；在 10-NN 上，sequence 邻域保留率约 69%，structure 邻域保留率约 89%。[doi:10.1002/advs.202404212, p.4]
  - 证据：[doi:10.1002/advs.202404212, p.4]
- **results：** 在 CATH structural hierarchy 上，S-PLM 的 CHI 约比 ProstT5 高 30%，比 ESM2 高约 300%，说明 sequence embedding 更具 structure awareness。[doi:10.1002/advs.202404212, p.5]
  - 证据：[doi:10.1002/advs.202404212, p.5]
- **results：** 在 enzyme clustering 上，deaminase 的 ARI 为 0.87，优于 ESM2 0.63、PromptProtein 0.46、ProstT5 0.80；kinase 的 ARI 为 0.72，也高于对应 baselines。[doi:10.1002/advs.202404212, p.6][doi:10.1002/advs.202404212, p.7]
  - 证据：[doi:10.1002/advs.202404212, p.6]；[doi:10.1002/advs.202404212, p.7]
- **results：** 在 fold 与 enzyme reaction classification 中，S-PLM 相比 ESM2 在冻结和 top-k fine-tuning 场景下总体更强，例如 fold 37.74% 对 34.96%，enzyme reaction 86.71% 对 84.50%。[doi:10.1002/advs.202404212, p.7]
  - 证据：[doi:10.1002/advs.202404212, p.7]
- **results：** 在 GO、EC 与 secondary structure 任务上，S-PLM 的最佳结果分别达到 GO-BP 0.495、GO-MF 0.686、SS 87.48%，并在若干设置下接近或超过结构输入方法。[doi:10.1002/advs.202404212, p.8]
  - 证据：[doi:10.1002/advs.202404212, p.8]
- **results：** 在 PROBE 上，S-PLM 在 drug target PFC 表现较好，但在 PPI binding affinity 上不占优；与 ESM2-650M 组合后，整体表现更均衡。[doi:10.1002/advs.202404212, p.9][doi:10.1002/advs.202404212, p.10]
  - 证据：[doi:10.1002/advs.202404212, p.9]；[doi:10.1002/advs.202404212, p.10]

## 页码证据

- [doi:10.1002/advs.202404212, p.12]
- [doi:10.1002/advs.202404212, p.13]
- [doi:10.1002/advs.202404212, p.1]
- [doi:10.1002/advs.202404212, p.2]
- [doi:10.1002/advs.202404212, p.5]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
