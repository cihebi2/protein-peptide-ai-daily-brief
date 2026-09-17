# ntranoslab/esm-variants

- **仓库：** [https://github.com/ntranoslab/esm-variants](https://github.com/ntranoslab/esm-variants)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1038/s41588-023-01465-0
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 变体效应打分 CLI 开箱即用；全部基准 CSV 含预测分数内置；DMS assay 集合可作 C008/C013 现成评测床；HF 门户可零安装查询。
- **能力：** inference、benchmark、data_loader、protocol

## 仓库摘要

Nature Genetics 论文官方仓库：ESM1b 全基因组错义变异效应打分工具 + ClinVar/gnomAD/DMS 完整基准（含预测分数）+ HF 在线查询门户。

## 入口脚本

- esm_score_missense_mutations.py
- esm_score_multi_residue_mutations.py

## 数据加载

- esm_variants_utils.py

## 模型权重

- fair-esm 依赖（ESM1b 权重自动下载）

## 评测基准

- benchmarks/ClinVar_gnomAD_benchmark_with_predictions.csv
- benchmarks/ClinVar_indel_benchmark_with_predictions.csv
- benchmarks/dms_assays.zip
- Table_of_results.xlsx

## 文档

- README.md

## 课题关联

- L2-蛋白语言模型（ESM1b 零样本 VEP 应用范本）
- C013-基线新颖性（零样本打分 vs 临床标签的评估协议）
- C008-基准校准（分数→致病概率的校准问题）
- C011-评估协议（ClinVar/gnomAD/DMS 三层基准）

## 与论文/课题的组合方式

- 与 plmeae（ESM zero-shot 适应度）构成同范式对照；其 ClinVar 阈值化协议可迁移到 AMP MIC 阈值评估；DMS zip 与 ProteinGym 互补作零样本基准池
