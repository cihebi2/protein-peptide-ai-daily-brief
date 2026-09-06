# PGAT-ABPp: harnessing protein language models and graph attention networks for antibacterial peptide identification with remarkable accuracy

- **论文 ID：** `EVIW-E288C151E5D5BCAF`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2024 Aug 9
- **DOI：** [10.1093/bioinformatics/btae497](https://doi.org/10.1093/bioinformatics/btae497)
- **范围标签：** `Pi 已解析` / `核心相关` / `有静态审计仓库` / `肽与抗菌肽` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出 PGAT-ABPp，把 ProtT5 embedding 与 AlphaFold2/ColabFold 预测结构构建的图输入 GAT，用于 ABP 二分类，并声称取得最优性能。

## 创新边界

`新意在于 PLM+预测结构+GAT 的 ABP 分类；不涉及候选生成、优化或湿实验验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在抗菌肽大规模筛选前，如何用计算方法高准确地区分 ABP 与 non-ABP，以降低实验筛选成本并辅助后续设计。

## 方法

- ProtT5-XL-U50嵌入；预测结构图；图注意力网络；独立测试与14个方法比较。

## 数据与基准

- 公开ABP/非ABP训练与独立测试集；结构为预测而非实验结构。

## 比较基线

- 14个既有ABP预测器及序列/结构特征消融。

## 结果证据

- 论文报告在独立集准确率、F1和MCC优于14个比较模型；没有实验抗菌验证。

## 可用资源与代码关系

- [https://github.com/moonseter/PGAT-ABPp](https://github.com/moonseter/PGAT-ABPp)
  - 固定 commit：`e3a1a38e784f5449c49c745372e0ea85b3e6ee04`
  - 静态复用层级：C_license_or_component_gaps
  - 许可证边界：license_not_found_reuse_blocked

## 已知限制

- 水中预测构象可能不同于膜环境；预测结构误差和序列同源泄漏可能影响性能。

## 仍未知

- 论文未提供湿实验验证来确认预测性能在真实筛选中的转化效果。
- 冻结页无法外部核实 GitHub 仓库当前是否可访问、是否含完整可复现脚本与数据。
- AlphaFold2/ColabFold 预测结构与真实膜环境构象可能存在偏差。

## Pi 结构化证据摘录

- **baseline：** 独立测试对比覆盖 IAMPE-KNN/RF/SVM/XGBOOST、AMP Scanner vr.2、iAMPpred、ADAM、Deep-ABPpred、amPEPpy、AMPDLMD、UniDL4BioPep、sAMPpred-GAT、AMPpred-MFA 和 KNIME-best fused-feature model。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.5]
- **baseline：** 作者说明这些模型都在同一主数据集上训练，部分结果来自原文，或是在随机初始化 10 次后取平均值。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.5]
- **data：** 主数据集 S 含 1635 ABPs 与 1485 non-ABPs，独立测试集 S_IN 含 4017 ABPs 与 5799 non-ABPs，且两者无重叠。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.2]
- **data：** 数据统计显示 ABPs 更富 α-helix、净正电荷更高，长度多集中在 15–25 aa，并富集 lysine、arginine、alanine 和 leucine。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.3]
- **declared_resources：** 论文声明 datasets 和 source codes 可在 https://github.com/moonseter/PGAT-ABPp/ 获取。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.1]
- **declared_resources：** 实现栈写明为 Keras 和 TensorFlow，结构预测依赖 ColabFold/AlphaFold2，特征提取依赖 ProtT5-XL-U50。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.1]；[doi:10.1093/bioinformatics/btae497, p.4]
- **limitations：** 作者承认 PLM 的选择会影响性能，且这种影响可能是 task-specific，后续更专用的生物 PLM 可能继续提升效果。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.8]
- **limitations：** 作者也指出预测结构来自水相条件，未必等同于膜环境构象；膜中结构可能更准确，但更难获得。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.8]
- **limitations：** 与序列直连方法相比，使用预测结构会带来额外计算开销。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.8]
- **method：** 作者把 ABP 定义为具有抗菌活性的 peptide，把无已知抗菌活性的 peptide 作为 non-ABP，并以 Deep-ABPpred 来源的数据集作为训练与独立测试基础。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.2]
- **method：** 他们用 ColabFold/AlphaFold2 预测全部序列的 3D 结构，再以 Cα 距离小于 10 Å 构造邻接矩阵与 contact map。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.3]；[doi:10.1093/bioinformatics/btae497, p.4]
- **method：** ProtT5-XL-U50 生成每个残基的 1024 维 embedding，GAT 经过多头注意力与 readout/global average pooling 后，再用 sigmoid 完成二分类。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.4]；[doi:10.1093/bioinformatics/btae497, p.5]
- **results：** 在独立测试集上，PGAT-ABPp 达到 Acc 96.49±0.21、Pr 95.31±0.51、Sp 96.72±0.38、AUC 0.9936±0.0007、Fs 0.9573±0.0025、MCC 0.9280±0.0042，作者声称均优于对比方法。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.5]
- **results：** 10-fold CV 的均值为 Acc 97.18±0.74、Pr 98.08±1.41、Sp 97.91±1.53、AUC 0.9882±0.0037、Fs 0.9728±0.0074、MCC 0.9437±0.0149。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.5]
- **results：** 消融实验显示 ProtT5-GAT 明显优于 Onehot-GAT、Word2vec-GAT 和 ProtT5-CNN，支持 ProtT5 与结构信息的增益。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.6]
- **results：** 注意力热图在 PGLa、Hepcidin-25、HNP-1、Magainin-2 上突出已知关键位点，作者据此主张模型具有一定可解释性。
  - 证据：[doi:10.1093/bioinformatics/btae497, p.7]

## 页码证据

- [doi:10.1093/bioinformatics/btae497, p.1]
- [doi:10.1093/bioinformatics/btae497, p.2]
- [doi:10.1093/bioinformatics/btae497, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
