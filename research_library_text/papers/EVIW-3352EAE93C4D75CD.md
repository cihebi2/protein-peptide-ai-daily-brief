# Advancing generative large language models toward discriminative performance in protein function prediction

- **论文 ID：** `EVIW-3352EAE93C4D75CD`
- **期刊 / 来源：** Genome Biol
- **发表时间：** 2026 May 21
- **DOI：** [10.1186/s13059-026-04109-8](https://doi.org/10.1186/s13059-026-04109-8)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `扩散/生成` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 OPUS-PLLM，一个用于 protein function prediction 的 multitask generative LLM，配套 modality encoding、modality refinement 和 instruction tuning 三阶段训练；同时构建 OPUS-InstructionCorpus、OPUS-InstructionCorpus-Evol 及相关 benchmark，并报告其在多数评测上优于现有生物知识增强 LLM，且在不少场景下超过 discriminative baselines。

## 创新边界

`新意主要在训练范式、指令数据构建与跨任务序列到功能映射，而不是新的 wet-lab 发现或蛋白候选生成。`。这不是全球首创性检索或独立复现结论。

## 研究问题

现有生物知识增强型 generative LLM 主要在自然语言式功能注释上有优势，但在 subcellular localization、GO term、EC number 等结构化多标签任务上常落后于专门的 discriminative model；作者要解决的是如何让生成式模型在保留通用问答与文本生成能力的同时，逼近甚至超过蛋白功能预测中的判别式基线。

## 方法

- 构建OPUS-InstructionCorpus及其Evol版本，对生成LLM进行多任务指令训练，并把自由文本输出映射到功能分类。

## 数据与基准

- 覆盖五项核心任务、18个基准和六类功能注释；另构建1684题Swiss2024-MCQA。

## 比较基线

- ChatGPT-4o、DeepSeek-v3、生物LLM、ESM2/ProtT5等判别模型。

## 结果证据

- 论文报告多数任务超过生物知识LLM和专用判别模型；GO任务平均F1相对次优生物LLM提高29.90%、相对最佳判别模型提高8.88%。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 通用LLM把序列当token串，残基级功能分析和CoT训练仍不足；生成输出的严格标签映射可能影响评价。

## 仍未知

- 冻结材料未验证公开代码仓库是否可完整复现全部结果。
- 补充材料 S1-S16 未逐表展开，部分细节只能依赖正文概述。
- 未见独立 prior-art 证据来验证 global novelty。

## Pi 结构化证据摘录

- **baseline：** 主要 generative baselines 包括 InstructProtein、Prot2Text、BioMedGPT、OPI-Llama 和 OPI-Galactica。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.3]；[doi:10.1186/s13059-026-04109-8, p.4]
- **baseline：** 主要 discriminative baselines 以 ESM2、ProtT5、Ankh 作为表示来源并配合 OPUS-GO 风格的 MLP head，同时还比较了 DeepLoc、OPILoc、DeepGO-SE 等任务专用方法。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.4]；[doi:10.1186/s13059-026-04109-8, p.9]；[doi:10.1186/s13059-026-04109-8, p.16]
- **baseline：** 扩展评测还引入 DeepSeek-7B、Qwen3-8B-Base/Instruct、Galactica-125M/1.3B/6.7B、Llama3-8B 及 RAG 版本作为 general-purpose LLM 对照。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.10]；[doi:10.1186/s13059-026-04109-8, p.11]；[doi:10.1186/s13059-026-04109-8, p.12]；[doi:10.1186/s13059-026-04109-8, p.14]
- **data：** 编码阶段训练集 ProtDescribe 含 546,026 对 protein sequence-functional description pairs，并划分为 436,822/54,602/54,602。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.21]
- **data：** OPUS-InstructionCorpus 基于 SWISS-PROT 2022-01 构建，覆盖 GO term、UniProt keyword、functional description、protein family、subcellular localization 和 EC number，经抽取、重标注、增强与同源去除后得到 2.11M unique triples。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.21]；[doi:10.1186/s13059-026-04109-8, p.22]；[doi:10.1186/s13059-026-04109-8, p.23]
- **data：** 评测侧包含 17 个 testing datasets；Swiss2024-series 由 SWISS-PROT 2024-05 构建，四个数据集分别含 904、1,607、1,712、1,687 条序列，另有 OPUS-InstructionCorpus-Evol 的 3.75M triples、1.64M chat examples 和 1,684 条 Swiss2024-MCQA。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.13]；[doi:10.1186/s13059-026-04109-8, p.22]；[doi:10.1186/s13059-026-04109-8, p.23]
- **declared_resources：** 论文声明源码已发布在 GitHub，许可证为 GPL-3.0。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.26]
- **declared_resources：** OPUS-InstructionCorpus、OPUS-InstructionCorpus-Evol 和 Benchmark 数据集已放在 Hugging Face，许可证为 CC BY 4.0。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.26]；[doi:10.1186/s13059-026-04109-8, p.28]
- **declared_resources：** pretrained models 也已在 Hugging Face 发布。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.26]；[doi:10.1186/s13059-026-04109-8, p.28]
- **limitations：** 作者明确指出当前训练数据缺少 explicit Chain-of-Thought supervision，因此 reasoning-enhanced foundation models 的潜力未被充分释放。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.17]
- **limitations：** 模型采用 protein-level averaging，会平滑局部信号，因此对单点突变等残基级功能变化不够敏感。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.17]
- **limitations：** 作者也把引入 structured biological knowledge graphs 与更细粒度 residue-level features 视为后续方向，说明当前框架仍依赖序列级表示与现有标签。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.17]；[doi:10.1186/s13059-026-04109-8, p.18]
- **method：** OPUS-PLLM 采用三阶段框架：modality encoding、modality refinement、instruction tuning，把 protein sequence 映射到自然语言功能输出。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.18]；[doi:10.1186/s13059-026-04109-8, p.20]；[doi:10.1186/s13059-026-04109-8, p.21]
- **method：** modality encoding 阶段用 ESM2 提取序列表示、Llama3 提取文本表示，再通过线性投影与 contrastive learning 对齐共享空间。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.18]；[doi:10.1186/s13059-026-04109-8, p.19]
- **method：** modality refinement 与 instruction tuning 分别借助 2.11M instruction triplets 和 LoRA，对 projection module 与 generative LLM 做任务化适配。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.20]；[doi:10.1186/s13059-026-04109-8, p.21]
- **results：** 在 13 个测试数据集、5 个任务上，OPUS-PLLM 对 5 个生物知识增强 generative LLM 全面领先，并在 GO/EC 等复杂任务上给出显著提升。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.3]；[doi:10.1186/s13059-026-04109-8, p.4]
- **results：** 与基于 ESM2、ProtT5、Ankh 的 discriminative baseline 相比，OPUS-PLLM 在多数任务上达到 comparable 或更优；用 OPUS-PLLM 表示做 discriminative head 时也优于对应 PLM 表示。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.4]；[doi:10.1186/s13059-026-04109-8, p.9]；[doi:10.1186/s13059-026-04109-8, p.11]；[doi:10.1186/s13059-026-04109-8, p.12]；[doi:10.1186/s13059-026-04109-8, p.16]
- **results：** 作者报告 GO term prediction 的平均 F1 比 next-best biological-knowledge-integrated LLM 高 29.90%，比 top discriminative models 高 8.88%，且在 Swiss2024 系列上保持一致优势。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.1]；[doi:10.1186/s13059-026-04109-8, p.3]；[doi:10.1186/s13059-026-04109-8, p.6]
- **results：** OPUS-PLLM-Evol 在 MCQA 上优于 general-purpose foundation models，而原有生物知识增强 LLM 在该任务上几乎为零。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.13]；[doi:10.1186/s13059-026-04109-8, p.15]
- **results：** 单任务与多任务训练整体上可比，且在 subcellular localization 上多任务设置相对单任务版本有 10.1% 的平均 accuracy 提升。
  - 证据：[doi:10.1186/s13059-026-04109-8, p.7]；[doi:10.1186/s13059-026-04109-8, p.8]

## 页码证据

- [doi:10.1186/s13059-026-04109-8, p.17]
- [doi:10.1186/s13059-026-04109-8, p.1]
- [doi:10.1186/s13059-026-04109-8, p.3]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
