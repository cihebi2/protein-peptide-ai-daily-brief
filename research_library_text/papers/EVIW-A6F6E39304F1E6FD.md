# GATSol, an enhanced predictor of protein solubility through the synergy of 3D structure graph and large language modeling

- **论文 ID：** `EVIW-A6F6E39304F1E6FD`
- **期刊 / 来源：** BMC Bioinformatics
- **发表时间：** 2024 Jun 1
- **DOI：** [10.1186/s12859-024-05820-8](https://doi.org/10.1186/s12859-024-05820-8)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `语言模型` / `结构预测`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出 GATSol：将 AlphaFold 预测的 3D 结构转成蛋白图，结合 ESM-1b 与 BLOSUM62 节点特征，再用 GAT 和 MLP 预测溶解度；作者声称它在 eSOL 与 S. cerevisiae 独立测试集上优于近期方法。

## 创新边界

`创新主要在已知组件的组合与图化建模方式；核心任务仍是监督式溶解度预测，不是新湿实验、不是候选蛋白生成，也不是新的结构预测模型本身。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在仅给定蛋白质序列的前提下，如何把预测结构图、蛋白语言模型表征和图注意力网络结合起来，更准确地预测蛋白质溶解度，并降低实验筛选成本。

## 方法

- PLM嵌入作节点特征，AlphaFold contact/distance构图，GAT pooling后回归/分类solubility。

## 数据与基准

- 独立eSOL和S. cerevisiae测试集及训练溶解度数据。

## 比较基线

- GraphSol、SoluProt及序列/结构单模态消融。

## 结果证据

- eSOL/S. cerevisiae R² 0.517/0.424，后者比GraphSol高18.4%；为计算预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 依赖AlphaFold距离图和小规模溶解度标签；表达系统/条件差异限制可迁移性。

## 仍未知

- 未独立核验 GitHub 仓库中的代码、参数和数据是否与论文完全一致。
- 未见作者说明 AlphaFold 具体版本、运行参数及结构置信度如何影响图构建。
- 未报告更多第三方外部数据集上的泛化表现。

## Pi 结构化证据摘录

- **baseline：** 引言把 SOLpro、PROSO II、DeepSol 等归为主要依赖 1D 序列特征的方法，并指出 GraphSol 虽引入 contact 信息，但数据处理流程较复杂。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.2]；[doi:10.1186/s12859-024-05820-8, p.3]
- **baseline：** 在 eSOL 独立测试集上，作者比较了 K-nearest neighbor、linear regression、random forest、Protein-Sol、XGBoost、SVM、DeepSol、ProGAN、SeqVec、TAPE、LSTM、GraphSol 和 GraphSol(Ensemble)。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.12]
- **baseline：** 在 S. cerevisiae 测试集上，作者比较了 GraphSol、GraphSol(ensemble)、ccSol、Protein-Sol、CamSol、DeepSol 和 ProGANb。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.13]
- **baseline：** 为了公平比较，作者把回归输出用 0.5 阈值二值化，再计算分类指标；同时明确表示没有使用 ensemble，以降低复杂度。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.9]；[doi:10.1186/s12859-024-05820-8, p.11]
- **data：** eSOL 原始包含 4132 个蛋白，映射到 NCBI 后为 3144 个样本，同源去除后得到 2679 条序列，最终划分为 2019 条训练与 660 条测试。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.4]
- **data：** S. cerevisiae 数据集原始为 447 个蛋白，去内部同源后剩 414 个，再与 eSOL 去冗余后得到 368 个；作者还给出与 GraphSol 对齐的 108 样本子集。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.4]；[doi:10.1186/s12859-024-05820-8, p.5]；[doi:10.1186/s12859-024-05820-8, p.13]
- **data：** 图边和距离图不是实验测得，而是由 AlphaFold 预测结构中的 Cα 坐标计算得到，因此结构信息来自计算推断。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.6]
- **declared_resources：** 论文声明源代码和数据可在 https://github.com/binbinbinv/GATSol 获取。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.1]；[doi:10.1186/s12859-024-05820-8, p.14]
- **declared_resources：** 作者感谢 Nanjing Tech University High-Performance Computing Center 提供计算资源支持。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.14]
- **declared_resources：** 论文声明项目获得了 National Key Research and Development Program of China 的资助。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.14]
- **limitations：** 论文只给出 5-fold cross-validation 和两个独立测试集上的计算结果，没有展示新的湿实验或前瞻性验证。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.9]；[doi:10.1186/s12859-024-05820-8, p.12]；[doi:10.1186/s12859-024-05820-8, p.13]
- **limitations：** 模型对 AlphaFold 预测结构和距离阈值设置有明显依赖，作者还需要通过交叉验证选择 10Å，这说明上游结构质量与阈值会影响最终图表示。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.6]；[doi:10.1186/s12859-024-05820-8, p.10]
- **limitations：** 部分对照评估依赖把连续溶解度预测强行二值化为 0.5 阈值，这使得分类指标对阈值设定较敏感。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.9]；[doi:10.1186/s12859-024-05820-8, p.11]
- **method：** 作者使用 eSOL 与 S. cerevisiae 两个数据集，并通过同源去冗余来划分训练集和独立测试集，以尽量减少泄漏。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.4]；[doi:10.1186/s12859-024-05820-8, p.5]
- **method：** 每个氨基酸被视为一个图节点，节点特征由 ESM-1b 的 1280 维向量与 BLOSUM62 的 20 维向量拼接而成。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.5]
- **method：** 作者先用 AlphaFold 从序列预测 PDB 结构，再按 Cα 距离构建邻接关系，并通过交叉验证选择距离阈值。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.6]；[doi:10.1186/s12859-024-05820-8, p.10]
- **method：** 模型主体是两层 multi-head GAT，随后接入 MLP 输出连续的溶解度值。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.7]；[doi:10.1186/s12859-024-05820-8, p.8]；[doi:10.1186/s12859-024-05820-8, p.9]
- **method：** 训练阶段采用 5-fold cross-validation，优化目标使用 RMSE；评估时以 R2 为主，并在二值化比较中报告 AUC、Accuracy、Precision、Recall 和 F1。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.9]；[doi:10.1186/s12859-024-05820-8, p.11]
- **results：** 在独立 eSOL 测试集上，GATSol 的 R2 达到 0.517，Accuracy 为 0.791，Precision 为 0.781，Recall 为 0.745，F1 为 0.763，AUC 为 0.882。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.12]
- **results：** 作者在 eSOL 上报告 GATSol 优于 GraphSol 与 GraphSol(Ensemble)，其中 R2 分别为 0.483 和 0.501。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.12]
- **results：** 在 S. cerevisiae_368 上，GATSol 的 R2 为 0.361；在与 GraphSol 对齐的 S. cerevisiae_108 上，R2 为 0.424，作者称其比 GraphSol 提升 18.4%，比 GraphSol(ensemble) 提升 14%。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.13]
- **results：** 消融实验显示，ESM-1b 与 BLOSUM62 联合使用时在训练集交叉验证中最好，R2 为 0.411；距离阈值方面，10Å 被选为最优。
  - 证据：[doi:10.1186/s12859-024-05820-8, p.10]

## 页码证据

- [doi:10.1186/s12859-024-05820-8, p.11]
- [doi:10.1186/s12859-024-05820-8, p.1]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
