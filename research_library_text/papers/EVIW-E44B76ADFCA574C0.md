# MAPLE: interpretable deep learning identifies selective antimicrobial peptides using joint evolutionary–physicochemical analysis

- **论文 ID：** `EVIW-E44B76ADFCA574C0`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2026 Jun 17
- **DOI：** [10.1093/bib/bbag318](https://doi.org/10.1093/bib/bbag318)
- **范围标签：** `待 Pi 解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `语言模型` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析待处理

## 作者主张的创新点

论文提出MAPLE，融合PLM embedding与显式physicochemical descriptors并给出motif解释。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

在严重不平衡数据下同时识别AMP、选择性、hemolysis和功能类别。

## 方法

- 序列PLM和理化分支联合训练多任务预测头，使用不平衡目标和motif attribution。

## 数据与基准

- AMP benchmark与sequence-non-overlapping独立验证，包含低prevalence临床相关endpoint。

## 比较基线

- PLM-only、descriptor-only及既有AMP/hemolysis predictors。

## 结果证据

- 论文报告独立集各任务表现均衡并超过代表性基线；为计算优先级排序。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 标签多为binary、结构整合不完整，解释motif只是可检验假设。

## 仍未知

- 外部实验校准、结构模态和新病原体泛化未知。

## 页码证据

- [doi:10.1093/bib/bbag318, p.13]
- [doi:10.1093/bib/bbag318, p.1]
- [doi:10.1093/bib/bbag318, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
