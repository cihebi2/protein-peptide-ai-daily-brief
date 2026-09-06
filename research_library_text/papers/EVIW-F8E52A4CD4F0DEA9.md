# Machine learning-based approaches for ubiquitination site prediction in human proteins

- **论文 ID：** `EVIW-F8E52A4CD4F0DEA9`
- **期刊 / 来源：** BMC Bioinformatics
- **发表时间：** 2023 Nov 28
- **DOI：** [10.1186/s12859-023-05581-w](https://doi.org/10.1186/s12859-023-05581-w)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者声称构建了 human ubiquitination benchmark HUSB，并以 10 种 ML/DL 方法系统比较特征型、序列型与混合型方案，给出可复现实验资源。

## 创新边界

`主要新意在 benchmark、数据切分与对比评测；模型本身多为标准架构，属于方法组合与实验设计层面的增量创新。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在人类蛋白中识别 ubiquitination sites，并在缺乏统一 benchmark 和一致评测协议的情况下，公平比较不同 ML/DL 方法的能力。

## 方法

- site windows、sequence features/ML。

## 数据与基准

- human ubiquitination datasets。

## 比较基线

- 既有ubiquitination predictors。

## 结果证据

- 论文报告计算site performance。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- PTM标签不完整、negative sites不确定。

## 仍未知

- GitHub 仓库是否仍可访问未核验
- 窗口长度与去重策略对结果的敏感性未独立重跑
- 未见外部独立数据集或湿实验验证

## Pi 结构化证据摘录

- **baseline：** 文中显式给出的 random classifier baseline macro-F1 为 0.305。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.15]
- **baseline：** 内部对照基线包含传统模型 XGBoost、SVM、KNN、RF、ANN，以及序列模型 LSTM、BERT 系列、Nystromformer、SqueezeBERT。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.6]；[doi:10.1186/s12859-023-05581-w, p.7]；[doi:10.1186/s12859-023-05581-w, p.16]；[doi:10.1186/s12859-023-05581-w, p.17]
- **data：** Set 1 由 dbPTM 2019 的 32,407 个蛋白经 CD-HIT 40% 后保留 5,429 个，用于训练/验证；其中训练集 4,886 个蛋白、验证集 543 个蛋白。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.11]；[doi:10.1186/s12859-023-05581-w, p.12]
- **data：** Set 2 由 dbPTM 2022 的 7,049 个新蛋白经 CD-HIT 40% 后保留 2,348 个，作为独立测试集；对应窗口级样本数为训练 15,181/180,393、验证 1,613/18,989、测试 9,713/82,554（positive/negative）。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.11]
- **declared_resources：** 作者声明 HUSB、数据集与源码已公开在 GitHub 仓库，便于复现与后续比较。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.4]；[doi:10.1186/s12859-023-05581-w, p.22]；[doi:10.1186/s12859-023-05581-w, p.23]
- **limitations：** 固定窗口会引入重复样本；作者在测试集不去重以贴近真实应用，这也说明预处理方式本身会影响可比性。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.13]；[doi:10.1186/s12859-023-05581-w, p.14]
- **limitations：** 作者观察到验证集 macro-F1 普遍高于测试集，说明仅靠同分布验证会高估泛化能力，独立测试集不可少。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.17]
- **limitations：** 较短窗口可能压缩上下文信息，作者也明确把窗口长度视为影响上限的重要因素。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.14]；[doi:10.1186/s12859-023-05581-w, p.21]
- **method：** 作者声称的主要贡献是建立可公平比较的 benchmark，并整合 open-access 数据集、标准指标和防信息泄漏的验证策略。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.3]；[doi:10.1186/s12859-023-05581-w, p.11]；[doi:10.1186/s12859-023-05581-w, p.12]
- **method：** 样本以固定窗口截取，目标 lysine 位于窗口中心；短序列用 padding 补齐，训练与验证集去重，而测试集保留重复窗口以模拟真实应用。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.13]；[doi:10.1186/s12859-023-05581-w, p.14]
- **method：** 作者比较了 feature-based conventional ML、sequence-based DL 以及 hybrid LSTM 融合特征方案，涵盖 XGBoost、SVM、KNN、RF、ANN、LSTM、BERT-small、BERT-tiny、Nystromformer 和 SqueezeBERT。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.6]；[doi:10.1186/s12859-023-05581-w, p.7]；[doi:10.1186/s12859-023-05581-w, p.8]；[doi:10.1186/s12859-023-05581-w, p.15]；[doi:10.1186/s12859-023-05581-w, p.17]；[doi:10.1186/s12859-023-05581-w, p.19]
- **method：** 评估采用 accuracy、recall、specificity、precision、F1、MCC，并把 macro-F1 作为主要模型选择指标；为类不平衡还比较了 weighted loss 与 balanced sample strategy。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.10]；[doi:10.1186/s12859-023-05581-w, p.17]
- **results：** 在 feature-based conventional ML 中，DNN + physicochemical feature 在 window size 21 达到最佳 macro-F1 0.537，整体优于 KNN、XGBoost、RF 和 SVM。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.16]
- **results：** 在 sequence-based DL 中，LSTM 在 window size 77 取得 test macro-F1 0.574，为该组最佳；作者也总结 DL 明显优于 classical ML。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.18]；[doi:10.1186/s12859-023-05581-w, p.21]
- **results：** 在 hybrid 方案中，LSTM + PSSM 于 window size 45 取得 macro-F1 0.576，且 positive class 的 F1、precision、recall 分别为 0.902、0.8786、0.9147，MCC 为 0.402。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.20]；[doi:10.1186/s12859-023-05581-w, p.21]
- **results：** 作者同时指出，把手工特征与 raw sequence 结合只带来很小增益（0.576 vs 0.574）。
  - 证据：[doi:10.1186/s12859-023-05581-w, p.21]

## 页码证据

- [doi:10.1186/s12859-023-05581-w, p.1]
- [doi:10.1186/s12859-023-05581-w, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
