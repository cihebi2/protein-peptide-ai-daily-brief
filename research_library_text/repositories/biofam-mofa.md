# biofam/mofa

- **仓库：** [https://github.com/biofam/mofa](https://github.com/biofam/mofa)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1186/s43556-025-00340-0
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** LGPL-3.0
- **语言：** R（含 Python 后端 mofapy）
- **复用度：** medium —— R 包结构完整（NAMESPACE/man/vignettes 齐全）、PyPI 有 mofapy，但 v1 已被官方弃用（建议 MOFA2），reticulate 混合环境配置成本较高；作为论文基准中被比较方法的复现仍有直接价值。
- **能力：** training_pipeline、inference、visualization、data_loader

## 仓库摘要

MOFA（Multi-Omics Factor Analysis）v1：多组学数据无监督整合的因子分析模型，可视为 PCA 向多组学的推广，学习跨模态潜在因子并支持下游可视化、缺失值填补与富集注释。R 包前端 + Python（mofapy）变分推断后端。官方已标记弃用并建议迁移到 MOFA2。

## 入口脚本

- R/runMOFA.R
- R/createMOFA.R
- mofapy/core/entry_point.py
- mofapy/run/

## 数据加载

- R/createMOFA.R
- R/prepareMOFA.R
- R/loadModel.R

## 模型权重

- 无内置权重；训练产物由 R/loadModel.R 加载；示例数据在独立包 bioFAM/MOFAdata（install_github 获取）

## 评测基准

- （无）

## 文档

- README.md
- vignettes/MOFA.Rmd
- vignettes/MOFA_example_CLL.Rmd
- vignettes/MOFA_example_scMT.Rmd
- vignettes/MOFA_example_simulated.Rmd
- man/

## 课题关联

- C008基准校准（多组学集成方法基准比较论文的被评方法之一）
- C011评估协议（多模态方法横向比较协议）
- C005表型（多组学表型/亚群发现）

## 与论文/课题的组合方式

- 与 DOI 10.1186/s43556-025-00340-0（多组学数据集成方法系统比较论文）组合：作为 MOFA/GFA/JIVE/SLIDE/iNMF 方法族中的一员复现基准实验；用 vignettes 的 CLL/mRNA 单细胞示例熟悉输入格式后，接入论文统一的仿真与 TCGA-BRCA 数据协议。
