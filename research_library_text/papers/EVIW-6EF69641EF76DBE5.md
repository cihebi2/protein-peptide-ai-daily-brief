# CaBind_MCNN: Identifying Potential Calcium Channel Blocker Targets by Predicting Calcium-Binding Sites in Ion Channels and Ion Transporters Using Protein Language Models and Multiscale Feature Extraction

- **论文 ID：** `EVIW-6EF69641EF76DBE5`
- **期刊 / 来源：** J Chem Inf Model
- **发表时间：** 2025 Feb 7
- **DOI：** [10.1021/acs.jcim.4c02252](https://doi.org/10.1021/acs.jcim.4c02252)
- **范围标签：** `待 Pi 解析` / `核心相关` / `论文声明资源` / `语言模型`
- **Pi 状态：** 已专家复核，等待 Pi 解析

## 作者主张的创新点

论文提出CaBind_MCNN，将蛋白语言模型与多尺度窗口卷积结合。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

识别离子通道和转运体中的钙结合位点，为阻断剂靶点筛选提供线索。

## 方法

- ProtTrans嵌入经多窗口CNN提取局部尺度特征并进行残基级分类。

## 数据与基准

- 使用结构与注释来源的钙结合残基数据集并进行独立测试。

## 比较基线

- 既有钙结合位点预测器、不同嵌入与窗口消融。

## 结果证据

- 论文报告在其基准上优于比较模型，并给出潜在阻断剂相关位点；结果为计算位点预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 标签数量、结构覆盖和负样本定义限制泛化；未证明候选位点可被药物阻断。

## 仍未知

- 对新型通道家族及药理选择性的外推未知。

## 页码证据

- [doi:10.1021/acs.jcim.4c02252, p.11]
- [doi:10.1021/acs.jcim.4c02252, p.1]
- [doi:10.1021/acs.jcim.4c02252, p.3]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
