# hive-uoft/prodcarl

- **仓库：** [https://github.com/hive-uoft/prodcarl](https://github.com/hive-uoft/prodcarl)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.48550/arxiv.2602.00157
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— SFT→RL对齐→生成打分的完整管线可单脚本复现，且附带可直接复用的 AMP/毒性两个预训练分类头权重与 APD3 数据，baselines 目录提供消融对照；缺点是无 LICENSE 且需自行准备 positive_samples.fasta。
- **能力：** training_pipeline、inference、benchmark、data_loader

## 仓库摘要

ProDCARL：将离散扩散模型 EvoDiff OA-DM 38M 先在已知 AMP 上监督微调，再用 top-k REINFORCE 强化学习按复合奖励 (pAMP+(1-pTox))^2 对齐，端到端生成 30 残基抗微生物肽；奖励来自 ProtT5-XL 嵌入上的 CNN+Self-Attention 分类头。

## 入口脚本

- run.py
- baselines/exp_prodcarl.py
- baselines/exp_base.py
- baselines/exp_ft.py
- baselines/exp_rl.py
- classifiers/amp_tox_classifiers.ipynb

## 数据加载

- classifiers/data/animalAMPs_APD2024a.fasta.txt
- classifiers/data/naturalAMPs_APD2024a.fasta.txt

## 模型权重

- classifiers/weights/best_toxic_model.pt (预训练毒性分类头)
- classifiers/weights/head_only.pt (预训练AMP分类头)
- ProtT5-XL (Rostlab/prot_t5_xl_half_uniref50-enc) 运行时从 HuggingFace 自动下载

## 评测基准

- baselines/ (base/微调/RL 对比实验)
- run.py 内置批量生成+打分输出 results/prodcal.csv

## 文档

- README.md

## 课题关联

- C001 AMP条件活性(AMP分类器+条件生成奖励)
- C002 肽毒性(毒性分类头与联合奖励)
- C007 条件生成(扩散+RL条件化生成)
- L4 肽生成
- L5 肽优化
- X06 优化(REINFORCE+熵正则策略优化)

## 与论文/课题的组合方式

- 与 arXiv:2602.00157 一一对应：run.py 复现论文主实验(40步RL、batch 200、top-30%、熵系数3.0)
- 其 pAMP/pTox 双分类头可作为 C001/C002 课题的现成评估器，用于给其他生成器(如 RFdiffusion 输出)打分
- EvoDiff SFT→RL 对齐范式可作为 L4/L5 肽生成-优化课题的基线方法与消融起点(baselines/exp_ft.py vs exp_rl.py)
