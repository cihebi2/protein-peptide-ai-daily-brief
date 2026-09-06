# A sequence-based deep learning framework (PepInter) for protein–peptide interaction representation learning with pretrained protein language models

- **论文 ID：** `EVIW-0AE5BB88A44BC105`
- **期刊 / 来源：** Communications Chemistry（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1038/s42004-026-02168-3](https://doi.org/10.1038/s42004-026-02168-3)
- **范围标签：** `待 Pi 解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析待处理

## 作者主张的创新点

论文提出 PepInter，在 ESM Cambrian 上先做能量筛选的伪对预训练，再做 MLM 和实验数据微调。

## 创新边界

`not_global_prior_art_verified`。这不是全球首创性检索或独立复现结论。

## 研究问题

用大量结构导出的伪蛋白-肽对缓解真实标注稀缺，学习蛋白-肽相互作用和亲和力。

## 方法

- 从 PDB 蛋白复合物用 Rosetta PeptiDerive 提取能量主导片段，构建约 900 万伪对；两阶段预训练后分别做 PPI 分类和亲和力回归。

## 数据与基准

- ProtFragDB 约 898 万训练伪对、PepInterDB 分类集、PepAffDB 3670 个亲和力对和案例数据。

## 比较基线

- 传统 ML、PepBind/SPRINT-seq、PepGPL 等深度模型和不同数据切分。

## 结果证据

- 分类任务报告 ACC 0.85、AUC 0.94、AUPR 0.95，并在 novel protein/peptide/pair 切分比较；新相互作用仍是预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 伪对来自 bound-like 片段且依赖 Rosetta 能量；不表示折叠熵、环肽或非天然修饰，真实亲和力泛化仍待检验。

## 仍未知

- 跨修饰肽、外部亲和力实验和结构变化引起的长程结合模式仍未知。

## 页码证据

- [doi:10.1038/s42004-026-02168-3, p.10]
- [doi:10.1038/s42004-026-02168-3, p.15]
- [doi:10.1038/s42004-026-02168-3, p.1]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
