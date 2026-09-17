# grantlandwehr/accelerated-enzyme-engineering

- **仓库：** [https://github.com/grantlandwehr/accelerated-enzyme-engineering](https://github.com/grantlandwehr/accelerated-enzyme-engineering)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1038/s41467-024-55399-0
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python (Jupyter notebook)
- **复用度：** high —— 实验数据、零样本预测特征、训练/验证划分全部随仓库分发，两个notebook即完整复现入口，MIT许可证，代码量小依赖轻。增广MLDE范式（少量实验标签+零样本预测增广）可平移到任何蛋白/肽工程课题。
- **能力：** training_pipeline、inference、data_loader、database

## 仓库摘要

机器学习引导的加速酶工程（酰胺合成酶热点饱和突变+无细胞表达）：用ESM-1b/EVmutation/MAESTRO零样本预测作为增广特征，训练增广岭回归(AugmentedMLDE)模型筛选突变体。含全部实验适配度数据。

## 入口脚本

- notebooks/Model Selection.ipynb（模型选择主流程）
- notebooks/Extended Predictions.ipynb（扩展预测）
- src/AugmentedMLDE_Class.py（增广岭回归模型类）
- src/Predict_EVCouplings.py

## 数据加载

- src/AugmentedMLDE_HelperFuncs.py（辅助函数/数据读取）
- notebook内直接读取data/目录xlsx与csv

## 模型权重

- 无预训练权重；依赖外部零样本预测（ESM-1b/EVmutation/MAESTRO结果已存data/zero-shot_predictions/，无需重算）

## 评测基准

- data/ML_validation/（多底物train/test划分：metoclopramide/moclobemide/cinchocaine/declopramide/itopride/procainamide/sulpiride）
- data/HSS/（热点筛选实验数据）
- data/curated_reduced_AAs/

## 文档

- README.md
- environment.yml

## 课题关联

- L1蛋白设计（酶工程突变筛选直接相关）
- L2蛋白语言模型（ESM-1b零样本预测作为特征的实际用例与现成产出文件）
- L3肽性质（小样本回归建模范式）
- C008基准校准（ML验证train/test协议）
- C013基线新颖性（岭回归作为强基线+零样本基线对比）
- X06优化（ML引导的序列优化闭环）

## 与论文/课题的组合方式

- 配论文10.1038/s41467-024-55399-0：跑两个notebook即可完整复现模型选择与扩展预测；其data/zero-shot_predictions/是现成的ESM-1b/EVmutation零样本特征库，可直接作为L1/L3课题的基线特征或C013基线对比对象；AugmentedMLDE范式可直接移植到C004 binder优化或L4/L5肽序列的实验-学习闭环设计。
