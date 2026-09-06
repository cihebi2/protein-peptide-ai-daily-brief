# DTGHAT: multi-molecule heterogeneous graph transformer based on multi-molecule graph for drug-target identification

- **论文 ID：** `EVIW-D7E7DD745CE6E5FC`
- **期刊 / 来源：** Frontiers in Pharmacology（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.3389/fphar.2025.1596216](https://doi.org/10.3389/fphar.2025.1596216)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 DTGHAT，把 15 个异构生物网络、graph attention / transformer、多尺度特征融合和先验属性整合为端到端的 drug-target 识别框架。

## 创新边界

`增量主要在多视图异构图 + GAT + 融合 + 先验属性的组合式设计；冻结证据不足以证明其全球新颖性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在多源生物分子关系中准确预测 drug-target interactions，并尽量缓解 cold-start 实体的识别困难。

## 方法

- 15网络构异构图，attention transformer聚合meta-relations并链接预测。

## 数据与基准

- 公开DTI/chemical/genomic/phenotypic/cellular网络，5折80/10/10。

## 比较基线

- 网络embedding/GNN DTI方法。

## 结果证据

- AUC 0.9634，至少比SOTA高4%；随机边拆分可能抬高性能。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 依赖已知网络，真正新entity cold-start和实验验证不足。

## 仍未知

- 公开仓库内容、许可和可复现性未在本次冻结证据中核验。
- 负样本随机采样的偏差控制与随机种子设置未充分展开。
- 参数选择叙述在正文与表格间存在不一致，最优超参结论需谨慎解读。

## Pi 结构化证据摘录

- **baseline：** 作者将 DTGHAT 与 DeepDTA、GCN-DTI、GraphDTA 比较，报告本方法在 AUC 和 AUPR 上均更高。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.5]；[doi:10.3389/fphar.2025.1596216, p.6]
- **baseline：** 相较于 matrix factorization-based 方法和 weighted nearest-neighbor similarity 模型，作者声称 DTGHAT 的表现更优，而这些基线的 AUC 处于 mid-0.8s。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.3]
- **baseline：** 文中还提到一个 simpler GCN without multi-view attention 约为 0.90 AUC，说明多视图注意力和融合模块带来额外增益。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.3]；[doi:10.3389/fphar.2025.1596216, p.4]
- **data：** 训练与测试数据来自 DrugBank、ChEMBL，并补充 BindingDB、STITCH 与 TargetNet 以扩大 drug-target 覆盖度。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.6]；[doi:10.3389/fphar.2025.1596216, p.7]
- **data：** 图构建还使用 Morgan fingerprints、BLAST 相似性和 UniProt 蛋白序列特征来表示 drug 与 protein 节点。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.6]；[doi:10.3389/fphar.2025.1596216, p.7]
- **data：** 负样本通过随机选择 non-interacting drug-target pairs 生成，数据按 80%/10%/10% 划分为训练、验证和测试集。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.3]；[doi:10.3389/fphar.2025.1596216, p.7]
- **declared_resources：** 论文正文明确声明代码免费公开，仓库地址为 https://github.com/stella-007/DTGHAT.git。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.1]
- **declared_resources：** 作者声明数据可在 online repositories 与 supplementary material 中获取，正文也指出数据来源包括 DrugBank、ChEMBL 等。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.6]；[doi:10.3389/fphar.2025.1596216, p.8]
- **declared_resources：** 论文声明获得 Hunan Provincial Science and Technology Innovation 与 Hunan Provincial Natural Science Foundation of China 的资助。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.8]
- **limitations：** 作者自己显示，去掉 prior attributes 后 cold-start 实体几乎接近随机，说明该框架对无已知交互的新实体仍较脆弱。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.4]
- **limitations：** 论文把 quantitative affinities、polypharmacology、temporal/condition-specific data 和 docking integration 列为 future work，表示当前版本仍主要是二分类 DTI 预测。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.6]
- **method：** DTGHAT 将 drugs、targets 及疾病等 biomolecules 组织为多视图 heterogeneous graph，并利用 15 类关系刻画 chemical、genomic、phenotypic 与 cellular 信息。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.1]；[doi:10.3389/fphar.2025.1596216, p.2]
- **method：** 模型在各个 view 上使用 graph attention / transformer 学习 topology-aware 表征，再通过 multi-scale feature fusion 聚合局部与全局上下文。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.3]；[doi:10.3389/fphar.2025.1596216, p.7]
- **method：** 作者把 drug 的 chemical descriptors 与 target 的 protein sequence embeddings 作为 prior knowledge，并与图表示拼接后送入 MLP 进行二分类预测。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.3]；[doi:10.3389/fphar.2025.1596216, p.7]
- **method：** 训练与评估采用 5-fold cross-validation，并在每折中使用 80%/10%/10% 的训练、验证和测试划分。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.3]；[doi:10.3389/fphar.2025.1596216, p.7]
- **results：** 在 5-fold cross-validation 中，DTGHAT 报告平均 AUC 0.9666±0.0102、AUPR 0.964±0.0097，accuracy 约 91%，MCC 0.8214±0.0366。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.4]；[doi:10.3389/fphar.2025.1596216, p.6]
- **results：** Ablation 显示，移除 graph attention 或 prior attributes 都会降性能，且在 cold-start 子集上去掉属性后 AUC 下降到约 0.5–0.6。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.4]
- **results：** Case study 在 DrugBank 外部文献支持下给出 acetaminophen-POLE、acetaminophen-MPO、benzydamine-MAPK 和 levodopa-EGFR 等候选。
  - 证据：[doi:10.3389/fphar.2025.1596216, p.6]

## 页码证据

- [doi:10.3389/fphar.2025.1596216, p.1]
- [doi:10.3389/fphar.2025.1596216, p.3]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
