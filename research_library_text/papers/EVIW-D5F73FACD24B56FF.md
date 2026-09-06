# FlowPacker: protein side-chain packing with torsional flow matching

- **论文 ID：** `EVIW-D5F73FACD24B56FF`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2025 Jan 9
- **DOI：** [10.1093/bioinformatics/btaf010](https://doi.org/10.1093/bioinformatics/btaf010)
- **范围标签：** `待 Pi 解析` / `核心相关` / `论文声明资源` / `扩散/生成`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析待处理

## 作者主张的创新点

论文提出FlowPacker，以扭转角流匹配和等变图注意力进行侧链打包。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

在已知氨基酸序列和主链坐标时，快速准确预测侧链构象。

## 方法

- 在侧链扭转空间进行条件流匹配，使用等变图注意力编码序列与主链环境，并支持缺失侧链修复和多聚体。

## 数据与基准

- 训练采用BC40等PDB结构聚类数据，并在常规结构、抗体-抗原复合物和多聚体测试集评估。

## 比较基线

- DiffPack、AttnPacker以及传统搜索/打分侧链打包方法。

## 结果证据

- 论文报告多数指标优于DiffPack、AttnPacker等基线且推理更快；结果为结构重建指标，没有实验折叠验证。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 依赖给定主链质量；等变张量计算仍有复杂度，突变效应及柔性构象的准确性留待后续。

## 仍未知

- 对低质量主链、配体诱导构象和真实突变设计的效果未知。

## 页码证据

- [doi:10.1093/bioinformatics/btaf010, p.1]
- [doi:10.1093/bioinformatics/btaf010, p.3]
- [doi:10.1093/bioinformatics/btaf010, p.6]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
