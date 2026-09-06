# ChemMORT: an automatic ADMET optimization platform using deep learning and multi-objective particle swarm optimization

- **论文 ID：** `EVIW-E513F4FA4C3C0EAA`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2024 Feb 20
- **DOI：** [10.1093/bib/bbae008](https://doi.org/10.1093/bib/bbae008)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 ChemMORT，一个可公开使用的 ADMET 优化平台，结合 SMILES Encoder、Descriptor Decoder 和 Molecular Optimizer，实现多端点优化与逆向 QSAR 式分子设计。

## 创新边界

`主要创新更偏向平台级整合与工程化落地，而不是提出全新的基础生成算法。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在巨大化学空间中，如何在不明显损失活性前提下同时优化多个 ADMET 端点。

## 方法

- 多ADMET models、particle swarm和chemical validity constraints。

## 数据与基准

- ADMET benchmarks/optimization cases。

## 比较基线

- single-objective/other optimizers。

## 结果证据

- 论文报告Pareto molecules；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- predictor bias/合成/实验未知。

## 仍未知

- 是否有独立外部测试集验证 ADMET 模型未说明
- 论文声明的 GitHub 仓库内容与可运行状态未在本 job 中核查
- 优化分子是否经过湿实验验证未见

## Pi 结构化证据摘录

- **baseline：** 论文的主要对照起点是 Olaparib，作者给出其 IC50 为 0.9 nmol，但 logS 仅为 −3.8。
  - 证据：[doi:10.1093/bib/bbae008, p.5]
- **baseline：** 优化结果以 Olaparib 和其他 approved PARP1 drugs 的结构相似性作为合理性参照，而不是与独立外部生成方法做系统 head-to-head 比较。
  - 证据：[doi:10.1093/bib/bbae008, p.7]；[doi:10.1093/bib/bbae008, p.8]
- **baseline：** 预测模型部分主要报告自身 CV/test 指标，正文未给出与其他 ADMET 预测框架并列的完整 benchmark 表。
  - 证据：[doi:10.1093/bib/bbae008, p.5]；[doi:10.1093/bib/bbae008, p.6]
- **data：** SMILES 翻译模型使用内部数据库中的 1.7 million accessible molecules，按 9:1 划分为 1.53 million 训练集和 0.17 million 测试集，每个分子用 10 种 enumerated SMILES 表示。
  - 证据：[doi:10.1093/bib/bbae008, p.2]
- **data：** ADMET 数据集约 30,000 条，来源于 ChEMBL、EPA 和 DrugBank，覆盖 logD7.4、LogS、Caco-2、MDCK、PPB、AMES、hERG、hepatoxicity 和 LD50。
  - 证据：[doi:10.1093/bib/bbae008, p.2]
- **data：** ADMET 模型训练时按 ChemSAR 的 Diverse training set split 以 75%/25% 划分训练与测试；Caco-2 和 MDCK 还使用了 data augment。
  - 证据：[doi:10.1093/bib/bbae008, p.4]；[doi:10.1093/bib/bbae008, p.6]
- **data：** 案例优化以 Olaparib 为起始分子，并把 solubility、QED、SA、similarity 以及 bioactivity motif 作为主要目标或约束。
  - 证据：[doi:10.1093/bib/bbae008, p.5]；[doi:10.1093/bib/bbae008, p.7]
- **declared_resources：** 公开平台地址为 https://cadd.nscc-tj.cn/deploy/chemmort/，Data Availability 还给出 GitHub 地址 https://github.com/antwiser/ChemMORT。
  - 证据：[doi:10.1093/bib/bbae008, p.1]；[doi:10.1093/bib/bbae008, p.9]
- **declared_resources：** 实现栈包括 Python 3.7、Django 2.2、TensorFlow 1.14.0、SQLite 3、celery 4.4.7、RabbitMQ 3.6.10、RDKit 2019.03.1、Ubuntu 18.04.4 LTS、Nginx 和 uWSGI。
  - 证据：[doi:10.1093/bib/bbae008, p.3]
- **declared_resources：** MD 和 docking 部分使用 AMBER ff19SB、GAFF2、AutoDock Vina 1.2.0 和 AmberTools2023。
  - 证据：[doi:10.1093/bib/bbae008, p.5]；[doi:10.1093/bib/bbae008, p.10]
- **declared_resources：** ADMET 数据来源包括 ChEMBL、EPA、DrugBank，模型构建还引用了 ChemSAR 的 Diverse training set split。
  - 证据：[doi:10.1093/bib/bbae008, p.2]；[doi:10.1093/bib/bbae008, p.4]
- **limitations：** 文中明确提示，任意 latent 向量组合可能产生 invalid or failed molecules，说明可逆表示并非总能映射回有效结构。
  - 证据：[doi:10.1093/bib/bbae008, p.4]
- **limitations：** 作者只用 PARP-1 inhibitor 的受限多目标优化作为案例来展示 utility，证据范围仍偏单一任务。
  - 证据：[doi:10.1093/bib/bbae008, p.1]；[doi:10.1093/bib/bbae008, p.5]；[doi:10.1093/bib/bbae008, p.8]
- **limitations：** 文中也指出，若缺少 similarity 与 substructure constraints，优化容易牺牲 bioactivity，因此平台对用户设定的约束权重依赖较强。
  - 证据：[doi:10.1093/bib/bbae008, p.4]；[doi:10.1093/bib/bbae008, p.5]
- **method：** ChemMORT 以 seq2seq 的 SMILES 编码-解码网络学习分子表示，编码器和解码器都采用三层 GRU，并通过 512 维信息瓶颈层输出 latent representation。
  - 证据：[doi:10.1093/bib/bbae008, p.2]
- **method：** Molecular Optimizer 将 reversible molecular representation、similarity constraint、substructure constraint 与 multi-objective PSO 结合，用于逆向 QSAR 式优化。
  - 证据：[doi:10.1093/bib/bbae008, p.3]；[doi:10.1093/bib/bbae008, p.4]
- **method：** ADMET 预测部分基于编码器得到的 512 维向量，使用 XGBoost 构建 9 个 ADMET/理化性质模型。
  - 证据：[doi:10.1093/bib/bbae008, p.2]；[doi:10.1093/bib/bbae008, p.6]
- **method：** Web 端实现采用 Python 3.7、Django 2.2、TensorFlow 1.14.0、SQLite 3、celery、RabbitMQ 和 RDKit，并部署在 Ubuntu 18.04.4 LTS 的 Nginx/uWSGI 环境上。
  - 证据：[doi:10.1093/bib/bbae008, p.3]
- **results：** 翻译模型训练到收敛后，训练集和测试集的平均单字符准确率都达到 99.8%。
  - 证据：[doi:10.1093/bib/bbae008, p.4]
- **results：** 9 个 ADMET 模型在 5-fold CV 与测试集上整体表现稳定；回归模型平均 RMSE/R2 为 0.442/0.747（CV）和 0.437/0.752（test），分类模型平均 Accuracy/AUC 为 0.763/0.836（CV）和 0.780/0.846（test）。
  - 证据：[doi:10.1093/bib/bbae008, p.5]；[doi:10.1093/bib/bbae008, p.6]
- **results：** 在 Olaparib 优化案例中，100 次任务共得到 171 个 unique optimized molecules，且 LogS、final score 和部分 docking scores 相比初始分子有所改善。
  - 证据：[doi:10.1093/bib/bbae008, p.5]；[doi:10.1093/bib/bbae008, p.7]
- **results：** MD simulation 显示 20 ns 内复合物整体稳定，MM/GBSA 结果也表明若干优化分子的结合自由能接近 Olaparib。
  - 证据：[doi:10.1093/bib/bbae008, p.5]；[doi:10.1093/bib/bbae008, p.8]

## 页码证据

- [doi:10.1093/bib/bbae008, p.1]
- [doi:10.1093/bib/bbae008, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
