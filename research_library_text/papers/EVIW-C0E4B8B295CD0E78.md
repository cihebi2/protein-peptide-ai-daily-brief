# Multi-feature enhanced protein language models for accurate protein-RNA binding residue prediction

- **论文 ID：** `EVIW-C0E4B8B295CD0E78`
- **期刊 / 来源：** Discover Artificial Intelligence（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1007/s40747-025-02065-7](https://doi.org/10.1007/s40747-025-02065-7)
- **范围标签：** `待 Pi 解析` / `可迁移方法` / `论文声明资源` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析待处理

## 作者主张的创新点

论文提出MFEPre三通道CNN与fully connected feature fusion。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

融合序列PLM、结构图和手工特征预测protein-RNA binding residue。

## 方法

- ProtTrans嵌入、protein graph embedding及传统描述符分别编码，再融合进行残基分类。

## 数据与基准

- 公开protein-RNA binding训练/独立测试。

## 比较基线

- 单模态PLM/GNN/手工特征和不同GNN。

## 结果证据

- 论文报告测试AUROC 0.827并优于既有模型；为计算位点预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- GIN深层易过拟合/梯度消失，预测结构误差和binding-site imbalance限制泛化。

## 仍未知

- 新RNA类别、无结构输入和实验验证未知。

## 页码证据

- [doi:10.1007/s40747-025-02065-7, p.11]
- [doi:10.1007/s40747-025-02065-7, p.15]
- [doi:10.1007/s40747-025-02065-7, p.1]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
