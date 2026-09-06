# DG-Affinity: predicting antigen-antibody affinity with language models from sequences

- **论文 ID：** `EVIW-E342A47CFC993CA7`
- **期刊 / 来源：** BMC Bioinformatics
- **发表时间：** 2023 Nov 13
- **DOI：** [10.1186/s12859-023-05562-z](https://doi.org/10.1186/s12859-023-05562-z)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称提出了一个 sequence-based 的亲和力预测框架 DG-Affinity：先用 TAPE 生成 antigen 表征、用 AbLang 生成 antibody 表征，再结合 ConvNeXt 做回归；在独立测试集上优于所列结构基线和传统工具，并可作为抗体设计辅助打分器。

## 创新边界

`创新边界主要是序列级亲和力回归与表征融合，不涉及候选抗体/抗原的生成、优化或湿实验筛选。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在仅有 antigen 和 antibody 序列、缺少复合物结构信息的情况下，如何更准确地预测 antigen–antibody binding affinity，用于支持抗体筛选与设计。

## 方法

- 分别生成抗原/抗体序列嵌入，拼接后输入 tiny ConvNeXt 与 MLP 回归头，并比较多种 CNN/Transformer 骨干。[doi:10.1186/s12859-023-05562-z, p.1][doi:10.1186/s12859-023-05562-z, p.5][doi:10.1186/s12859-023-05562-z, p.7]

## 数据与基准

- 由公开实验亲和力数据库整理抗原-抗体对，并设置独立测试集。[doi:10.1186/s12859-023-05562-z, p.2]

## 比较基线

- 结构型亲和力方法、序列工具及 12 种常见 CNN/Transformer 骨干。[doi:10.1186/s12859-023-05562-z, p.1][doi:10.1186/s12859-023-05562-z, p.7]

## 结果证据

- 独立测试集 Pearson 相关超过 0.65，论文称优于所比较结构型和序列型方法。[doi:10.1186/s12859-023-05562-z, p.1]

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 序列相似性、抗原家族和抗体克隆型切分若不严格可能抬高相关；相关系数不能保证绝对亲和力误差或未见抗原外推。[doi:10.1186/s12859-023-05562-z, p.9]

## 仍未知

- DG-Affinity 是否存在独立公开源码仓库，正文没有给出明确 URL。
- 独立测试集仅覆盖单链复合物，能否外推到多链或更复杂体系未知。
- 不同基线的输入预处理、版本差异与在线服务可用性是否完全一致未知。
- 论文中未见前瞻性 wet-lab 验证，实际实验可用性仍未知。

## Pi 结构化证据摘录

- **baseline：** 对比对象包括结构基线 CSM-AB、AREA-AFFINITY，以及 LISA、CIPS、PRODIGY、NIS、CCharPPI 等常用 protein-protein affinity 工具。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.6]
- **baseline：** CSM-AB 被作者描述为面向 antibody-antigen docking 和 binding affinity prediction 的 graph-based scoring function；AREA-AFFINITY 则整合了多种 area-based affinity models。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.6]
- **baseline：** LISA、CIPS、PRODIGY、NIS 和 CCharPPI 分别依赖 local interaction、contact preference、atom-atom contacts、surface physicochemical properties 与 composite descriptors 等结构信息。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.6]
- **data：** benchmark 数据集来自 sdAb-DB 和 Baidu PaddlePaddle 2021 Global Antibody Affinity Prediction Competition 的 Round A 数据，去除共享的 antibody–antigen interactions 后得到 1,673 条记录、448 个 distinct complexes。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.3]
- **data：** 作者将数据分成五等份做五折交叉验证，并使用来自 antibody_benchmark 的独立测试集；其中原始 42 个复合物里仅保留 antibody 和 antigen 都是单链的 26 个样本。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.3]
- **data：** 原始 kd 先按文中方法做负对数变换并归一化，使标签大致落到 0–1 区间，少量异常值会落在 1 之外。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.3]
- **declared_resources：** 作者提供了 DG-Affinity 的网页服务，地址为 https://www.digitalgeneai.tech/solution/affinity。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.1]；[doi:10.1186/s12859-023-05562-z, p.10]
- **declared_resources：** 实现层面使用了公开的 ConvNeXt 代码、PyTorch 和 Adam，并将 ConvNeXt tiny 作为默认 backbone。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.5]
- **declared_resources：** 表征层面依赖 TAPE 与 AbLang 两个预训练语言模型，分别服务于 antigen 与 antibody 序列嵌入。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.4]
- **limitations：** 作者明确指出，现有结构基方法往往需要 antigen-antibody complex structure，而这类结构信息难以获得，因此是 sequence-based 方法试图缓解的核心约束。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.2]；[doi:10.1186/s12859-023-05562-z, p.9]
- **limitations：** 作者也承认独立测试集不够大且样本不平衡，这会影响结果解释，并可能放大个别特征分支的表观收益。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.8]
- **limitations：** 基线比较部分依赖在线 webserver 和手工计算指标，说明复现时需要处理不同工具的输入与输出流程。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.6]
- **method：** DG-Affinity 采用 TAPE 为 antigen 序列生成 embedding，并用 AbLang 为 antibody 序列生成 embedding，再把两类表征送入后续网络学习亲和力回归。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.4]；[doi:10.1186/s12859-023-05562-z, p.5]
- **method：** 模型主体由三个并行的 ConvNeXt backbone 组成，分别处理 antibody 特征、antigen 特征和 antibody–antigen 拼接特征；随后将表征做 element-wise multiplication、concat，再经 MLP 输出回归值。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.5]
- **method：** 训练实现使用 PyTorch，作者选择 ConvNeXt tiny 版本，训练 50 epochs，learning rate 为 0.000001，并使用 Adam optimizer。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.5]
- **method：** 评估指标采用 Pearson correlation coefficient (R)、R2、RMSD 和 MAE；对结构基线则通过在线网站预测后手工汇总这些指标。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.6]
- **results：** 在独立测试集上，DG-Affinity 的 Pearson R 超过 0.6556，作者报告其在所有对比方法中表现最好。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.7]
- **results：** 相较基线，DG-Affinity 在训练集与独立集的多项指标上都更优；文中还指出部分基线出现负相关，例如 CP_PIE 和 AREA-AFFINITY。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.7]
- **results：** 在替换 backbone 的对比中，ConvNeXt 在 13 种网络里整体表现最好，尤其在五折交叉验证和独立测试集上更占优。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.7]；[doi:10.1186/s12859-023-05562-z, p.8]
- **results：** 消融实验显示，去掉 antigen 特征分支对性能影响最大；作者也观察到 full feature 在独立集上优于五折结果，可能与独立集规模较小且样本不平衡有关。
  - 证据：[doi:10.1186/s12859-023-05562-z, p.8]

## 页码证据

- [doi:10.1186/s12859-023-05562-z, p.1]
- [doi:10.1186/s12859-023-05562-z, p.7]
- [doi:10.1186/s12859-023-05562-z, p.1]
- [doi:10.1186/s12859-023-05562-z, p.2]
- [doi:10.1186/s12859-023-05562-z, p.5]
- [doi:10.1186/s12859-023-05562-z, p.7]
- [doi:10.1186/s12859-023-05562-z, p.9]
- [doi:10.1186/s12859-023-05562-z, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
