# cihebiyql/toxgin

- **仓库：** [https://github.com/cihebiyql/toxgin](https://github.com/cihebiyql/toxgin)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** medium —— 训练+预处理+推理代码完整并有测试样例，但训练/测试数据与结构文件需从 Google Drive 下载，新肽结构还需自行用 ColabFold 预测
- **能力：** data_loader、training_pipeline、inference

## 仓库摘要

ToxGIN 用图同构网络（GIN）预测肽毒性：以 ColabFold 预测的肽 3D 结构建图（残基为节点），融合 ESM2 序列特征与氨基酸理化性质，输出毒性概率。配套论文发表于 Briefings in Bioinformatics。

## 入口脚本

- train.py
- predict.py
- preprocess.py
- predict_preprocess.py

## 数据加载

- preprocess.py
- predict_preprocess.py
- predict_preprocess.ipynb

## 模型权重

- model/ 目录，README 指向 Google Drive 下载链接（数据/权重需外部下载，仓库内无权重文件）

## 评测基准

- predict.ipynb
- test_sequence.csv
- test_structures/

## 文档

- README.md
- model/README.md
- train_dataset/README.md
- test_dataset/README.md

## 课题关联

- C002
- C013

## 与论文/课题的组合方式

- ToxGIN 可直接作为肽毒性预测基线：用于 C002 课题作对比，其'ColabFold 结构→图 + ESM2 特征'的预处理管线可复用于 C003 多端点预测或 C001 AMP 活性模型的结构感知扩展。
