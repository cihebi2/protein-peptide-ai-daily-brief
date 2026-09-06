# Structure-enhanced deep learning accelerates aptamer selection for small molecule families like steroids

- **论文 ID：** `EVIW-89C54A6ECDC07E00`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2025 Dec 18
- **DOI：** [10.1093/bib/bbaf680](https://doi.org/10.1093/bib/bbaf680)
- **范围标签：** `待 Pi 解析` / `核心相关` / `论文声明资源` / `蛋白-配体`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析待处理

## 作者主张的创新点

论文提出 DL-SELEX：AptaVAE 用分子家族结构信息生成初始库，AptaClux 从 SELEX NGS 提取共识候选。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

通过深度学习设计初始 SELEX 文库并从 NGS 数据挑选候选，加速小分子适配体发现。

## 方法

- 用 DNABERT/ChemBERT 表征、VAE 与共注意力设计 steroid 文库；对 hydrocortisone/testosterone 做 SELEX、ITC、特异性、突变与 MD/docking。

## 数据与基准

- 既有 steroid aptamer、CS/TES 初始库与 HT-SELEX/NGS 数据。

## 比较基线

- 手工结构化文库、传统 SELEX 和既有 CS/TES aptamer。

## 结果证据

- 论文报告亲和力最高较既有 aptamer 提升 450 倍、SELEX 轮次最多减少 80%，并用 ITC 和点突变验证选定候选。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 仅在同一 steroid 家族的两个靶标验证；结构模拟和 docking 只支持机制假设，不能替代 ITC。

## 仍未知

- 跨化学家族、不同 SELEX 条件和更大前瞻实验的成功率未知。

## 页码证据

- [doi:10.1093/bib/bbaf680, p.13]
- [doi:10.1093/bib/bbaf680, p.1]
- [doi:10.1093/bib/bbaf680, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
