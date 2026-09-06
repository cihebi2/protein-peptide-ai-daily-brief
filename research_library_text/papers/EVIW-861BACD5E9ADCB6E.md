# Deep-WET: a deep learning-based approach for predicting DNA-binding proteins using word embedding techniques with weighted features

- **论文 ID：** `EVIW-861BACD5E9ADCB6E`
- **期刊 / 来源：** Sci Rep
- **发表时间：** 2024 Feb 5
- **DOI：** [10.1038/s41598-024-52653-9](https://doi.org/10.1038/s41598-024-52653-9)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 Deep-WET：先用 GloVe、Word2Vec 和 fastText 编码序列，再用 DE 学习权重、用 SHAP 选择特征，最后以 CNN 完成 DBP 二分类，并声称在独立测试上优于多种基线。

## 创新边界

`主要是对现有 embedding、加权融合、SHAP 选特征和 CNN 分类的组合式改进；冻结证据支持的是实验增益，而不是全球首创。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何仅依据蛋白质 primary sequence，稳定地区分 DNA-binding proteins 与 non-DBPs，并在独立测试上优于既有序列驱动方法。

## 方法

- k-mer/word embeddings与weighted network。

## 数据与基准

- DNA-BP/non-DNA datasets。

## 比较基线

- 传统features/ML。

## 结果证据

- 论文报告超过baselines；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 全蛋白分类非binding site，负样本/同源偏差。

## 仍未知

- 未见可复用源码仓库
- 未见独立外部复现
- web server 实际可用性未由冻结材料验证

## Pi 结构化证据摘录

- **baseline：** 作者把 Deep-WET 与 SVM、XGBoost、LightGBM 及普通 CNN 在三类 embedding 上做了对比，整体上 CNN 优于传统 ML。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.10]；[doi:10.1038/s41598-024-52653-9, p.13]
- **baseline：** 独立测试的公开方法基线包括 DPP-PseAAC、iDNA-Prot、iDNA-Prot|dis、PseDNA-Pro、PSFM-DBT、IKP-DBPPred、Local-DPP、iDNAProt-ES、TargetDBP 等。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.11]；[doi:10.1038/s41598-024-52653-9, p.14]
- **baseline：** 文中指出 iDNAProt-ES 的 sensitivity 最高但 specificity 很低，而 Local-DPP 的 specificity 很高但 precision 很差。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.14]
- **data：** 训练集与独立测试集来自 Jun Hu 等人整理的 PDB 蛋白链数据，并先用 CD-HIT 0.25 去冗余、去除少于 50 residues 或含未知残基的序列。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.3]
- **data：** 冻结材料给出的规模是训练集 1052 个 DBPs 与 1052 个 non-DBPs，独立测试集 148 个 DBPs 与 148 个 non-DBPs。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.3]
- **declared_resources：** Deep-WET 提供 web server，可上传 FASTA 序列并返回概率和类别结果，job ID 可保留 15 天。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.13]
- **declared_resources：** 作者同时给出了数据下载页面，表示实验数据可从项目网站获取。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.14]；[doi:10.1038/s41598-024-52653-9, p.15]
- **declared_resources：** 实现环境包括 Apache 2.4.48、Laravel 8.16.1、Python 3.8.0、TensorFlow 2.0 和 SHAP 0.39.0；硬件为多台 Intel Core i5 机器与一台 64GB RAM 服务器。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.7]；[doi:10.1038/s41598-024-52653-9, p.13]
- **limitations：** 作者承认 NLP embedding 仍可能有 ambiguity、lexical gaps 和 structural gaps，因此后续考虑 autoencoder。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.14]
- **limitations：** 网页服务在处理较大序列文件时会比较慢，作者建议一次输入较少的序列。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.13]
- **limitations：** 作者还把 label noise 和未知结构列为后续方向，计划结合 small-loss、pLOF 与 graph-based deep learning。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.14]
- **method：** 作者将蛋白序列分别编码为 GloVe、Word2Vec 和 fastText 三种 word embedding，并按顺序融合为候选特征。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.1]；[doi:10.1038/s41598-024-52653-9, p.2]；[doi:10.1038/s41598-024-52653-9, p.7]
- **method：** 他们用 differential evolution 学习特征权重，再用 SHAP 按重要性筛选出最优特征子集。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.5]；[doi:10.1038/s41598-024-52653-9, p.8]；[doi:10.1038/s41598-024-52653-9, p.9]
- **method：** 最终将筛出的特征送入 CNN；模型使用卷积层、max-pooling、batch normalization、dropout 和 Adam 进行二分类训练。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.6]；[doi:10.1038/s41598-024-52653-9, p.7]；[doi:10.1038/s41598-024-52653-9, p.9]
- **method：** 作者还用 5-fold cross-validation 和独立测试集来选择最终模型，并把 CNN 与 SVM、XGBoost、LightGBM 做了同场比较。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.7]；[doi:10.1038/s41598-024-52653-9, p.10]；[doi:10.1038/s41598-024-52653-9, p.13]
- **results：** 在 5-fold CV 中，GloVe+fastText+Word2Vec 的 CNN 达到 AUC 0.864、ACC 79.07%、MCC 0.585，优于单一 embedding。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.7]
- **results：** 加入 SHAP 后，400 维最优特征子集的 CNN 在训练集上达到 AUC 0.883、ACC 82.56%、Spe 92.00%、MCC 0.641。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.8]；[doi:10.1038/s41598-024-52653-9, p.9]
- **results：** 独立测试上，Deep-WET 达到 AUC 0.805、ACC 78.08%、Sen 78.05%、Spe 78.13%、MCC 0.559、Pre 82.05%、F1 0.800。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.14]
- **results：** 与 TargetDBP 等现有方法相比，Deep-WET 在独立测试的 ACC、MCC、Pre 和 F1 上最好，且 AUC 也高于大多数基线。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.14]
- **results：** 消融实验显示，移除卷积滤波器、池化、kernel size 或全连接层都会削弱 AUC，说明各组件都对结果有贡献。
  - 证据：[doi:10.1038/s41598-024-52653-9, p.12]

## 页码证据

- [doi:10.1038/s41598-024-52653-9, p.1]
- [doi:10.1038/s41598-024-52653-9, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
