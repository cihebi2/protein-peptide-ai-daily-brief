# Artificial intelligence for prediction of biological activities and generation of molecular hits using stereochemical information

- **论文 ID：** `EVIW-7B1AD73D6D7BD5FE`
- **期刊 / 来源：** J Comput Aided Mol Des
- **发表时间：** 2023 Oct 17
- **DOI：** [10.1007/s10822-023-00539-9](https://doi.org/10.1007/s10822-023-00539-9)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者宣称提出一个由生成器、带 attention 的生物活性 Predictor 和深度强化学习组成的 de novo 生成框架，可面向 USP7 生成候选抑制剂，并通过自适应多目标优化、立体异构体枚举与 docking 给出更可解释的分子 hits。[doi:10.1007/s10822-023-00539-9, p.1][doi:10.1007/s10822-023-00539-9, p.14]

## 创新边界

`新意主要在于把 SMILES-based Predictor、attention、REINFORCE 生成和自适应权重的 pIC50/SAS 优化连成一体；但这份冻结证据并不能独立证明其全球首创性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

论文试图解决的是：在 USP7 这一与癌症相关的靶点上，如何用计算方法同时生成可合成、具较高生物活性、并保留立体化学信息的分子 hit，同时还能指出哪些子结构最可能参与结合。[doi:10.1007/s10822-023-00539-9, p.1][doi:10.1007/s10822-023-00539-9, p.2]

## 方法

- 以SMILES学习pIC50回归器，将预测亲和力和立体化学/合成奖励用于RNN生成器强化学习。

## 数据与基准

- ChEMBL预训练分子及有限USP7活性数据。

## 比较基线

- 无attention RNN、常规SMILES生成与不同奖励设置。

## 结果证据

- 论文报告生成具有高预测亲和力、可合成性和优选立体构型的候选；没有合成或USP7实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- USP7标签稀缺，代理pIC50和立体构型评分可能被生成器利用；无湿实验。

## 仍未知

- 是否能迁移到其他靶点或更小的数据场景仍未知。
- 候选分子在真实合成、体内外活性与毒性层面的表现未知。
- 数据增强带来的噪声是否会显著影响泛化稳定性仍未知。

## Pi 结构化证据摘录

- **baseline：** 生成器与 ORGAN、VAE、AAE、Graph MCTS、SMILES LSTM 等方法做了对比，作者据此声称其结果具有竞争力。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.7]
- **baseline：** Predictor 也对比了 ECFP4、ECFP6、RDKFingerprint 的 FCNN 以及多种 SMILES-RNN 结构，attention 版本整体优于无 attention 版本。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.4]；[doi:10.1007/s10822-023-00539-9, p.8]；[doi:10.1007/s10822-023-00539-9, p.9]
- **data：** Generator 预训练数据来自 ChEMBL22；作者先筛掉无法解析或标准化的分子，并限制分子量在 200–600 g/mol、logP 在 -2 到 6 之间。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.3]
- **data：** Predictor 的最终数据集包含 1453 个分子，作者通过加入与 USP7 catalytic domain 相似的其他靶点数据来扩增样本。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.4]
- **data：** 评估时，作者生成了 10,000 个分子用于 unbiased Generator 统计，并额外比较了 200 个优化前后的样本。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.7]；[doi:10.1007/s10822-023-00539-9, p.10]
- **data：** 对接部分使用 USP7 的 5NGF 结构，分辨率为 2.33 Å，作者删除了 chain B、配体、1,2-ethanediol 和水分子后保留 chain A 作为 receptor。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.7]
- **declared_resources：** 作者在文中声明 data 和 source code 可从 GitHub 获取。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.15]
- **declared_resources：** 研究还明确使用了 ChEMBL22、RDKit、Guacamol 和 MOE v.2022.02 等现成资源。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.3]；[doi:10.1007/s10822-023-00539-9, p.7]；[doi:10.1007/s10822-023-00539-9, p.15]
- **limitations：** 作者明确指出，USP7 已报道抑制剂数量有限，因此 Predictor 的训练样本偏少，泛化能力仍受约束。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.14]
- **limitations：** 作者也承认，使用与 USP7 相似靶点做 augmentation 可能把含糊或可疑信息带入模型。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.14]
- **method：** Generator 先用来自 ChEMBL22 的 1,179,477 条 SMILES 预训练，输入经过 tokenization、padding、embedding，再由两层 LSTM 预测下一个 token。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.3]；[doi:10.1007/s10822-023-00539-9, p.4]
- **method：** Predictor 比较了 ECFP4、ECFP6、RDKFingerprint 与多种 SMILES-RNN 结构；作者最终采用 SMILES + bidirectional GRU + attention 的配置，并用五折交叉验证与 hold-out set 评估。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.4]；[doi:10.1007/s10822-023-00539-9, p.8]；[doi:10.1007/s10822-023-00539-9, p.9]
- **method：** 在 RL 阶段，Generator 通过 REINFORCE 接收 Predictor 的 reward，把最大化 pIC50 与最小化 SAS 合并为单一的自适应加权目标。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.5]；[doi:10.1007/s10822-023-00539-9, p.6]
- **method：** 作者对候选分子使用 MOE 在 USP7 晶体结构 5NGF 的催化域上做 docking，生成 30 个 poses，并以 GBVI/WSA dG 进行打分与刚性受体精修。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.7]
- **results：** 作者报告 unbiased Generator 的 validity 为 0.966、uniqueness 为 0.984、novelty 为 0.982；biased Generator 则把 pIC50 提升到 6.35±0.41，并把 SAS 降到 2.03±0.26。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.7]；[doi:10.1007/s10822-023-00539-9, p.10]
- **results：** Predictor 的配置 I（SMILES + bidirectional GRU + attention）在 MSE、Q2、RMSE 和 CCC 上最好，且明显优于 fingerprint-based 模型和无 attention 变体。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.8]；[doi:10.1007/s10822-023-00539-9, p.9]
- **results：** 作者报告部分生成分子的 docking score 可接近晶体配体，并与 Gln297、Asp295、Arg408、Phe409 等关键残基形成氢键或 polar hydrogen-pi 相互作用。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.12]；[doi:10.1007/s10822-023-00539-9, p.13]
- **results：** attention 热点与 docking 中识别出的 hydrazine 和 amide 片段一致，作者据此主张模型对关键相互作用区域具有一定解释性。
  - 证据：[doi:10.1007/s10822-023-00539-9, p.11]；[doi:10.1007/s10822-023-00539-9, p.13]

## 页码证据

- [doi:10.1007/s10822-023-00539-9, p.14]
- [doi:10.1007/s10822-023-00539-9, p.1]
- [doi:10.1007/s10822-023-00539-9, p.4]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
