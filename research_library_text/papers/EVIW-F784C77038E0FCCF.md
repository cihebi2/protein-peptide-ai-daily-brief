# Identification of plant vacuole proteins by using graph neural network and contact maps

- **论文 ID：** `EVIW-F784C77038E0FCCF`
- **期刊 / 来源：** BMC Bioinformatics
- **发表时间：** 2023 Sep 22
- **DOI：** [10.1186/s12859-023-05475-x](https://doi.org/10.1186/s12859-023-05475-x)
- **范围标签：** `待 Pi 解析` / `可迁移方法` / `论文声明资源` / `图与几何学习` / `结构预测`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析待处理

## 作者主张的创新点

论文声称GraphIdn以SeqVec初始化残基，AlphaFold2接触图构图并用GCN分类。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

融合序列嵌入与AlphaFold2 contact map识别植物液泡蛋白。

## 方法

- 序列经SeqVec嵌入，预测结构转为contact adjacency，图卷积pooling后做二分类。

## 数据与基准

- 作者整理的植物液泡/非液泡蛋白训练测试及AlphaFold2结构。

## 比较基线

- 既有植物液泡蛋白序列预测器、无contact/不同表示消融。

## 结果证据

- 独立测试accuracy 88.51%，五折89.93%，优于所选预测器；仅为分类。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 性能受AlphaFold2 pLDDT影响；标签集/物种有限，亚细胞定位预测需实验验证。

## 仍未知

- 物种同源拆分与GitHub许可未复核。

## 页码证据

- [doi:10.1186/s12859-023-05475-x, p.17]
- [doi:10.1186/s12859-023-05475-x, p.1]
- [doi:10.1186/s12859-023-05475-x, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
