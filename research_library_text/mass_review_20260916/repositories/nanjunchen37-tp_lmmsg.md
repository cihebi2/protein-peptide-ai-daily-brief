# nanjunchen37/tp_lmmsg

- **仓库：** [https://github.com/nanjunchen37/tp_lmmsg](https://github.com/nanjunchen37/tp_lmmsg)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 训练/交叉验证/测试全管线 + 七个 AMP 数据集划分 + 训练好的 .pth 权重均在仓库内；但完整特征生成需另装 psiblast/hhsuite/nrdb90 等外部工具且环境较老（Python3.7+TF1.14），推理可直接用权重
- **能力：** data_loader、training_pipeline、inference、benchmark

## 仓库摘要

TP-LMMSG 是融合柔性氨基酸属性表征的语言模型引导图神经网络，用于肽功能预测（AMP/ACP/AVP 多数据集二分类）。节点特征结合 BLOSUM62、语言模型嵌入与氨基酸理化属性，发表于 Briefings in Bioinformatics 2024。

## 入口脚本

- train.py
- train_cv.py
- test.py
- run.sh

## 数据加载

- generate_features_hmm.py
- generate_features_no_hmm.py
- node_embed/data_processing.py
- node_embed/featurization.py
- node_embed/LM_embedding.py
- node_embed/multi_label_feature.py

## 模型权重

- saved_models/models/*.pth（训练好的 GNN 检查点已随仓库分发）
- node_embed/seq2vec_pretrain_model/（预训练 LM 占位目录，需按 model_files/model_files.md 下载）

## 评测基准

- data/（APD3/CAMP/dbAMP/DRAMP/LAMP/XU/YADAMP 七个 AMP 数据集 train/test 划分 + cv_data 中 ACP/AVP 数据）
- test_results/test_results.md

## 文档

- readme.md
- data/data_format.md
- model_files/model_files.md
- tp_pre.yml
- tp_lmmsg.yml

## 课题关联

- C001
- C008
- C011
- C013

## 与论文/课题的组合方式

- C001 AMP 活性课题的强基线与数据源：七数据集划分可直接用作 C008 基准校准的统一评测床，TP-LMMSG 及其 .pth 权重可作 C013 基线新颖性对比对象；ACP/AVP 数据可支撑 C003 多端点扩展。
