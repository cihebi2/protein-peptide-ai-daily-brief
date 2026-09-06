# Deep-STP: a deep learning-based approach to predict snake toxin proteins by using word embeddings

- **论文 ID：** `EVIW-DECE7E720EE17251`
- **期刊 / 来源：** Front Med (Lausanne)
- **发表时间：** 2024 Jan 17
- **DOI：** [10.3389/fmed.2023.1291352](https://doi.org/10.3389/fmed.2023.1291352)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称提出首个名为 Deep-STP 的深度学习预测器，先用 g-gap、natural vector 与 word2vector 编码序列，再结合 ANOVA、GBDT 和 IFS 选择最优特征，最终用 CNN 完成 snake toxin proteins 识别。

## 创新边界

`创新主要体现在一个面向蛇毒蛋白分类的特征工程+CNN 流水线；它不生成、设计或优化候选蛋白，核心构件也都是已知方法的组合。`。这不是全球首创性检索或独立复现结论。

## 研究问题

建立一个可由蛋白序列直接驱动的计算模型，快速识别 snake toxin proteins，以缓解传统生化鉴定成本高、耗时长的问题，并弥补在缺少同源序列时依赖 FASTA/BLAST 等方法的局限。

## 方法

- 把氨基酸k-mer映射为词向量，经1D CNN和分类层预测toxin/non-toxin。

## 数据与基准

- UniProt正例和RefSeq负例，十折交叉验证。

## 比较基线

- 同源搜索、传统特征和既有toxin predictor。

## 结果证据

- 论文报告accuracy 82.00%；为类别预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 随机十折可能受同源泄漏影响，负例定义和物种偏差未完全解决。

## 仍未知

- 主文页面未给出 CNN 的完整超参数、层数、卷积核设置和训练轮次。
- 独立测试集的逐类样本分布与划分细节未在当前页面中完全展开。
- GitHub 仓库的实际可复现性与代码完整性未在本次冻结证据中独立核验。

## Pi 结构化证据摘录

- **baseline：** 与 RF 和 LSTM 相比，CNN 在融合特征上的表现更好；作者报告其在 10-fold CV 上的 AUROC 高于这些基线。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.5]
- **baseline：** 在 independent data 上，CNN 也优于 RF 和 LSTM；表中给出的 CNN accuracy 为 81.14%，而 RF 和 LSTM 分别为 78.20% 和 80.10%。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.6]
- **data：** 去冗余后，数据集包含 270 条 positive sequences 和 339 条 negative sequences。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.2]
- **data：** 作者将数据划分为 80% training data 和 20% independent data，用于客观评估模型。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.2]
- **declared_resources：** 论文明确声明 dataset 和 code 可在 GitHub 仓库 https://github.com/linDing-groups/Deep-STP 获取。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.6]
- **declared_resources：** 作者声明原始贡献已包含在正文或 Supplementary material 中，并可向通讯作者进一步咨询。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.6]
- **declared_resources：** 论文同时披露了经费来源，包括 National Nature Scientific Foundation of China 62302079 等。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.6]
- **limitations：** 作者的验证仍限于 10-fold CV 和单一 independent split，未见外部独立队列或湿实验验证。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.2]；[doi:10.3389/fmed.2023.1291352, p.5]；[doi:10.3389/fmed.2023.1291352, p.6]
- **limitations：** 作者在结尾仅提出后续将开发 web application，并尝试更多 feature selection techniques 与 algorithms，说明当前工作仍是初步基线而非终局方案。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.6]
- **method：** 样本来自 UniProt 和 RefSeq，并通过 80% sequence identity cutoff 去冗余后构建训练集与独立测试集。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.2]
- **method：** 序列被分别用 g-gap dipeptide composition、natural vector 和 word2vector 进行编码，其中 word2vector 采用 CBOW，嵌入维度为 200。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.2]；[doi:10.3389/fmed.2023.1291352, p.3]
- **method：** 作者用 ANOVA、GBDT 与 IFS 共同筛选最优特征子集，以降低冗余并提升分类性能。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.4]
- **method：** 筛选后的特征被输入 1-D CNN；实验实现使用 Keras 2.3.1、Python 3.5.4 和 TensorFlow 2.1.0，并与 RF、LSTM 等模型对比。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.4]；[doi:10.3389/fmed.2023.1291352, p.5]
- **results：** 在 10-fold CV 中，使用 167 个最优特征的 CNN 融合模型取得 82.00% accuracy，AUROC 为 0.926。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.5]
- **results：** 在 independent data 上，最佳 CNN 模型达到 81.14% accuracy，AUROC 为 0.917。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.6]
- **results：** 作者报告在最优融合模型中，NV、W2V 和 g-gap 的贡献分别为 35.92%、43.11% 和 20.95%。
  - 证据：[doi:10.3389/fmed.2023.1291352, p.5]

## 页码证据

- [doi:10.3389/fmed.2023.1291352, p.1]
- [doi:10.3389/fmed.2023.1291352, p.2]
- [doi:10.3389/fmed.2023.1291352, p.5]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
