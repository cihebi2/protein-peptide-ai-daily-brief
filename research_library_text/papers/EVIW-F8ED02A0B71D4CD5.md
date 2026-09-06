# The promises of large language models for protein design and modeling

- **论文 ID：** `EVIW-F8ED02A0B71D4CD5`
- **期刊 / 来源：** Front Bioinform
- **发表时间：** 2023 Nov 23
- **DOI：** [10.3389/fbinf.2023.1304099](https://doi.org/10.3389/fbinf.2023.1304099)
- **范围标签：** `Pi 已解析` / `背景资料` / `论文声明资源` / `蛋白质设计` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者以 perspective 形式系统梳理了自然语言与 protein language 的类比，概述 Transformer、BERT、GPT 及其在蛋白领域的 Encoder-based、Decoder-based、conditional 和 encoder-decoder 变体，并把现有应用整理为一套面向未来的 protein modeling/design 路线图。[doi:10.3389/fbinf.2023.1304099, p.2] [doi:10.3389/fbinf.2023.1304099, p.3] [doi:10.3389/fbinf.2023.1304099, p.5] [doi:10.3389/fbinf.2023.1304099, p.6] [doi:10.3389/fbinf.2023.1304099, p.7] [doi:10.3389/fbinf.2023.1304099, p.8]

## 创新边界

`这是综述/观点文章，没有作者自己的新算法、新数据集或湿实验验证；新意主要在于概念整合、文献归纳和未来方向判断。[doi:10.3389/fbinf.2023.1304099, p.1] [doi:10.3389/fbinf.2023.1304099, p.9] [doi:10.3389/fbinf.2023.1304099, p.10]`。这不是全球首创性检索或独立复现结论。

## 研究问题

本文讨论如何将 LLM/Transformer 的表示学习与生成能力迁移到 protein modeling 与 protein design，重点关注蛋白序列表示、功能预测、条件生成、分子对接式设计，以及可解释性与计算成本等现实瓶颈。[doi:10.3389/fbinf.2023.1304099, p.1] [doi:10.3389/fbinf.2023.1304099, p.2] [doi:10.3389/fbinf.2023.1304099, p.8] [doi:10.3389/fbinf.2023.1304099, p.9]

## 方法

- perspective review。

## 数据与基准

- 被引研究。

## 比较基线

- 不适用。

## 结果证据

- 无原创结果。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 愿景性、非系统评估。

## 仍未知

- Supplementary Material 的具体内容未在逐页文本中展开，无法确认是否含额外分析或图表。
- 正文未见独立代码仓库或训练细节，因此无法判断是否存在可复现实作。

## Pi 结构化证据摘录

- **baseline：** 文章将 LLM/PLM 与传统 HMM、SVM、RNN 以及 task-specific deep learning models 作概念对比，以突出 transfer learning 和 parallel computation 的优势。
  - 证据：[doi:10.3389/fbinf.2023.1304099, p.1]；[doi:10.3389/fbinf.2023.1304099, p.3]；[doi:10.3389/fbinf.2023.1304099, p.4]
- **baseline：** 在蛋白生成与设计语境中，作者把自然进化样本与已发表系统如 ESM、ProteinBERT、ProGPT2、Progen 作为参照背景，而非本文自身的实验基线。
  - 证据：[doi:10.3389/fbinf.2023.1304099, p.5]；[doi:10.3389/fbinf.2023.1304099, p.6]；[doi:10.3389/fbinf.2023.1304099, p.7]
- **data：** 文中没有给出原创实验数据集；相关论述主要依赖公开 protein repositories 如 UniParc 与 UniProt，以及已发表模型的结果。
  - 证据：[doi:10.3389/fbinf.2023.1304099, p.4]；[doi:10.3389/fbinf.2023.1304099, p.5]
- **data：** 作者声明原始贡献与补充材料可在正文/Supplementary Material 中获得，但未提供独立的 benchmark、代码仓库或数据发布包。
  - 证据：[doi:10.3389/fbinf.2023.1304099, p.9]；[doi:10.3389/fbinf.2023.1304099, p.10]
- **declared_resources：** Funding 来自 National Center for Gene Therapy and Drugs based on RNA Technology、DOE Contract DE-AC02-05CH11231，以及 European Commission JRC 的合作。
  - 证据：[doi:10.3389/fbinf.2023.1304099, p.9]；[doi:10.3389/fbinf.2023.1304099, p.10]
- **declared_resources：** 文章提供了 Supplementary Material 链接，但正文没有声明专门的代码仓库或可复用模型权重。
  - 证据：[doi:10.3389/fbinf.2023.1304099, p.10]
- **limitations：** 作者明确指出 PLM 的可解释性仍是 open problem，attention-based explanation 的 faithfulness 与 plausibility 仍存在争议。
  - 证据：[doi:10.3389/fbinf.2023.1304099, p.9]
- **limitations：** 文中也强调模型训练和查询成本较高，压缩技术如 pruning、quantization、distillation 仍不足以完全解决该问题。
  - 证据：[doi:10.3389/fbinf.2023.1304099, p.9]
- **limitations：** 蛋白的 word boundaries、tokenization 与生物学 grammar 并不清晰，而且功能性结论仍需要大量实验验证。
  - 证据：[doi:10.3389/fbinf.2023.1304099, p.2]；[doi:10.3389/fbinf.2023.1304099, p.9]
- **method：** 文章先用 natural language 与 protein language 的类比建立分析框架，再据此讨论 tokenization、motif/domain 和长程依赖在蛋白中的对应关系。
  - 证据：[doi:10.3389/fbinf.2023.1304099, p.2]
- **method：** 正文按 Transformer、BERT、GPT、Encoder-based PLM、Decoder-based PLM、conditional Transformer、encoder-decoder Transformer 的顺序展开。
  - 证据：[doi:10.3389/fbinf.2023.1304099, p.3]；[doi:10.3389/fbinf.2023.1304099, p.4]；[doi:10.3389/fbinf.2023.1304099, p.5]；[doi:10.3389/fbinf.2023.1304099, p.6]；[doi:10.3389/fbinf.2023.1304099, p.7]；[doi:10.3389/fbinf.2023.1304099, p.8]
- **method：** 作者用 Table 1 和 Table 2 归纳既有工作与未来应用场景，而不是报告自有实验流程。
  - 证据：[doi:10.3389/fbinf.2023.1304099, p.6]；[doi:10.3389/fbinf.2023.1304099, p.8]
- **results：** 文章给出的核心结论是：Encoder-based PLM 更适合 embedding 与 downstream prediction，Decoder-based PLM 更适合 de novo generation，conditional Transformer 更适合定向蛋白设计。
  - 证据：[doi:10.3389/fbinf.2023.1304099, p.5]；[doi:10.3389/fbinf.2023.1304099, p.6]；[doi:10.3389/fbinf.2023.1304099, p.7]
- **results：** 作者进一步把 de novo drug design、enzyme design、multimodal PLM、explainability 与 compression 描述为未来最值得推进的方向。
  - 证据：[doi:10.3389/fbinf.2023.1304099, p.8]；[doi:10.3389/fbinf.2023.1304099, p.9]

## 页码证据

- [doi:10.3389/fbinf.2023.1304099, p.1]
- [doi:10.3389/fbinf.2023.1304099, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
