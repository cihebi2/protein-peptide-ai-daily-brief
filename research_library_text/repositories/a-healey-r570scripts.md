# a-healey/r570scripts

- **仓库：** [https://github.com/a-healey/r570scripts](https://github.com/a-healey/r570scripts)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1038/s41586-024-07231-4
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** R (R+Python 混合)
- **复用度：** medium —— 脚本通用性较好(作者明确声明面向一般多倍体基因组分析)且提供conda环境；但属于植物基因组学工具集，无ML组件，与肽/蛋白设计课题族无直接复用点。
- **能力：** data_loader、visualization

## 仓库摘要

甘蔗 R570 杂合多倍体基因组组装论文(Nature 2024)的配套分析脚本集(R/Python)：从 Illumina BAM 提取遗传标记、从 FASTA 提取唯一标记、minimap2/mummer 比对解析与可视化、GENESPACE 直系同源/祖先染色体分析。

## 入口脚本

- bedFileFromFai.py
- extractMarkersFromBam.py
- extractUniqueMarkersFromFasta.py
- parseMummerToPlot.py
- matchSeqs.R
- genespaceCommands.R
- r570_orthogroupProgenitorAnalysis_forSupp.ipynb

## 数据加载

- 各脚本自行读取 BAM/FASTA/.fai/PAF 输入(无打包数据)

## 模型权重

- （无）

## 评测基准

- （无）

## 文档

- README.md (逐脚本用法说明)
- R570_analysisEnv.yml (conda环境: minimap2/mummer/samtools/bedtools/biopython等)

## 课题关联

- 与课题族无直接关联(植物泛基因组组装领域)；仅可作为'论文配套脚本型仓库'的审计对照样本

## 与论文/课题的组合方式

- 作为 10.1038/s41586-024-07231-4 (R570甘蔗基因组) 补充材料的脚本载体，可配合论文SI复现图表；对 C001-C013/L/X 课题族组合价值可忽略
