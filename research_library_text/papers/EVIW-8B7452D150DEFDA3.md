# iMFP-LG: Identify Novel Multi-functional Peptides Using Protein Language Models and Graph-based Deep Learning

- **论文 ID：** `EVIW-8B7452D150DEFDA3`
- **期刊 / 来源：** Genomics Proteomics Bioinformatics
- **发表时间：** 2024 Nov 25
- **DOI：** [10.1093/gpbjnl/qzae084](https://doi.org/10.1093/gpbjnl/qzae084)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `语言模型` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 iMFP-LG，把 protein language model 与 graph attention network 结合，将多标签多功能 peptide 识别转换为图节点分类，并进一步用于从 UniRef90 中筛选候选新 peptide，最终给出实验验证。

## 创新边界

`论文自述其为首个显式建模功能标签关联的 multi-functional peptide 识别框架；此处仅确认论文内的自我新颖性陈述，未做独立 prior-art 复核。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在多功能 peptide 标注稀缺、类别极不平衡且功能关联复杂的条件下，如何更准确地识别并筛选具有多个功能的 peptide。

## 方法

- 序列PLM+图表示多标签分类。

## 数据与基准

- 多功能peptide datasets与UniRef90 millions。

## 比较基线

- PrMFTP、ETFC等。

## 结果证据

- 8候选中1条通过结构对齐和实验验证同时抗菌/抗癌。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 小类别区分弱，实验仅1条。

## 仍未知

- UniRef90_P82904 之外的其余 7 条候选 peptide 的真实功能机制尚不清楚。
- 论文未给出完整的外部独立复现结果，只提供了文内比较和作者复现实验。
- 代码链接已在文中声明，但我未实际打开仓库核验实现细节。

## Pi 结构化证据摘录

- **baseline：** 论文比较了 CLR、RAKEL、RBRL、MLDF 等传统多标签方法，以及 MPMABP、MLBP、PrMFTP、ETFC 等深度学习基线。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.3]；[doi:10.1093/gpbjnl/qzae084, p.4]
- **baseline：** 作者还在 feature extraction 层面对 AAC、PAAC、DP、CTDD、CNN、RNN、CNN-BiLSTM 和 TAPE 等方案做了对照，以验证 pLM 与 GAT 的增益。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.2]；[doi:10.1093/gpbjnl/qzae084, p.3]
- **baseline：** 对于未公开训练集或无法复现的基线，作者采用文献报告结果；可复现的深度学习方法则在同一训练集上重新训练后比较。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.3]
- **data：** MFBP 数据集来自 2020 年检索 bioactive peptides，共 5986 条 peptide、5 类功能，并用 CD-HIT 去冗余后按 80/20 划分训练和测试集。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.8]；[doi:10.1093/gpbjnl/qzae084, p.9]
- **data：** MFTP 数据集来自 2021 年检索 therapeutic peptides，清洗后保留 9874 条 peptide 和 21 类功能，过滤了非标准氨基酸、长度异常样本以及少样本类别。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.9]
- **data：** 作者还从 UniRef90 的 166,459,614 条蛋白序列中筛出 1,077,593 条 peptide 作为候选库，并以 0.95 阈值筛选 ACP/AMP 候选。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.8]
- **declared_resources：** 论文在第 12 页给出 GitHub 与 BioCode 两个代码入口，说明实现可公开获取。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.12]
- **declared_resources：** 训练与推理在配备 Intel Xeon Gold 6248R CPU 和 NVIDIA A100 GPU 的服务器上完成，软件框架为 PyTorch 1.12。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.11]
- **declared_resources：** 湿实验资源包括 solid-phase peptide synthesis、mass spectrometry、HPLC，以及针对细菌和肿瘤细胞的 OD600/MTT 测定。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.11]
- **limitations：** 作者明确指出，数据集标注只覆盖已发表实验结果，部分 peptide 可能仍有未揭示功能，因此标签并不完备。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.9]
- **limitations：** 论文也承认，预测到的候选功能仍需要进一步实验验证，且未来计划融合结构信息、功能相关特征和理化性质。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.8]；[doi:10.1093/gpbjnl/qzae084, p.11]
- **method：** iMFP-LG 先用预训练 TAPE 提取 peptide 的 768 维表示，再通过节点特征编码器把同一表示映射到不同功能标签节点上。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.9]；[doi:10.1093/gpbjnl/qzae084, p.10]
- **method：** 图分类模块使用 2 层 fully connected graph 的 GAT，每层 6 个 attention heads，用于学习不同 peptide 功能标签之间的关联。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.10]；[doi:10.1093/gpbjnl/qzae084, p.11]
- **method：** 训练过程中引入 FGM adversarial training，并用 binary cross-entropy 计算多标签损失，以增强鲁棒性和泛化能力。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.10]；[doi:10.1093/gpbjnl/qzae084, p.11]
- **results：** 在 MFBP 上，iMFP-LG 的 precision/coverage/accuracy/absolute true/absolute false 分别为 0.797/0.803/0.796/0.788/0.078，整体优于最强对照 MLBP。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.4]
- **results：** 在 MFTP 上，iMFP-LG 的五项指标为 0.730/0.730/0.689/0.616/0.032，优于 ETFC 等对照，且 absolute false 基本持平。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.4]
- **results：** 作者报告 iMFP-LG 对小类别和多功能类别更敏感，尤其在 ACP、ADP、AIP、AMP 以及 ACP_AMP、ADP_AIP 等组合上表现更好。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.5]；[doi:10.1093/gpbjnl/qzae084, p.6]
- **results：** 从 UniRef90 筛出 8 条候选 peptide 后，UniRef90_P82904 经过细菌抑制与肿瘤细胞活性实验验证，表现出双重 anti-bacterial 和 anti-cancer 活性。
  - 证据：[doi:10.1093/gpbjnl/qzae084, p.8]

## 页码证据

- [doi:10.1093/gpbjnl/qzae084, p.1]
- [doi:10.1093/gpbjnl/qzae084, p.5]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
