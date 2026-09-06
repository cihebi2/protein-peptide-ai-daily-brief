# AptaTrans: a deep neural network for predicting aptamer-protein interaction using pretrained encoders

- **论文 ID：** `EVIW-5B4F83FAF83C4EDF`
- **期刊 / 来源：** BMC Bioinformatics
- **发表时间：** 2023 Nov 27
- **DOI：** [10.1186/s12859-023-05577-6](https://doi.org/10.1186/s12859-023-05577-6)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称提出 AptaTrans：用 k-mer/FCS tokenization、双路 transformer encoder、interaction matrix 与 CNN 做 API 预测，并将其接入 Apta-MCTS、RNA Composer 和 ZDOCK 形成候选 aptamer 生成与评估流水线。

## 创新边界

`创新边界主要是组合式集成与预训练策略；论文未提供独立 prior-art 证据，因此不验证全球首创，只记录其方法边界。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在 SELEX 代价高、周期长且现有 in silico 方法常忽略 residue-structure level 交互的情况下，如何更准确地预测 aptamer-protein interaction，并进一步把预测结果用于候选 aptamer 的推荐与排序。

## 方法

- 分别用预训练编码器表示蛋白与适配体序列/结构特征，以深度网络预测交互，再由蒙特卡洛树搜索生成候选。[doi:10.1186/s12859-023-05577-6, p.1][doi:10.1186/s12859-023-05577-6, p.17]

## 数据与基准

- 使用 PDB 和 bpRNA 等来源构建 API 基准数据并在作者基准划分上验证。[doi:10.1186/s12859-023-05577-6, p.1][doi:10.1186/s12859-023-05577-6, p.18]

## 比较基线

- 与既有 API 计算方法和仅序列/不同预训练表示的消融比较。[doi:10.1186/s12859-023-05577-6, p.1]

## 结果证据

- 论文报告 AptaTrans 在其基准上提升交互分类，并展示与 Apta-MCTS 的候选生成集成；没有在本页证据中看到这些候选的直接结合实验。[doi:10.1186/s12859-023-05577-6, p.1][doi:10.1186/s12859-023-05577-6, p.17]

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 当前分数是交互分类而非定量亲和力；作者提出未来需用结合实验浓度把分数扩展到亲和力，并承认序列/二级结构之外因素未充分纳入。[doi:10.1186/s12859-023-05577-6, p.17]

## 仍未知

- AptaTrans 生成的新候选是否经过独立合成与结合实验，文中未充分披露。
- ZDOCK score 与真实亲和力之间的定量映射没有系统校准。
- 跨靶标泛化与外部独立 test set 的结果未充分报告。

## Pi 结构化证据摘录

- **baseline：** API 预测的外部基线是 PPAI 与 Li et al. 的 pseudo-amino-acid composition 模型。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.10]
- **baseline：** 内部基线包括未预训练的 AptaTrans、仅预训练单个 encoder、去掉 FCS mining、简化 encoder 和浅层 CNN。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.11]；[doi:10.1186/s12859-023-05577-6, p.12]
- **baseline：** 候选生成对照包括原始 Apta-MCTS 与 SELEX 已知 aptamers。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.13]；[doi:10.1186/s12859-023-05577-6, p.15]；[doi:10.1186/s12859-023-05577-6, p.16]
- **baseline：** 作者指出，既有 machine learning/API 方法多依赖序列特征，往往忽略 aptamer 与 protein 在 residue-structure level 的交互。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.2]；[doi:10.1186/s12859-023-05577-6, p.3]
- **data：** API benchmark 来自实验得到的 aptamer-protein complex 数据，包含 DNA/RNA；DNA 先用 T→U 转成 RNA，训练集为 580/1740，测试集为 145/435。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.3]；[doi:10.1186/s12859-023-05577-6, p.4]
- **data：** 预训练蛋白语料为 PDB 的 166,136 条序列，RNA 语料为 bpRNA-1m 的 79,890 条序列，并从 mmCIF/PDBx 与 DSSP 获取蛋白二级结构。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.4]
- **data：** 候选评估覆盖 6GOF、5UMO、2RH1、3SN6_4、3V79 和 5VOE_HL 六个蛋白，并对 GCPII/PS202 做额外对照。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.13]；[doi:10.1186/s12859-023-05577-6, p.15]；[doi:10.1186/s12859-023-05577-6, p.16]
- **declared_resources：** 预训练资源来自公开的 PDB 和 bpRNA-1m；蛋白二级结构由 mmCIF/PDBx 和 DSSP 生成。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.4]
- **declared_resources：** 候选评估和可视化依赖 RNA Composer、ZDOCK Server、PyMOL 与 MEME，另用 ELISA 评估 PS202。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.9]；[doi:10.1186/s12859-023-05577-6, p.14]；[doi:10.1186/s12859-023-05577-6, p.15]；[doi:10.1186/s12859-023-05577-6, p.16]
- **declared_resources：** 论文声明源代码与 benchmark dataset 公开在 GitHub: https://github.com/pnumlb/AptaTrans。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.1]；[doi:10.1186/s12859-023-05577-6, p.18]
- **limitations：** 作者明确承认，AptaTrans 生成的候选 aptamer 仍无法通过生物实验直接确认亲和力。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.17]
- **limitations：** 文中还指出温度、pH 和 ionic strength 等外部条件可能影响结合，但未纳入模型。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.17]
- **limitations：** ZDOCK、motif 与可视化更多是支持性证据，不能替代系统性的 wet-lab 验证。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.16]；[doi:10.1186/s12859-023-05577-6, p.17]
- **method：** RNA aptamer 采用 3-mer，protein 采用 FCS mining 分词；两路序列分别进入 transformer encoder，随后用嵌入向量点积构造 interaction matrix。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.4]；[doi:10.1186/s12859-023-05577-6, p.5]；[doi:10.1186/s12859-023-05577-6, p.6]
- **method：** 编码器预训练使用 masked token prediction 与 secondary structure prediction，两类预训练语料分别来自 PDB 蛋白序列和 bpRNA-1m RNA 序列及其结构标注。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.4]；[doi:10.1186/s12859-023-05577-6, p.7]；[doi:10.1186/s12859-023-05577-6, p.8]
- **method：** 主模型在 interaction matrix 上堆叠多层 convolution blocks、BatchNorm 和 GELU，再接 fully connected layer 输出 binding score。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.6]；[doi:10.1186/s12859-023-05577-6, p.7]
- **method：** 训练时做了对称序列增强，把 aptamer 的 symmetric sequence 视作同一分子以扩大训练集。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.8]
- **method：** 实验使用 6-layer transformer encoder、8 heads、128-dim embedding、512 hidden dimension 和 AdamW (1e-5) 训练。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.8]
- **results：** 在 API 分类上，AptaTrans 在 ROC-AUC、ACC、MCC、Sn、Sp、F1 六项指标都优于 PPAI 和 Li et al. 模型；文中报告 ROC-AUC 分别提升约 4.2% 和 15.4%。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.10]
- **results：** 预训练消融显示，双 encoder 都预训练时最好（ROC-AUC 0.921、ACC 0.876、MCC 0.679、F1 0.761），说明 self-supervised pretraining 带来稳定增益。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.11]
- **results：** 结构消融显示，去掉 FCS mining、使用 simple Encoders 或 shallow CNN 都会降分，其中 shallow CNN 的 ROC-AUC 降到 0.832。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.12]
- **results：** 候选推荐结果显示，AptaTrans pipeline 在多个目标蛋白上的 ZDOCK 评分高于原始 Apta-MCTS 和 known aptamers；作者还用 PyMOL 与 MEME 观察到相似 binding site 和 motif。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.13]；[doi:10.1186/s12859-023-05577-6, p.14]；[doi:10.1186/s12859-023-05577-6, p.15]
- **results：** 在 GCPII/PS202 对照里，PS202 的 ELISA 仍显示浓度相关结合增强，而 AptaTrans 候选的 ZDOCK 分数与其接近，支持该流程可产出接近已知 SELEX aptamer 的候选。
  - 证据：[doi:10.1186/s12859-023-05577-6, p.16]

## 页码证据

- [doi:10.1186/s12859-023-05577-6, p.1]
- [doi:10.1186/s12859-023-05577-6, p.17]
- [doi:10.1186/s12859-023-05577-6, p.18]
- [doi:10.1186/s12859-023-05577-6, p.1]
- [doi:10.1186/s12859-023-05577-6, p.18]
- [doi:10.1186/s12859-023-05577-6, p.1]
- [doi:10.1186/s12859-023-05577-6, p.18]
- [doi:10.1186/s12859-023-05577-6, p.1]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
