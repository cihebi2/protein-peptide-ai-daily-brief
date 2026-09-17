# oxpig/calm

- **仓库：** [https://github.com/oxpig/calm](https://github.com/oxpig/calm)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1038/s42256-024-00791-0
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** BSD-3-Clause
- **语言：** Python
- **复用度：** high —— pip可安装(pyproject.toml, 版本0.1.2)，权重自动下载，7个基准数据集CSV随仓库内置，API极简(CaLM().embed_sequence)，可直接作为密码子级特征提取器嵌入任何蛋白/肽性质预测或优化流程
- **能力：** 密码子级DNA序列蛋白质语言模型嵌入、预训练权重自动下载、7类蛋白质性质预测基准(含数据)、序列嵌入提取(embed_sequence)、PyTorch训练管线(含checkpointing)

## 仓库摘要

CaLM（Codon adaptation Language Model）：在DNA密码子层面而非氨基酸层面训练的蛋白质语言模型。论文《Codon language embeddings provide strong signals for use in protein engineering》(Nature Machine Intelligence 2024, Outeiral & Deane) 的官方实现。代码包含模型本体、训练管线、预训练权重自动下载，以及论文使用的7类下游蛋白质性质预测基准数据（功能、亚细胞定位、熔解温度meltome、蛋白丰度、溶解度、物种识别、转录丰度），各以CSV形式随仓库分发。密码子级嵌入可捕获同义密码子偏好等氨基酸模型无法获取的信号。

## 入口脚本

- calm/pipeline.py (CaLM类, embed_sequence入口)
- training.py (预训练脚本)
- CaLM.ipynb (示例notebook)
- test_pipeline.py
- test_sequence.py

## 数据加载

- calm/dataset.py
- data_module.py
- calm/sequence.py
- calm/alphabet.py

## 模型权重

- calm/pretrained.py: 预训练权重 calm_weights.pkl 从 http://opig.stats.ox.ac.uk/data/downloads/calm_weights.pkl 自动下载缓存

## 评测基准

- data/function
- data/localization
- data/meltome (meltome_data.csv)
- data/protein_abundance
- data/solubility (solubility_data.csv)
- data/species
- data/transcript_abundance

## 文档

- README.md (安装与embed_sequence用法示例)

## 课题关联

- L2
- L3
- L5
- C003

## 与论文/课题的组合方式

- L2蛋白语言模型：作为与ESM/ProtT5等氨基酸级PLM对齐的密码子级PLM基线，比较嵌入在下游任务的迁移能力
- L3肽性质：其7个内置基准(溶解度、meltome、丰度等)可直接作为肽/蛋白性质预测的多端点评测协议
- C003多端点：仓库本身即论文多端点评估协议的落地实现，可复用其数据划分与评测管线
- L5肽优化：密码子级信号可用于表达优化导向的序列设计(同义密码子选择影响表达量)
