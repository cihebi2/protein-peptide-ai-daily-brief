# Benchmarking compound activity prediction for real-world drug discovery applications

- **论文 ID：** `EVIW-27BCEE46559B0DFA`
- **期刊 / 来源：** Commun Chem
- **发表时间：** 2024 Jun 4
- **DOI：** [10.1038/s42004-024-01204-4](https://doi.org/10.1038/s42004-024-01204-4)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 CARA 基准，并用 VS/LO 分类、new-protein/new-assay 划分和 per-assay 评测来系统比较多种活性预测模型与 few-shot 策略。

## 创新边界

`创新边界主要在 benchmark 与评测协议，不是新的候选生成算法。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在真实世界药物发现中，如何对稀疏、多来源、带偏置的 compound activity 数据进行更公平、贴近应用的基准评测。

## 方法

- temporal/scaffold/series splits与多模型评估。

## 数据与基准

- 实际drug discovery activity datasets。

## 比较基线

- fingerprint/ML/GNN/transformer。

## 结果证据

- 论文揭示随机split与real-world差距；为benchmark。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 仍受assay/项目特异和公开数据限制。

## 仍未知

- 补充材料中的全部分布图、任务规模和超参数细节未在冻结主文页中逐项展开。
- 代码仓库的当前可运行性与复现实验成本未在冻结页内直接验证。

## Pi 结构化证据摘录

- **baseline：** zero-shot 评测的代表性基线包括 DeepCPI、DeepDTA、GraphDTA、Tsubaki et al.、DeepConvDTI、MONN、TransformerCPI 和 MolTrans。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.7]；[doi:10.1038/s42004-024-01204-4, p.15]；[doi:10.1038/s42004-024-01204-4, p.16]
- **baseline：** few-shot 评测比较了 QSAR（RF、GBT、SVM、DNN）、pre-training/finetuning、re-training、MAML 以及 multi-task learning，并以 MTDNN 和 DeepConvDTI-c 等实现具体策略。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.7]；[doi:10.1038/s42004-024-01204-4, p.8]；[doi:10.1038/s42004-024-01204-4, p.16]
- **baseline：** 在有结构的 kinase 子集上，作者还把 AutoDock Vina、iDock 和 LeDock 作为 docking baseline，与 sequence-based 方法做对照。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.14]；[doi:10.1038/s42004-024-01204-4, p.17]
- **data：** CARA 主要来自 ChEMBL v30 的公开实验活性记录；文中给出的总量显示，VS 约有 1,237,256 个样本和 317,855 个唯一化合物，LO 约有 1,187,136 个样本和 625,099 个唯一化合物。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.4]
- **data：** 作者指出数据是稀疏的：平均每个化合物在 VS 中约测试 4 次、在 LO 中约测试 2 次，体现了典型的真实世界 assay 级别稀疏性。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.4]
- **data：** CARA 的 test assays 通过蛋白聚类选取，要求样本充足、标签范围合适且标签值多样，以便形成可比较的 assay-level 评测单元。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.15]；[doi:10.1038/s42004-024-01204-4, p.16]
- **declared_resources：** 论文声明 CARA 数据集已公开到 Zenodo。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.17]
- **declared_resources：** 论文同时给出代码仓库与代码归档地址，分别指向 GitHub 和 Zenodo。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.17]
- **limitations：** 作者明确说明，当前版本没有大规模评估 structure-based 方法，主要原因是多数 ChEMBL 蛋白缺乏实验结构和 binding pocket 信息。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.14]；[doi:10.1038/s42004-024-01204-4, p.15]
- **limitations：** 作者指出常用 uncertainty 指标，例如不同模型输出的标准差或 Gaussian process variance，仍难以准确捕捉 sample-level 误差。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.14]
- **limitations：** activity cliff 仍然是困难问题，文中显示 AC compounds 的 MAE 往往显著高于非 AC compounds。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.14]
- **limitations：** 作者也说明 CARA 不直接适用于 drug repurposing 和 selectivity 任务，因此其适用范围仍然是 task-specific 的。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.14]；[doi:10.1038/s42004-024-01204-4, p.15]
- **method：** 作者先从 ChEMBL v30 清洗单蛋白、小分子、完整 activity 记录，并按 assay 与测量类型重组为 CARA 的单一测量类型 assay。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.15]
- **method：** 作者用每个 assay 内分子两两 Tanimoto 相似度中位数 0.2 区分 VS 和 LO，再按 All、Kinase、GPCR 形成六个任务。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.4]；[doi:10.1038/s42004-024-01204-4, p.5]；[doi:10.1038/s42004-024-01204-4, p.15]
- **method：** 作者为减轻 protein exposure bias，先按蛋白序列相似度聚类，再对 VS 用 new-protein split、对 LO 用 new-assay split；few-shot 场景下每个 test assay 额外抽取 50 个 support 样本。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.6]；[doi:10.1038/s42004-024-01204-4, p.15]；[doi:10.1038/s42004-024-01204-4, p.16]
- **method：** 作者针对 VS 主要使用 EF@1%/5%，针对 LO 主要使用 PCC，并定义 per-assay、bulk 和 success rate 三层评测，其中 success 以 top 1% 命中或 PCC≥0.5 为阈值。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.5]；[doi:10.1038/s42004-024-01204-4, p.6]
- **method：** 作者在 zero-shot 与 few-shot 两种场景下比较了 pre-training、fine-tuning、re-training、QSAR、MAML 和 multi-task learning 等训练策略，并重复 5 次训练评估。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.7]；[doi:10.1038/s42004-024-01204-4, p.8]；[doi:10.1038/s42004-024-01204-4, p.9]；[doi:10.1038/s42004-024-01204-4, p.16]
- **results：** 作者用模拟例子和真实任务都说明 bulk evaluation 会高估性能，per-assay 评测能揭示不同 assay 之间很宽的性能分布。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.3]；[doi:10.1038/s42004-024-01204-4, p.7]
- **results：** 在 zero-shot 场景中，DeepConvDTI 取得最佳 success rate：VS-All 为 39.40%，LO-All 为 26.60%；LO-All 的 per-assay PCC 还可从 -0.4 到 1.0 波动。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.7]；[doi:10.1038/s42004-024-01204-4, p.8]
- **results：** few-shot 显著提升了结果：相较 zero-shot，VS-All 最佳 success rate 最多提高 9.80%，LO-All 最多提高 36.80%，平均 per-assay EF@1% 和 PCC 也分别提升了 6.78 和 0.26。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.9]
- **results：** 在 VS 任务中，cross-assay 信息通常能明显优于纯 QSAR；但在 LO 任务中，QSAR、meta-learning 和 multi-task learning 的表现相近，说明训练策略应随任务类型而变。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.9]；[doi:10.1038/s42004-024-01204-4, p.10]；[doi:10.1038/s42004-024-01204-4, p.11]
- **results：** 不同模型的 assay-level 输出相关性与性能正相关，作者还展示了把五个较强模型做 ensemble 可以在部分 assay 上进一步提升结果。
  - 证据：[doi:10.1038/s42004-024-01204-4, p.12]

## 页码证据

- [doi:10.1038/s42004-024-01204-4, p.1]
- [doi:10.1038/s42004-024-01204-4, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
