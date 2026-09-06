# Fine-tuning protein language models boosts predictions across diverse tasks

- **论文 ID：** `EVIW-70FFFBE1CB0E8DF4`
- **期刊 / 来源：** Nat Commun
- **发表时间：** 2024 Aug 28
- **DOI：** [10.1038/s41467-024-51844-2](https://doi.org/10.1038/s41467-024-51844-2)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者比较了 ESM2、ProtT5、Ankh/ProstT5 在 8 个蛋白预测任务上的冻结 embedding、full fine-tuning 与 LoRA/PEFT 方案，主张监督 fine-tuning 几乎总能提升下游预测，并给出可直接复用的 notebooks 与实践建议。

## 创新边界

`创新边界主要是下游 transfer 的监督微调与 PEFT 评估，不是新的蛋白设计生成模型。`。这不是全球首创性检索或独立复现结论。

## 研究问题

评估 task-specific supervised fine-tuning 与 parameter-efficient fine-tuning 是否能系统提升 protein language models 在多种下游预测任务中的性能，并尽量降低训练资源开销。

## 方法

- 对三个 PLM 做任务特异监督全量微调或 PEFT，并覆盖逐蛋白、逐残基及适应度景观任务。[doi:10.1038/s41467-024-51844-2, p.1][doi:10.1038/s41467-024-51844-2, p.2]

## 数据与基准

- 八个公开任务集，包括 GFP、稳定性、AAV、GB1、meltome、二级结构、亚细胞定位和无序数据。[doi:10.1038/s41467-024-51844-2, p.7]

## 比较基线

- 冻结嵌入、全量微调、PEFT，并横向比较 ESM2、ProtT5、Ankh。[doi:10.1038/s41467-024-51844-2, p.1]

## 结果证据

- 作者报告监督微调几乎总能提高下游预测，PEFT 常可接近全量微调，尤其小数据单蛋白适应度任务受益；二级结构等接近上限任务增益有限。[doi:10.1038/s41467-024-51844-2, p.1][doi:10.1038/s41467-024-51844-2, p.2]

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 部分“未知蛋白”基准规模很小或切分不一致，二级结构性能可能已接近上限；最优策略依赖任务、数据与模型。[doi:10.1038/s41467-024-51844-2, p.2]

## 仍未知

- 这些结论对未测试的蛋白任务、数据规模和模型家族的外部泛化程度未知。
- Zenodo/GitHub 资源的实际可运行性与完整性未在本次审查中验证。
- 论文未提供独立 prior-art 证据，因此 global novelty 仅做保守判断。

## Pi 结构化证据摘录

- **baseline：** 主要非微调基线是冻结 embeddings + 单层全连接预测头。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.6]；[doi:10.1038/s41467-024-51844-2, p.7]
- **baseline：** Mutation landscape 的对照包括基于 MMseqs2 的 homology-based inference（HBI）和 reference-free analysis（RFA）。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.4]；[doi:10.1038/s41467-024-51844-2, p.6]
- **baseline：** Subcellular location 与 disorder 的比较对象分别包括 Light Attention、SETH、ODiNPred 和 AlphaFold2。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.4]
- **baseline：** Secondary structure 结果还对照了文献中的 ProtT5 与 ProstT5 预训练 embedding 方法。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.3]
- **baseline：** PEFT 层面还把 IA3 与 Prefix-tuning 作为 LoRA 的方法学对照。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.2]；[doi:10.1038/s41467-024-51844-2, p.4]
- **data：** 数据覆盖 3 个 mutational landscapes（GFP、AAV、GB1）和 5 个 diverse tasks（Stability、Meltome、SubCellLoc、Disorder、Secondary structure）。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.3]；[doi:10.1038/s41467-024-51844-2, p.6]
- **data：** 数据来源包括 TAPE、FLIP、DeepLoc 和 SETH；作者还在文中重打包了数据以便复用。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.7]；[doi:10.1038/s41467-024-51844-2, p.6]
- **data：** 切分策略尽量减少泄漏：序列任务用 MMseqs2 做 sequence-identity 去冗余，结构相关任务也使用更严格的 redundancy reduction；Secondary structure 还用 CASP12 和 NEW364 作为测试对照。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.5]；[doi:10.1038/s41467-024-51844-2, p.6]；[doi:10.1038/s41467-024-51844-2, p.3]
- **declared_resources：** 作者在单张 NVIDIA A10G 24GB GPU 上完成训练，并按需使用 mixed precision、gradient accumulation 和 DeepSpeed CPU offloading。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.5]；[doi:10.1038/s41467-024-51844-2, p.7]
- **declared_resources：** 软件环境包括 Torch 1.13.1 和 transformers 4.26.1，模型初始化来自 Hugging Face checkpoints。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.7]
- **declared_resources：** 论文声明提供了 fine-tuning notebooks、embedding-based predictor notebooks、重打包数据以及 source data。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.7]
- **limitations：** Secondary structure 的提升很小，最高只有约 1.2 个百分点，而且 CASP12 与 NEW364 的对比暴露出 benchmark 本身并不稳健。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.3]
- **limitations：** 作者自己的 PEFT 方法比较只基于单个模型和单个数据集，因此对其他任务和模型的外推性有限。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.2]
- **limitations：** 随机种子会显著影响结果，其波动幅度可接近超参数选择或模型选择带来的差异。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.6]
- **limitations：** 作者明确提示，过拟合很大程度上由数据集特性驱动，单靠调参或换模型并不能完全消除。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.5]；[doi:10.1038/s41467-024-51844-2, p.6]
- **limitations：** 部分 baseline 也有数据依赖的失败模式，例如 RFA 对 GFP 失效、对 AAV 还需要额外过滤序列。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.6]
- **method：** 将三类 pLM（ESM2、ProtT5、Ankh/ProstT5）放到 8 个预测任务上，比较冻结 embeddings 与监督 fine-tuning 的下游效果。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.1]；[doi:10.1038/s41467-024-51844-2, p.2]
- **method：** 对较大模型主要采用 LoRA 这一 PEFT 方案；较小的 ESM2 版本也做了 full fine-tuning 以便对照。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.2]；[doi:10.1038/s41467-024-51844-2, p.7]
- **method：** 预训练对照使用冻结 embeddings，再接一个 size 32 的全连接预测头；fine-tuning 则把同样的头接到 encoder 上并更新 encoder 或其 LoRA 子集。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.6]；[doi:10.1038/s41467-024-51844-2, p.7]
- **method：** LoRA 的默认配置为 rank 4、alpha 1，作用于 query、key、value 与 attention output；同时还比较了 DoRA、IA3 和 Prefix-tuning。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.2]；[doi:10.1038/s41467-024-51844-2, p.7]
- **method：** 训练采用 Adam、基于 validation loss 的 early stopping，并对不同随机种子重复训练；大模型使用 mixed precision、gradient accumulation 和必要时的 DeepSpeed CPU offloading。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.5]；[doi:10.1038/s41467-024-51844-2, p.7]
- **results：** 总体上，监督 fine-tuning 在几乎所有 pLM/task 组合上都带来数值提升；少数例外包括 ESM2-150M on Stability 以及两个 Ankh 模型，全文中仅 5/64 组合变差。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.2]
- **results：** 在 PEFT 对比里，LoRA 和 DoRA 优于 IA3 与 Prefix-tuning，而且四种微调法平均都优于冻结 embeddings；作者因此主用 LoRA。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.2]
- **results：** Disorder 任务中，SETH-LoRA 将 Spearman 从 0.72 提升到 0.736；ESM2-150M 进一步达到 0.742，并超过更大的 ESM2 版本。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.4]
- **results：** Subcellular location 任务里，LoRA 的数值表现超过 Light Attention，但作者也指出该差异未必在更常见的 95% CI 下显著。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.4]
- **results：** Mutational landscape 任务中，fine-tuned pLM 平均优于 HBI 和 RFA，两类简单基线无法稳定覆盖 GFP、AAV 和 GB1。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.4]
- **results：** 资源方面，LoRA 对 ESM2-3B 的训练速度约快 4.5 倍；但对最小的 ESM2-8M，LoRA 反而略慢。
  - 证据：[doi:10.1038/s41467-024-51844-2, p.5]

## 页码证据

- [doi:10.1038/s41467-024-51844-2, p.1]
- [doi:10.1038/s41467-024-51844-2, p.1]
- [doi:10.1038/s41467-024-51844-2, p.2]
- [doi:10.1038/s41467-024-51844-2, p.7]
- [doi:10.1038/s41467-024-51844-2, p.7]
- [doi:10.1038/s41467-024-51844-2, p.7]
- [doi:10.1038/s41467-024-51844-2, p.2]
- [doi:10.1038/s41467-024-51844-2, p.1]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
