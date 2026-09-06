# Protein embeddings predict binding residues in disordered regions

- **论文 ID：** `EVIW-A8926FF4DD7A845A`
- **期刊 / 来源：** Sci Rep
- **发表时间：** 2024 Jun 12
- **DOI：** [10.1038/s41598-024-64211-4](https://doi.org/10.1038/s41598-024-64211-4)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 IDBindT5：用 ProtT5 embeddings 加上 disorder annotation 训练轻量 FNN，对 IDPR 中的 binding residues 做单序列预测，并声称其效果与 ANCHOR2、DeepDISOBind 相当或更好、速度更快。

## 创新边界

`新意主要是把 pLM embedding 迁移到 IDPR binding residue prediction；它不是候选分子生成，也不是湿实验发现。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在 intrinsically disordered protein regions (IDPRs) 中逐残基预测 binding residues，并尽量摆脱 MSA、手工特征和复杂架构对该任务的依赖。

## 方法

- MobiDB/DisProt派生无序binding标签，ProtT5残基嵌入经FNN/CNN二分类。

## 数据与基准

- 去冗余训练/测试及CAID2-binding benchmark。

## 比较基线

- ANCHOR2、DeepDISOBind、homology/MSA和expert-feature方法。

## 结果证据

- balanced accuracy 57.2±3.6%，与ANCHOR2/DeepDISOBind在95%CI内无显著差异；总体难度仍高。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 数据少且注释不完整，性能接近随机以上但不高；binding type/partner信息有限。

## 仍未知

- 冻结证据未验证 GitHub 仓库中的代码、模型与论文描述是否完全一致。
- 未知该方法在更大、更多样或不同 disorder 标注体系的独立数据上是否保持同等泛化。
- 未知去掉 disorder 输入或更换 pLM 后，实际部署性能与速度会下降到什么程度。

## Pi 结构化证据摘录

- **baseline：** 随机基线按训练集中 positive 的频率工作，随机把 38.8% 的 disordered residues 标为 binding，用来提供最低参照。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.7]
- **baseline：** AAindex_disorder 用 566 个 AAindex1 特征替代蛋白嵌入，并沿用 CNN_disorder 结构，作为经典手工特征对照。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.7]
- **baseline：** 文中还把 ANCHOR2 和 DeepDISOBind 作为外部 SOTA 对照，在自建测试集和 CAID2 benchmark 上比较。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.4]；[doi:10.1038/s41598-024-64211-4, p.8]
- **data：** Mobi2k 训练集包含 1780 个蛋白，其中 697 个 positive、1083 个 negative；在 disorder 区域内共有 64,228 个 binding residues 与 101,381 个 non-binding residues。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.6]
- **data：** Mobi195 测试集包含 195 个蛋白，其中 80 个 positive、115 个 negative；对应 disorder 区域内有 6657 个 binding residues 与 11,644 个 non-binding residues。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.6]
- **data：** 作者还构建了 CAID2 binding benchmark（78 个蛋白、8209 个 binding residues）以及用于速度评估的 Mobi11k（11,114 个 human proteins，median length 489 residues）。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.6]；[doi:10.1038/s41598-024-64211-4, p.7]
- **declared_resources：** 论文声明 source code、datasets、trained models 和 detailed manual 都已公开在 GitHub 仓库 `https://github.com/jahnl/binding_in_disorder`。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.8]
- **declared_resources：** ProtT5 embeddings 可通过 `bio_embeddings` pipeline 或 ProtTrans GitHub notebook 生成，方便复现实验流程。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.8]
- **declared_resources：** disorder annotations 也可以由 LambdaPP predictions 替代，用于实际推理时的输入准备。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.8]
- **limitations：** 方法只能输出 binary binding / non-binding，不能区分 ligand 或 partner 类型；作者明确说 MobiDB API 未提供这些信息，因此无法训练多标签模型。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.5]
- **limitations：** 作者把评估限制在 disordered residues 上，因为 negatives 约占 93%、positives 约占 7%；否则类不平衡会偏向只分辨 ordered 与 disordered 的方法。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.5]；[doi:10.1038/s41598-024-64211-4, p.6]
- **limitations：** 若用 SETH 或 AlphaFold2-disorder 的预测 disorder 代替人工注释，性能仍可用但 recall 与 F1 会下降，说明模型对 disorder 输入质量有依赖。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.5]
- **limitations：** 测试集与 CAID2 benchmark 都较小，作者也承认在这种规模下，多数方法都难以在统计显著性上稳定超过 random baseline。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.3]；[doi:10.1038/s41598-024-64211-4, p.4]；[doi:10.1038/s41598-024-64211-4, p.6]
- **method：** 作者先从 MobiDB 只保留人工整理的 disorder 与 interaction 注释，再用 MMseqs2、UniqueProt 和 CD-HIT 逐步去冗余，构建训练、验证与测试集，以减少序列和结构泄漏。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.6]；[doi:10.1038/s41598-024-64211-4, p.7]
- **method：** 最终模型 IDBindT5 采用 ProtT5 的逐残基 embedding，再拼接一个二值 disorder 标记，输入单隐层 FNN；文中给出的最终配置约为 1025 个输入单元、612 个隐层单元和 1.7M 参数。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.7]
- **method：** 各 fold 的阈值按 ROC 曲线单独选择，五个 fold 模型再做平均形成 ensemble；性能估计使用 bootstrap，并用 Welch t-test 比较重叠置信区间的模型。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.7]；[doi:10.1038/s41598-024-64211-4, p.8]
- **results：** 在 Mobi195 上，IDBindT5 的 balanced accuracy 为 57.2 ± 3.6%，MCC 为 0.139 ± 0.07，precision 为 43.2 ± 1.9%，recall 为 58.7 ± 2.6%。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.6]
- **results：** 与 ANCHOR2 和 DeepDISOBind 相比，IDBindT5 在数值上通常最好，但多数差异未在 95% CI 下达到显著性；它相对 random baseline 则明确更好。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.3]；[doi:10.1038/s41598-024-64211-4, p.4]
- **results：** 当输入 disorder 改为 SETH 或 AlphaFold2-disorder 的预测结果时，除 recall 和 F1 明显下降外，其余指标大体仍落在原始置信区间内。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.5]；[doi:10.1038/s41598-024-64211-4, p.6]
- **results：** 在 Mobi11k 上，IDBindT5 的运行时间明显短于 DeepDISOBind；文中报告同机环境下 DeepDISOBind 需 33 小时 22 分，而 IDBindT5 需 2 小时 10 分，单蛋白 CPU 推理约 2 秒。
  - 证据：[doi:10.1038/s41598-024-64211-4, p.5]

## 页码证据

- [doi:10.1038/s41598-024-64211-4, p.1]
- [doi:10.1038/s41598-024-64211-4, p.2]
- [doi:10.1038/s41598-024-64211-4, p.5]
- [doi:10.1038/s41598-024-64211-4, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
