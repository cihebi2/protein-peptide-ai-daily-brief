# kewei2023/ampcliff-generation

- **仓库：** [https://github.com/kewei2023/ampcliff-generation](https://github.com/kewei2023/ampcliff-generation)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— cliff 生成管线完整（生成+划分+相似度矩阵归一化），且仓库自带 GRAMPA S.aureus 数据与 BLOSUM62/Tanimoto 矩阵，conda 环境文件齐备，数据在本地即可复跑
- **能力：** data_loader、benchmark、database、protocol

## 仓库摘要

AMPCliff：定量定义并生成抗菌肽（AMP）'活性悬崖'配对基准的工具。以归一化 BLOSUM62 相似度≥0.9 且 MIC 变化≥2 倍定义 cliff，从 GRAMPA 数据集构建金黄色葡萄球菌 AMP cliff 基准，并含数据划分脚本。姊妹仓库 Kewei2023/AMPCliff 提供 17 种模型（ML/DL/掩码LM/生成式LM）的基准评测。

## 入口脚本

- generate_cliffs.py
- generate_cliffs.sh
- data_partition.py

## 数据加载

- fingerprint_2d.py
- similarity_matrix_normalization.py
- grampa_show.py

## 模型权重

- 无模型权重（数据集生成工具；基准评测模型代码在姊妹仓库 Kewei2023/AMPCliff）

## 评测基准

- data/grampa_s_aureus_7_25.csv
- data/blosum62_normalized.csv
- data/tanimoto_normalized.csv
- data_partition.py

## 文档

- README.md
- environment.yaml

## 课题关联

- C001
- C008
- C011
- C013

## 与论文/课题的组合方式

- C001 AMP 条件活性课题的核心资产：直接复用其 cliff 定义（BLOSUM62≥0.9 且 MIC 差≥2 倍）与基准数据做条件活性预测评估；生成管线可迁移到 C002 毒性/C003 多端点构造对应悬崖基准，配合姊妹仓库 AMPCliff 的 17 模型基线结果可校准新模型的真实增益。
