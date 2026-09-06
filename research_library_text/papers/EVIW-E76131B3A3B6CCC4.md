# GraphMHC: Neoantigen prediction model applying the graph neural network to molecular structure

- **论文 ID：** `EVIW-E76131B3A3B6CCC4`
- **期刊 / 来源：** PLoS One
- **发表时间：** 2024 Mar 27
- **DOI：** [10.1371/journal.pone.0291223](https://doi.org/10.1371/journal.pone.0291223)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `图与几何学习`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者声称提出 GraphMHC：把 HLA/MHC 与 peptide 转成分子图，使用图神经网络和卷积层联合建模结合关系，并把预测结果用于 TCGA-SKCM 的临床分层。

## 创新边界

`可确认的是一套新的图式结合预测流程；作者“first”式全球首创主张未被本次冻结证据独立验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

论文要解决的是：仅依据 MHC/HLA 与 peptide 的内在序列与分子结构信息，预测二者结合与 neoantigen load，从而辅助免疫治疗预后判断。

## 方法

- pMHC结构/接触图消息传递分类。

## 数据与基准

- HLA-peptide binding/immunogenicity与neoantigen data。

## 比较基线

- NetMHCpan等。

## 结果证据

- 论文报告超过序列baselines；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 结构预测/allele覆盖、immunogenicity标签少。

## 仍未知

- 是否存在更早的同类图结构 MHC-peptide 预测工作，冻结证据中无法独立核实。
- GitHub 仓库与论文版本是否完全一致、是否可复现实验细节，冻结证据中无法确认。
- TCGA-SKCM 的临床分层结果是否能在独立队列稳定复现，文中未给出外部验证。
- class II 额外验证与 class I 结果之间的可迁移性边界仍不清楚。

## Pi 结构化证据摘录

- **baseline：** 作者以 NetMHCpan-4.1 作为主要 baseline，并在 class II extra-validation 中使用 NetMHCIIpan-4.0 进行对照。
  - 证据：[doi:10.1371/journal.pone.0291223, p.8]
- **baseline：** 还比较了更少层数的图/卷积结构（2 GNNs + 2 CNNs、4 GNNs），用于说明完整 GraphMHC 架构更优。
  - 证据：[doi:10.1371/journal.pone.0291223, p.8]；[doi:10.1371/journal.pone.0291223, p.9]
- **data：** 训练/测试数据来自 IEDB 的 human MHC class I 记录，原始 157,325 行中有 157,084 行完成转换；额外验证使用 IEDB 的 MHC class II 数据。
  - 证据：[doi:10.1371/journal.pone.0291223, p.3]；[doi:10.1371/journal.pone.0291223, p.5]；[doi:10.1371/journal.pone.0291223, p.8]
- **data：** 临床数据来自 TCGA-SKCM，共 310 名受试者；HLA 类型、ESTIMATE 分数与 Firehose/公开网站数据共同用于分组和生存分析。
  - 证据：[doi:10.1371/journal.pone.0291223, p.7]；[doi:10.1371/journal.pone.0291223, p.1]
- **declared_resources：** 论文声明数据均来自公开来源，且代码发布在 GitHub：GraphMHC。
  - 证据：[doi:10.1371/journal.pone.0291223, p.1]
- **declared_resources：** 实现与评估依赖 RDKit 2022.03.2、NetworkX 2.8.4、PyTorch Geometric 2.1.0、PyTorch 1.11.0+cu113、Scikit-learn 1.1.2，以及 RTX 3090 24GB GPU。
  - 证据：[doi:10.1371/journal.pone.0291223, p.5]；[doi:10.1371/journal.pone.0291223, p.6]；[doi:10.1371/journal.pone.0291223, p.7]
- **limitations：** 作者承认 IEDB 中的 MHC/peptide 结合与 HLA 多态性信息并不完整，且多步转换会引入不可避免的不确定性。
  - 证据：[doi:10.1371/journal.pone.0291223, p.11]
- **limitations：** 论文指出 NetMHCpan 所对应的 34-mer HLA 转换并非绝对可靠，而且 GNN 结构比字符串模型更占内存。
  - 证据：[doi:10.1371/journal.pone.0291223, p.11]
- **limitations：** 作者还说明本文未纳入额外外部数据或 TCR binding 建模；更广泛的免疫治疗预后仍受 neoantigen load 之外因素影响。
  - 证据：[doi:10.1371/journal.pone.0291223, p.12]
- **method：** 以 IEDB 的 human MHC class I 结合数据构建任务，按 IC50 ≤ 500 nM 视为 binding、> 500 nM 视为 non-binding，并划分 80%/20% 训练测试集。
  - 证据：[doi:10.1371/journal.pone.0291223, p.3]；[doi:10.1371/journal.pone.0291223, p.5]
- **method：** 将 HLA 与 peptide 序列经 NetMHCpan-4.1/ RDKit 转成 SMILES 与分子结构，再编码为图；节点使用 31 维特征、边使用 12 维特征。
  - 证据：[doi:10.1371/journal.pone.0291223, p.5]
- **method：** GraphMHC 采用 4 层 GAT、mean readout、2 层 Conv1D 与 skip connection，最后经 FC+sigmoid 分类；训练时使用 Adam、batch size 64、100 epochs。
  - 证据：[doi:10.1371/journal.pone.0291223, p.5]；[doi:10.1371/journal.pone.0291223, p.6]；[doi:10.1371/journal.pone.0291223, p.7]
- **method：** 临床应用部分把 TCGA-SKCM 的 MAF 依次转为 VCF、VEP 注释、筛选 missense 变异、用 customProDB 生成 9-mer，再与 HLA 一起预测 neoantigen load。
  - 证据：[doi:10.1371/journal.pone.0291223, p.7]
- **results：** 在 intra-validation 中，GraphMHC 的 AUC-ROC 为 0.922（0.919–0.925），优于 2 GNNs + 2 CNNs 的 0.872 和 4 GNNs 的 0.688。
  - 证据：[doi:10.1371/journal.pone.0291223, p.9]
- **results：** 与 NetMHCpan-4.1 相比，GraphMHC 在 inter-validation 中 AUC-ROC 与 sensitivity 更高，但 specificity 和 F1-score 更低。
  - 证据：[doi:10.1371/journal.pone.0291223, p.9]
- **results：** 在 TCGA-SKCM 上，GraphMHC 分组得到的 5 年生存差异为边界显著（p=0.061），且 stromal score 存在显著差异；NetMHCpan-4.1 未见显著性。
  - 证据：[doi:10.1371/journal.pone.0291223, p.9]；[doi:10.1371/journal.pone.0291223, p.10]
- **results：** 在 MHC class II extra-validation 中，GraphMHC 的 AUC-ROC 为 0.874，高于 NetMHCIIpan-4.0 的 0.834，sensitivity 更高，F1-score 相同。
  - 证据：[doi:10.1371/journal.pone.0291223, p.11]

## 页码证据

- [doi:10.1371/journal.pone.0291223, p.1]
- [doi:10.1371/journal.pone.0291223, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
