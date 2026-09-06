# Bilingual language model for protein sequence and structure

- **论文 ID：** `EVIW-50CC17ACB2AEA40C`
- **期刊 / 来源：** NAR Genom Bioinform
- **发表时间：** 2024 Nov 15
- **DOI：** [10.1093/nargab/lqae150](https://doi.org/10.1093/nargab/lqae150)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `语言模型` / `结构预测`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 ProstT5：在 ProtT5 上继续预训练并双向微调的 bilingual pLM，能够在 amino acid 与 3Di 之间翻译，生成新蛋白序列，增强结构相关 embeddings，并把 3Di 预测与结构级检索加速到无需先做完整结构预测即可完成。

## 创新边界

`新意主要在于把现成的 ProtT5 扩展为 sequence↔structure 的双向翻译模型；不是从头训练的新基础模型，也没有湿实验或独立前瞻验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何把蛋白 1D 序列与由 Foldseek/3Di 表示的 3D 结构统一到一个语言模型中，从而同时支持结构-序列互译、结构相关表征学习、快速远程同源搜索与逆折叠。

## 方法

- 从AlphaFoldDB构建非冗余结构-序列对，微调ProtT5执行3Di到氨基酸及反向翻译。[doi:10.1093/nargab/lqae150, p.1]

## 数据与基准

- 训练数据来自AlphaFoldDB高质量预测结构，规模受非冗余和质量过滤约束。[doi:10.1093/nargab/lqae150, p.1][doi:10.1093/nargab/lqae150, p.11]

## 比较基线

- MMseqs2、ProteinMPNN、one-hot及单模态/任务特定表示。[doi:10.1093/nargab/lqae150, p.6][doi:10.1093/nargab/lqae150, p.8]

## 结果证据

- 论文报告结构感知搜索/预测优于传统序列比对，并在部分结构生成指标上优于ProteinMPNN；均为计算评估。[doi:10.1093/nargab/lqae150, p.6][doi:10.1093/nargab/lqae150, p.10]

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 3Di到序列映射不平衡，且使用3Di预训练后再评估结构相关任务存在循环性/信息泄漏风险。[doi:10.1093/nargab/lqae150, p.11]

## 仍未知

- 对未见家族、真正 novel fold 以及无序蛋白的泛化能力仍不清楚。
- 3Di 直接预测在不同数据分布下的稳健性与可迁移性未被独立验证。
- 公开资源是否包含可直接复现全部训练流程的完整环境说明，文中未完全展开。

## Pi 结构化证据摘录

- **baseline：** 结构检索对照主要是 Foldseek on experimental 3Di、关闭 C-alpha reranking 的 Foldseek，以及传统序列检索 MMseqs2。
  - 证据：[doi:10.1093/nargab/lqae150, p.5]；[doi:10.1093/nargab/lqae150, p.6]
- **baseline：** 表征与分类基线包括 random transfer、HBI MMseqs2、ESM-1b、Ankh、ProtT5；逆折叠的关键对照是 ProteinMPNN。
  - 证据：[doi:10.1093/nargab/lqae150, p.6]；[doi:10.1093/nargab/lqae150, p.9]
- **data：** 训练集来自 clustered AFDB：214M UniProtKB 预测先聚成 52M representatives，再经 Foldseek 聚为 18.8M clusters，最终筛到 17M proteins，对应 34M 训练样本；验证和测试各保留 474 个代表蛋白。
  - 证据：[doi:10.1093/nargab/lqae150, p.2]
- **data：** 评测数据覆盖 NetSurfP-2.0、CASP12、CASP14、NEW364、DevSet1014/TestSet300、ConSurf10k、CATH、SCOPe40、DeepLoc setHARD，以及 M. jannaschii proteome 的 runtime benchmark。
  - 证据：[doi:10.1093/nargab/lqae150, p.4]；[doi:10.1093/nargab/lqae150, p.5]
- **declared_resources：** 公开资源包括 HuggingFace 上的 ProstT5 模型、GitHub 示例脚本、Zenodo 存档、PDB files、3Di dataset/splits，以及 Foldseek webserver 集成。
  - 证据：[doi:10.1093/nargab/lqae150, p.12]
- **declared_resources：** 训练与推理资源还包括 8×Nvidia A100 80GB、DeepSpeed stage-2、bf16、torchInductor，以及在 MacBook M1 与 RTX A5000 上做的 runtime benchmark。
  - 证据：[doi:10.1093/nargab/lqae150, p.3]；[doi:10.1093/nargab/lqae150, p.5]
- **limitations：** 作者明确承认高 pLDDT 过滤会偏向短而规则、尤其偏 helices 的蛋白，并排除大多数 intrinsically disordered proteins，因此训练分布带有明显偏差。
  - 证据：[doi:10.1093/nargab/lqae150, p.11]
- **limitations：** 3Di token 分布严重不均衡，而且部分 secondary structure/3Di/CATH 评测存在 circularity 与信息泄漏风险；对真正新 fold 的泛化仍未被独立证明。
  - 证据：[doi:10.1093/nargab/lqae150, p.6]；[doi:10.1093/nargab/lqae150, p.11]
- **method：** 作者先用 Foldseek 将蛋白结构编码为 3Di token，并给 ProtT5 扩展 20 个 3Di 词元与 <fold2AA>/<AA2fold> 方向标记，以支持 amino acid↔3Di 的双向翻译。
  - 证据：[doi:10.1093/nargab/lqae150, p.2]；[doi:10.1093/nargab/lqae150, p.3]
- **method：** 训练流程先在 17M 高质量、非冗余的 AFDB 蛋白上做 span denoising，再用 DeepSpeed、bf16 和 torchInductor 进行约 700K steps 的双向翻译微调。
  - 证据：[doi:10.1093/nargab/lqae150, p.2]；[doi:10.1093/nargab/lqae150, p.3]
- **method：** 下游评估把 ProstT5 的 encoder 最后一层 embeddings 送入 CNN、light-attention、contrastive learning 与 EAT/Foldseek 等流程，分别测试结构、功能和检索任务。
  - 证据：[doi:10.1093/nargab/lqae150, p.4]；[doi:10.1093/nargab/lqae150, p.5]
- **results：** 在 SCOPe40 远程同源检测上，ProstT5 预测 3Di 后接 Foldseek 的 superfamily ROC-AUC 为 0.45，接近实验 3Di 的 0.49，明显高于 MMseqs2 的 0.06；用 3Di 直接预测还比先做结构预测快了三个数量级。
  - 证据：[doi:10.1093/nargab/lqae150, p.6]
- **results：** 在 CATH annotation transfer 中，ProstT5(3Di) 的 C/A/T/H 准确率为 90/77/65/75，ProstT5(AA) 与 ProstT5(cat) 也整体优于 ProtT5、ESM-1b 和 Ankh。
  - 证据：[doi:10.1093/nargab/lqae150, p.6]
- **results：** 在二级结构等 embedding 任务上，ProstT5 比 ProtT5 更好，但把 3Di 作为输入或 one-hot 3Di 往往会让 secondary structure 指标接近上限；而 binding、conservation 和 location 任务有时会出现轻微退化。
  - 证据：[doi:10.1093/nargab/lqae150, p.7]；[doi:10.1093/nargab/lqae150, p.11]
- **results：** 逆折叠方面，ProstT5 生成序列的平均 lDDT 为 0.72、TM-score 为 0.58、RMSD 为 2.90、PIDE 为 21.9%，加入 roundtrip 过滤后略升到 lDDT 0.73；它接近 ProteinMPNN 但仍略弱。
  - 证据：[doi:10.1093/nargab/lqae150, p.8]；[doi:10.1093/nargab/lqae150, p.9]；[doi:10.1093/nargab/lqae150, p.10]；[doi:10.1093/nargab/lqae150, p.11]

## 页码证据

- [doi:10.1093/nargab/lqae150, p.6]
- [doi:10.1093/nargab/lqae150, p.8]
- [doi:10.1093/nargab/lqae150, p.10]
- [doi:10.1093/nargab/lqae150, p.11]
- [doi:10.1093/nargab/lqae150, p.12]
- [doi:10.1093/nargab/lqae150, p.1]
- [doi:10.1093/nargab/lqae150, p.6]
- [doi:10.1093/nargab/lqae150, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
