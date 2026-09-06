# Comprehensive Research on Druggable Proteins: From PSSM to Pre-Trained Language Models

- **论文 ID：** `EVIW-9BCBB5D287E1A4A6`
- **期刊 / 来源：** Int J Mol Sci
- **发表时间：** 2024 Apr 19
- **DOI：** [10.3390/ijms25084507](https://doi.org/10.3390/ijms25084507)
- **范围标签：** `Pi 已解析` / `背景资料` / `论文声明资源` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者声称提出了一个基于 fine-tuned ESM-2 嵌入的快速而精确的可成药蛋白分类器，在 Jamali 基准上达到 95.11% accuracy；同时系统比较了 ESM-2 与 PSSM，并将改造后的 GPT-2 首次用于 druggable protein 识别，还用较新的 Pharos 数据集做了进一步验证。

## 创新边界

`创新主要在序列表征与分类管线的适配组合上：PLM embedding、fine-tuning、CapsNet/DNN/BiLSTM 以及改造 GPT-2。它没有展示新的生物学机制、湿实验发现或候选分子生成能力。`。这不是全球首创性检索或独立复现结论。

## 研究问题

从纯蛋白序列中识别可成药蛋白，以便在药物发现前期快速筛选靶点、降低实验成本并提高大规模筛查效率。

## 方法

- 综述。

## 数据与基准

- 被引研究。

## 比较基线

- 不适用。

## 结果证据

- 无原创结果。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 非系统meta-analysis。

## 仍未知

- GitHub 仓库与 web server 的可访问性、许可证和可复现性未独立核验
- Pharos 与 Jamali 的标签口径不一致，跨数据集比较存在偏差
- 论文未提供任何湿实验或外部临床验证

## Pi 结构化证据摘录

- **baseline：** 与既有方法相比，作者在 Jamali benchmark 上对照了 DrugMiner、GA-Bagging-SVM、XGB-DrugPred 和 DrugFinder，并报告其 fine-tuned ESM-2 with CapsNet 略优。
  - 证据：[doi:10.3390/ijms25084507, p.8]；[doi:10.3390/ijms25084507, p.9]
- **baseline：** 作者强调预训练模型在效率上优于 PSSM，因为 PSSM 需要在 CPU 上遍历整个数据集，而 PLM 更适合 GPU 加速。
  - 证据：[doi:10.3390/ijms25084507, p.10]
- **baseline：** 对 Pharos 数据集，作者表示没有现成的 benchmark 可直接对照，因此只能与 Jamali 结果做间接比较。
  - 证据：[doi:10.3390/ijms25084507, p.8]
- **data：** Jamali/DrugMiner 数据集包含 1224 个 druggable proteins 和 1319 个 undruggable proteins，正样本来自 DrugBank，负样本来自 Swiss-Prot。
  - 证据：[doi:10.3390/ijms25084507, p.11]
- **data：** Pharos 原始数据集共 20,142 条序列，四类分别为 Tbio 12,277、Tchem 1,915、Tdark 5,516、Tclin 704；本文仅使用 Tclin 与 Tdark。
  - 证据：[doi:10.3390/ijms25084507, p.11]
- **data：** 作者给出的数据划分中，Jamali 与 Pharos 都按 80:20 形成训练/测试集，并在训练集内再切出验证集；对应样本数见 Table 7。
  - 证据：[doi:10.3390/ijms25084507, p.12]
- **data：** 作者指出两个数据集共有的 2101 条序列里有 43 条存在标签不一致，这会影响跨数据集比较。
  - 证据：[doi:10.3390/ijms25084507, p.8]
- **declared_resources：** 作者在第18页给出源码仓库链接 https://github.com/txz32102/DruggableProtein，并声明代码与数据可供学术社区使用。
  - 证据：[doi:10.3390/ijms25084507, p.18]
- **declared_resources：** 作者还公开了 web server https://druggableprotein.com，可上传 FASTA 并获得预测结果。
  - 证据：[doi:10.3390/ijms25084507, p.10]；[doi:10.3390/ijms25084507, p.18]
- **declared_resources：** 网页服务页明确写到该平台可在 1 core、2 GB RAM 的机器上运行，并支持生成 fine-tuned ESM-2 embeddings 与 1200D PSSM embeddings。
  - 证据：[doi:10.3390/ijms25084507, p.10]
- **limitations：** 作者自己也指出，Pharos 的样本更少、标签又与 Jamali 存在差异，因此两套数据上的性能差别不能简单解释为模型优劣。
  - 证据：[doi:10.3390/ijms25084507, p.8]；[doi:10.3390/ijms25084507, p.10]
- **limitations：** Pharos 的 Method 2 虽然用了 SMOTE 并在训练时看起来更高，但在验证或测试阶段表现较差，所以最终没有采用。
  - 证据：[doi:10.3390/ijms25084507, p.11]
- **limitations：** 作者明确承认 modified GPT-2 的结果并不好，说明 LLM 端到端方案在这个任务上仍不稳定。
  - 证据：[doi:10.3390/ijms25084507, p.9]；[doi:10.3390/ijms25084507, p.18]
- **limitations：** 论文结论也写明，PLM 的优势可能受数据集特性影响，不能据此推断在所有设置下都稳定优于 PSSM。
  - 证据：[doi:10.3390/ijms25084507, p.10]；[doi:10.3390/ijms25084507, p.18]
- **method：** 作者先以 Jamali/DrugMiner 作为平衡基准，并从 Pharos 仅保留 Tclin/Tdark；Pharos 还尝试过随机下采样与 SMOTE 两种平衡方案，但最终采用随机下采样方案。
  - 证据：[doi:10.3390/ijms25084507, p.11]
- **method：** 训练/验证/测试采用 80:20 切分，训练集内再做 80/20 验证，同时用 5-fold CV 与独立测试汇报性能。
  - 证据：[doi:10.3390/ijms25084507, p.11]；[doi:10.3390/ijms25084507, p.17]
- **method：** ESM-2 选用 esm2_t6_8M_UR50D，抽取 320D embedding，并在 Jamali 数据集上微调以获得更好的表征；还利用 attention contacts 画 contact map。
  - 证据：[doi:10.3390/ijms25084507, p.12]；[doi:10.3390/ijms25084507, p.16]；[doi:10.3390/ijms25084507, p.17]
- **method：** PSSM 通过 PSI-BLAST 对 SWISS-PROT 做 3 轮迭代、E-value 0.001，随后拼接 DPC-PSSM、KSB-PSSM(k=3) 和 S-FPSSM 形成 1200D 特征。
  - 证据：[doi:10.3390/ijms25084507, p.12]；[doi:10.3390/ijms25084507, p.13]
- **method：** 分类器包括 scikit-learn 的 SVM/RF/NB/XGB，以及 DNN、CapsNet、BiLSTM；作者还把 GPT-2 改造成端到端二分类器。
  - 证据：[doi:10.3390/ijms25084507, p.13]；[doi:10.3390/ijms25084507, p.14]；[doi:10.3390/ijms25084507, p.15]；[doi:10.3390/ijms25084507, p.16]
- **results：** 整体上，ESM-2 编码在 Jamali 与 Pharos 两个数据集上都优于 PSSM；Jamali 的最佳 ACC 为 0.9326，Pharos 的最佳 ACC 为 0.8739。
  - 证据：[doi:10.3390/ijms25084507, p.3]；[doi:10.3390/ijms25084507, p.4]；[doi:10.3390/ijms25084507, p.6]
- **results：** 深度学习里，Jamali 上 CapsNet+ESM-2 达到 0.9340 ACC，Pharos 上 DNN+ESM-2 达到 0.9037 ACC。
  - 证据：[doi:10.3390/ijms25084507, p.6]；[doi:10.3390/ijms25084507, p.7]
- **results：** 作者最好的模型是 fine-tuned ESM-2 with CapsNet，Jamali benchmark 上达到 0.9511 ACC、0.9683 SN、0.9691 SP、0.9512 F1 和 0.9011 MCC。
  - 证据：[doi:10.3390/ijms25084507, p.8]；[doi:10.3390/ijms25084507, p.9]
- **results：** SHAP 分析显示，在三类 PSSM 特征中，S-FPSSM 的平均绝对贡献最高，其次是 DPC-PSSM 和 KSB-PSSM。
  - 证据：[doi:10.3390/ijms25084507, p.3]
- **results：** 改造后的 GPT-2 只能达到 0.9282 ACC，作者也明确承认它没有取得最佳结果。
  - 证据：[doi:10.3390/ijms25084507, p.8]；[doi:10.3390/ijms25084507, p.9]；[doi:10.3390/ijms25084507, p.18]

## 页码证据

- [doi:10.3390/ijms25084507, p.1]
- [doi:10.3390/ijms25084507, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
