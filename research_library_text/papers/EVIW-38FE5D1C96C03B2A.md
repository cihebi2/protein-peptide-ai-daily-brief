# p-IgGen: a paired antibody generative language model

- **论文 ID：** `EVIW-38FE5D1C96C03B2A`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2024 Nov 9
- **DOI：** [10.1093/bioinformatics/btae659](https://doi.org/10.1093/bioinformatics/btae659)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `扩散/生成` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 p-IgGen，一个基于 GPT-2 风格 decoder-only 架构的 paired antibody generative language model；它先在大规模 unpaired OAS 序列上预训练，再在 1.8M paired VH/VL 序列上微调，并可继续微调成 developable p-IgGen 以偏向 TAP 低风险抗体分布。

## 创新边界

`主要新意在于配对抗体生成与 developability 偏置微调；冻结页中报告的证据均为 in silico 评估，未见 wet-lab 验证，且全球新颖性未被独立外部证据验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

面向抗体药物发现，生成新的配对 heavy-light chain 抗体序列，同时尽量避免 developability 问题，并能进一步偏向临床样本式的 3D 生物物理性质分布。

## 方法

- 先在未配对序列上预训练 IgGen，再用配对重/轻链序列微调为 p-IgGen，并对预测的三维生物物理性质分布进一步偏置。[doi:10.1093/bioinformatics/btae659, p.1][doi:10.1093/bioinformatics/btae659, p.3]

## 数据与基准

- 使用 Observed Antibody Space 的配对与未配对抗体序列；过滤后的训练/测试集发布在 Zenodo。[doi:10.1093/bioinformatics/btae659, p.4]

## 比较基线

- 比较未配对 IgGen、配对 p-IgGen 及其他抗体语言模型的零样本表示性能，并比较生成序列与天然/临床抗体性质分布。[doi:10.1093/bioinformatics/btae659, p.1][doi:10.1093/bioinformatics/btae659, p.3]

## 结果证据

- 论文报告生成序列具有天然配对特征与抗体样多样性，并在零样本序列预测基准上优于所比较抗体语言模型；均为计算评估。[doi:10.1093/bioinformatics/btae659, p.1]

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 可开发性来自结构/性质预测分布约束，没有证明生成抗体的表达、结合、特异性或安全性；OAS 采样偏差可能被模型继承。[doi:10.1093/bioinformatics/btae659, p.3][doi:10.1093/bioinformatics/btae659, p.4]

## 仍未知

- 补充材料中的完整过滤规则、统计检验细节和表达任务完整分数未在冻结页中展开。
- 未见独立的 wet-lab 验证，因此生成序列的真实实验可开发性仍无法从当前证据直接确认。

## Pi 结构化证据摘录

- **baseline：** 作者将 p-IgGen 与随机 VH/VL 配对、自然训练序列，以及 FLAb 中的 IgLM、AntiBERTy、ProGen OAS、ProteinMPNN、ESM-IF 等模型进行比较。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.2]；[doi:10.1093/bioinformatics/btae659, p.4]
- **baseline：** developability 评估的主要对照是 paired OAS validation set，且文中还对同一批生成序列做随机重配对作为 pairing 控制。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.2]；[doi:10.1093/bioinformatics/btae659, p.3]
- **baseline：** immunogenicity benchmark 上，p-IgGen 的表现优于 IgLM、AntiBerty、ESM-IF、MPNN 等；expression benchmark 上，论文文本称它优于 antibody-specific LMs，但不及部分 ProGen 模型。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.4]
- **data：** 训练数据来自 Observed Antibody Space (OAS)，仅使用 human sequences，过滤后得到 117,431,915 条 VL 和 130,246,252 条 VH unpaired 序列。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.2]
- **data：** paired 数据集包含 1,800,545 条 VH/VL 配对序列；作者沿用 paired 模型的 train/validation/test 划分，并在比较中使用 OAS validation/test 相关样本。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.2]；[doi:10.1093/bioinformatics/btae659, p.3]
- **data：** developable 微调集先用 ABodyBuilder2 对所有 paired OAS 序列建模，再用 TAP 标注；保留四个 structure-based metrics 全为 green flag 的 909,790 条序列作为安全集合。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.2]；[doi:10.1093/bioinformatics/btae659, p.3]
- **data：** zero-shot 任务数据来自 FLAb：immunogenicity 集包含 217 个 therapeutics 的抗药抗体反应，expression 集来自 anti-VEGF 的 deep mutational scan，共 4,275 条序列。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.2]；[doi:10.1093/bioinformatics/btae659, p.4]
- **declared_resources：** 论文明确给出模型与 inference code 的公开地址：www.github.com/oxpig/p-IgGen。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.1]
- **declared_resources：** cleaned training data 已存放于 Zenodo，DOI 为 10.5281/zenodo.13880874。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.1]；[doi:10.1093/bioinformatics/btae659, p.5]
- **declared_resources：** IgGen 训练使用 4 A100 GPUs；p-IgGen 与 developable p-IgGen 的微调使用单张 A100 GPU，整体实现于 PyTorch。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.1]；[doi:10.1093/bioinformatics/btae659, p.2]
- **declared_resources：** 模型规模为 17,349,888 parameters。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.2]
- **limitations：** 全文报告的是计算与结构建模层面的证据，未见生成抗体的湿实验验证或真实功能回收实验。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.1]；[doi:10.1093/bioinformatics/btae659, p.3]；[doi:10.1093/bioinformatics/btae659, p.4]
- **limitations：** developable 目标来自 TAP 的四个 structure-based flags，而不是直接的实验 developability 指标；此外作者明确说明未对 CDR length metric 进行过滤。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.2]；[doi:10.1093/bioinformatics/btae659, p.3]
- **limitations：** 模型并非在所有任务上都最强：expression 任务上 general protein LMs 仍优于 p-IgGen，说明其优势更集中于 antibody-specific 场景。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.4]
- **method：** 模型采用 GPT-2 like 的 autoregressive decoder-only 架构，并加入 rotary positional embeddings；paired 模型将 light chain 与 heavy chain 连接，训练时随机采用正向或反向输入，使推断时可由一条链生成另一条链。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.1]；[doi:10.1093/bioinformatics/btae659, p.2]
- **method：** 训练流程分三步：IgGen 在 unpaired 序列上预训练，p-IgGen 在 paired VH/VL 上微调，developable p-IgGen 再在被 TAP 过滤出的 developable 序列上微调。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.2]；[doi:10.1093/bioinformatics/btae659, p.3]
- **method：** 采样时使用 temperature 1.2、top-p 0.95，并丢弃最低 5% 生成序列；developable p-IgGen 将 temperature 提高到 1.25 以维持多样性。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.2]
- **results：** 生成序列在 Hamming distance、diversity 和 ESM-2 likelihood 上与自然序列接近；ANARCI 能为所有生成序列识别 heavy 和 light chain，CDR length 分布也与自然抗体相近。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.2]；[doi:10.1093/bioinformatics/btae659, p.3]
- **results：** p-IgGen 生成序列的 VH/VL mutation rate correlation 为 0.52，接近自然序列的 0.51，而随机配对仅为 -0.04，说明模型捕捉到真实 pairing 偏好。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.2]；[doi:10.1093/bioinformatics/btae659, p.3]
- **results：** 在 true pairing 与 50 个随机 VL 的 likelihood 比较中，94% 的情况真实配对高于随机配对均值；12% 的 VH 中真实 VL 取得最高 likelihood，52% 的情况位于前 8。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.3]
- **results：** developable p-IgGen 相比 p-IgGen 显著降低 TAP 的 amber/red flags，同时仍保持多样性和序列身份分布接近。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.3]
- **results：** 在 zero-shot immunogenicity 上，p-IgGen 的 Pearson correlation 为 0.53，优于 developable p-IgGen 的 0.52、ProGen/small 的 0.48 和 IgGen 的 0.45；在 expression 任务上，p-IgGen 优于所有 antibody-specific LMs，但部分更大的 general protein LMs 仍更强。
  - 证据：[doi:10.1093/bioinformatics/btae659, p.4]

## 页码证据

- [doi:10.1093/bioinformatics/btae659, p.1]
- [doi:10.1093/bioinformatics/btae659, p.3]
- [doi:10.1093/bioinformatics/btae659, p.1]
- [doi:10.1093/bioinformatics/btae659, p.3]
- [doi:10.1093/bioinformatics/btae659, p.4]
- [doi:10.1093/bioinformatics/btae659, p.4]
- [doi:10.1093/bioinformatics/btae659, p.1]
- [doi:10.1093/bioinformatics/btae659, p.4]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
