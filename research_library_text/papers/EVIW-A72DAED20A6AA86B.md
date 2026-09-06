# An interpretable geometric graph neural network for enhancing the generalizability of drug–target interaction prediction

- **论文 ID：** `EVIW-A72DAED20A6AA86B`
- **期刊 / 来源：** BMC Biology（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1186/s12915-025-02456-9](https://doi.org/10.1186/s12915-025-02456-9)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `图与几何学习`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 GPS-DTI，把 GINE+MHAM 的药物图编码、ESM-2+CNN 的蛋白编码和 cross-attention 融合结合起来，旨在提升 DTI 预测的泛化性、稳定性与可解释性。

## 创新边界

`创新边界在于 DTI 预测的表征与融合，不涉及分子生成、优化或 docking。`。这不是全球首创性检索或独立复现结论。

## 研究问题

现有 DTI 预测模型在未见药物、未见靶标、冷启动和跨域分布下泛化不足，难以支撑真实药物发现场景中的稳健筛选与解释。

## 方法

- 小分子图和蛋白结构图经geometric GNN编码，与全局序列/分子特征融合并解释关键区域。

## 数据与基准

- in-domain、cross-domain DTI/DTA及COVID-19独立测试。

## 比较基线

- 序列、图和结构DTI模型及局部/全局消融。

## 结果证据

- 论文报告多基准SOTA和独立COVID集鲁棒性；为计算interaction/affinity预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 结构预测误差和负样本偏差仍存在，解释权重不等同于机制。

## 仍未知

- 补充材料 Additional file 1-7 的具体统计检验、复杂度表和可视化流程未在冻结页完整展开。
- GitHub 仓库与冻结稿是否完全一致、以及代码/数据/模型许可证细节未被外部核验。
- COVID-19 独立测试集的完整负样本采样与阈值选择细节仅部分披露。

## Pi 结构化证据摘录

- **baseline：** 分类任务基线包括 SVM、RF、GraphDTA、DeepConvDTI、TransformerCPI、MolTrans、HyperAttDTI、DrugBAN 和 CAT-DTI。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.3]；[doi:10.1186/s12915-025-02456-9, p.4]
- **baseline：** DTA 冷启动比较还纳入 DeepDTA、AttentionMGT-DTA、ELECTRA-DTA 与 GraphDTA，药物编码消融则用 GAT、GCN、GINE 和 GIN 作为替代。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.7]；[doi:10.1186/s12915-025-02456-9, p.8]；[doi:10.1186/s12915-025-02456-9, p.10]
- **data：** 五个公开基准数据集分别是 Human、C.elegans、BioSNAP、BindingDB 和 DrugBank，表 3 报告了它们在 drugs、proteins、interactions 和 positives 上的规模差异。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.12]
- **data：** 作者还用 DAVIS 做 DTA 冷启动回归，并从 TTD 筛出 101 条 COVID-19 相关相互作用（50 个 proteins、69 个 drugs）做独立验证，负样本按 1× 到 20× 比例随机构造。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.6]；[doi:10.1186/s12915-025-02456-9, p.7]；[doi:10.1186/s12915-025-02456-9, p.8]；[doi:10.1186/s12915-025-02456-9, p.18]
- **declared_resources：** 论文声明 source code 已公开于 GitHub: https://github.com/xa-123955/GPS-DTI。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.18]
- **declared_resources：** 数据均来自公开资源，包括 DrugBAN/MolTrans/CPI_prediction/DrugBank/AttentionMGT-DTA/TTD 等仓库或数据库。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.17]；[doi:10.1186/s12915-025-02456-9, p.18]；[doi:10.1186/s12915-025-02456-9, p.19]
- **limitations：** 作者承认训练数据的规模与多样性仍有限，限制模型覆盖真实世界 DTI 空间。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.11]；[doi:10.1186/s12915-025-02456-9, p.12]
- **limitations：** 当前方法主要依赖 2D 化学表示和蛋白序列，尚未系统整合 3D 结构信息。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.11]；[doi:10.1186/s12915-025-02456-9, p.12]
- **limitations：** allosteric regulation 等复杂机制因公开数据不足未被充分评估，作者也明确指出仍需要更强的 domain adaptation。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.11]；[doi:10.1186/s12915-025-02456-9, p.12]
- **method：** 药物分支先将 SMILES 转为包含原子与键特征的分子图，并加入 Laplacian eigenvectors 作为 positional encoding，以增强结构表征。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.12]；[doi:10.1186/s12915-025-02456-9, p.14]
- **method：** GPS layer 以 GINE/MPNN 进行局部消息传递，再用 MHAM 建模全局依赖，随后通过 MLP 融合并更新节点与边表示。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.14]；[doi:10.1186/s12915-025-02456-9, p.15]
- **method：** 蛋白分支使用预训练 ESM-2 生成序列嵌入，再经三层 CNN 提取局部模式；药物与蛋白表示随后通过 cross-attention、global max pooling 和全连接分类器输出 DTI 概率。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.12]；[doi:10.1186/s12915-025-02456-9, p.15]；[doi:10.1186/s12915-025-02456-9, p.16]
- **results：** 五折交叉验证中，GPS-DTI 在 DrugBank、BioSNAP、Human 和 C.elegans 上整体优于 SVM、RF、GraphDTA、DeepConvDTI、TransformerCPI、MolTrans、HyperAttDTI、DrugBAN 和 CAT-DTI；BindingDB 上略低于 DrugBAN 但仍保持稳健。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.4]；[doi:10.1186/s12915-025-02456-9, p.5]
- **results：** 跨域评估中，GPS-DTI 在 BindingDB 上取得 AUROC 0.699、AUPRC 0.599、F1 0.680，并在 BioSNAP 上也达到最优。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.5]
- **results：** DAVIS 冷启动回归里，drug cold 的 MSE/CI/r2m 为 0.570/0.694/0.154，target cold 为 0.2854/0.8461/0.5211；pair cold 仍优于其他模型。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.6]；[doi:10.1186/s12915-025-02456-9, p.7]
- **results：** COVID-19 独立测试中，GPS-DTI 在 1× 到 20× negative ratios 下保持最高 AUROC，并在强类别不平衡下维持较稳定的 F1。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.8]
- **results：** 消融实验显示完整模型 M-4 在 BioSNAP 和 BindingDB 的 cross-domain AUROC 分别为 0.781 和 0.679，优于去掉 MHAM 或 CAM 的变体。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.10]
- **results：** 在 3S75 和 2XFK 复合物上，cross-attention 定位到与已知氢键/结合残基一致的 sulfonamide、amine 等关键原子，以及 Thr199、Thr293、Asn294 等位点。
  - 证据：[doi:10.1186/s12915-025-02456-9, p.11]

## 页码证据

- [doi:10.1186/s12915-025-02456-9, p.12]
- [doi:10.1186/s12915-025-02456-9, p.1]
- [doi:10.1186/s12915-025-02456-9, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
