# A Molecular-Protein Fusion Framework for Rapid Virtual Screening: Accelerating Lead Discovery for 'Undruggable' Oncogenic Targets

- **论文 ID：** `EVIW-DB4950B4D4A2E3D1`
- **期刊 / 来源：** Pharmaceuticals (Basel)
- **发表时间：** 2026 May 12
- **DOI：** [10.3390/ph19050753](https://doi.org/10.3390/ph19050753)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称提出 MPFF-IS：用 ESM2 蛋白表示与 MPNN 分子图表示做交叉融合预测，再把高置信候选物送入 docking、300 ns MD 与 MM/PBSA 验证，以支持 KRAS G12D 抑制剂快速筛选。

## 创新边界

`其可确认的新意主要是面向 KRAS G12D 的蛋白-分子融合式筛选流程与一体化验证链条；冻结证据不足以独立证明其全球方法学原创性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

面向 PDAC 中难成药的 KRAS G12D，作者要解决的是如何用机器学习与结构生物学联合流程快速筛出潜在抑制剂，并尽量降低传统虚拟筛选中的假阳性与手工特征依赖。

## 方法

- drug/protein LM/graph encoders与ranking。

## 数据与基准

- oncogenic targets/ligands/candidate libraries。

## 比较基线

- docking/DTI models。

## 结果证据

- 论文报告virtual hits；无明确实验则保持计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- target labels/结构/无prospective assay。

## 仍未知

- 未见湿实验、动物实验或前瞻性外部验证。
- 补充材料的具体内容在冻结页面中未展开，无法独立核验。
- 无法仅凭冻结证据确认 MPFF-IS 的全球方法学新颖性。

## Pi 结构化证据摘录

- **baseline：** 文中对比的机器学习/DTI 基线包括 KNN、SVM、RF、GNB、XGB、LightGBM、CatBoost，以及 DeepDTA 和 GraphDTA。
  - 证据：[doi:10.3390/ph19050753, p.4]；[doi:10.3390/ph19050753, p.5]；[doi:10.3390/ph19050753, p.6]
- **baseline：** 虚拟验证阶段还以 MRTX1133 和 BI-2852 作为两类机制参照抑制剂，用于比较 docking、MD 和 MM/PBSA 结果。
  - 证据：[doi:10.3390/ph19050753, p.7]；[doi:10.3390/ph19050753, p.8]；[doi:10.3390/ph19050753, p.14]；[doi:10.3390/ph19050753, p.15]
- **data：** 标签规则定义为 IC50 ≤ 6.1 nM 为正样本、IC50 ≥ 6.1 nM 为负样本，阈值来源于 MRTX1133 的活性标准。
  - 证据：[doi:10.3390/ph19050753, p.18]
- **data：** 对接与结构验证使用 KRAS G12D 结构 7RPZ 和 6GJ8，预处理包括去水、加氢、赋 Gasteiger 电荷，并以 7RPZ 中 MRTX1133 位点设置 20 Å 立方网格。
  - 证据：[doi:10.3390/ph19050753, p.22]
- **data：** MD 采用 AMBER99SB-ILDN 力场与 TIP3P 水模型，加入约 0.15 mol/L 离子并进行 2 fs 步长、总计 300 ns 的生产模拟。
  - 证据：[doi:10.3390/ph19050753, p.23]
- **data：** MM/PBSA 从 300 ns 轨迹中每 2 ns 抽取一帧，共 150 帧，用于估计结合自由能及其静电、范德华和溶剂化分量。
  - 证据：[doi:10.3390/ph19050753, p.23]；[doi:10.3390/ph19050753, p.24]
- **declared_resources：** 文中声明补充材料可从 MDPI 页面下载，原始数据也可向作者进一步索取；Funding 来自 National College Students’ Innovation and Entrepreneurship Training Program (202510291096).
  - 证据：[doi:10.3390/ph19050753, p.25]
- **declared_resources：** 实现与分析工具明确列出 ESM2、DGL-LifeSci、RDKit、PyTorch 2.6.0、AutoDock Vina 1.2.0、GROMACS 2025.2、gmx_MMPBSA 和 PLIP 2025，并采用 AMBER99SB-ILDN 与 TIP3P。
  - 证据：[doi:10.3390/ph19050753, p.19]；[doi:10.3390/ph19050753, p.20]；[doi:10.3390/ph19050753, p.21]；[doi:10.3390/ph19050753, p.22]；[doi:10.3390/ph19050753, p.23]；[doi:10.3390/ph19050753, p.24]
- **limitations：** 作者明确指出该框架目前只面向单一蛋白靶点，不能覆盖 RMC-6236 一类多蛋白协同机制，因此未来需要结合复合物结构和 network pharmacology。
  - 证据：[doi:10.3390/ph19050753, p.24]；[doi:10.3390/ph19050753, p.25]
- **limitations：** 冻结文本中的验证链条主要停留在 docking、300 ns MD、MM/PBSA 和 PCA，未见湿实验或动物实验来直接确认候选化合物活性。
  - 证据：[doi:10.3390/ph19050753, p.22]；[doi:10.3390/ph19050753, p.23]；[doi:10.3390/ph19050753, p.24]；[doi:10.3390/ph19050753, p.25]
- **method：** 训练集来自 BindingDB，共 2540 条 KRAS G12D 配对样本，按 Bemis–Murcko scaffold 分层划分训练/验证/测试集，以尽量避免 scaffold 泄漏并近似 8:1:1 切分。
  - 证据：[doi:10.3390/ph19050753, p.18]
- **method：** 候选筛选库来自 IBS、NPASS、ChEMBL 和 ZINC，经过 MW、LogP、HBD、HBA 等理化阈值过滤并去重后，形成 133,856 个待筛分子。
  - 证据：[doi:10.3390/ph19050753, p.18]
- **method：** 模型主体由 ESM2 蛋白编码器、MPNN 分子图编码器、cross-coupled fusion 模块和 MLP 预测头组成，其中 ESM2 参数默认冻结，仅训练下游投影与融合层。
  - 证据：[doi:10.3390/ph19050753, p.19]；[doi:10.3390/ph19050753, p.20]；[doi:10.3390/ph19050753, p.21]
- **method：** 训练策略使用 AdamW、BCEWithLogitsLoss、early stopping 与 Bayesian optimization，分子侧执行 6 轮 message passing，以学习更高阶的结构信息。
  - 证据：[doi:10.3390/ph19050753, p.21]
- **results：** MPFF-IS 在测试集上达到 Accuracy 0.8465、ROC-AUC 0.9463、F1 0.8040、MCC 0.6881，整体优于 KNN、SVM、RF、GNB、XGB、LightGBM、CatBoost、DeepDTA 和 GraphDTA。
  - 证据：[doi:10.3390/ph19050753, p.4]；[doi:10.3390/ph19050753, p.5]；[doi:10.3390/ph19050753, p.6]
- **results：** 消融结果显示，MPNN + ESM2 + Fusion + MLP 的完整组合表现最好；而 fingerprint 加 one-hot 的简化配置明显变差，说明深层表示与融合机制确有增益。
  - 证据：[doi:10.3390/ph19050753, p.6]；[doi:10.3390/ph19050753, p.7]
- **results：** 模型从 133,856 个分子中筛出 2663 个高置信候选物；GDP-state 组里 CHEMBL5079995、CHEMBL5409510、CHEMBL4867851 的 Vina score 均优于 MRTX1133。
  - 证据：[doi:10.3390/ph19050753, p.7]；[doi:10.3390/ph19050753, p.8]
- **results：** MD 与 MM/PBSA 显示，Lig2/Lig3 对 GDP-state 的结合自由能接近 MRTX1133，而 Lig4/Lig5 对 GDP/GTP-state 的结果接近 BI-2852，其中 Lig5 在活性态组表现最稳。
  - 证据：[doi:10.3390/ph19050753, p.11]；[doi:10.3390/ph19050753, p.12]；[doi:10.3390/ph19050753, p.14]；[doi:10.3390/ph19050753, p.15]；[doi:10.3390/ph19050753, p.16]
- **results：** PCA 显示候选体系与参考抑制剂的构象空间存在部分重叠但并不完全一致，作者将其解释为保持关键功能特征同时仍可进一步优化。
  - 证据：[doi:10.3390/ph19050753, p.16]；[doi:10.3390/ph19050753, p.17]

## 页码证据

- [doi:10.3390/ph19050753, p.1]
- [doi:10.3390/ph19050753, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
