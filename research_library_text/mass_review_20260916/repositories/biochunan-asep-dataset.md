# biochunan/asep-dataset

- **仓库：** [https://github.com/biochunan/asep-dataset](https://github.com/biochunan/asep-dataset)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 完整管线：数据集有 Zenodo DOI 可一键下载，附带 devcontainer/conda 环境、训练与多基线评测脚本及汇总指标；开箱可复现基准
- **能力：** data_loader、training_pipeline、inference、benchmark

## 仓库摘要

AsEP：抗体特异性表位预测（Antibody-specific Epitope Prediction）基准数据集（NeurIPS 2024 D&B 投稿），提供 Python 数据接口（PLM+GNN 模型）、数据加载器及多个深度学习基线（EpiPred/ESMBind/ESMFold/MaSIF-site）的训练评测代码，原始数据托管于 Zenodo（DOI 10.5281/zenodo.11495514）。

## 入口脚本

- asep/train_model.py
- experiments/train-walle/train.py
- experiments/train-walle-epitope-group/train.py
- experiments/inference/evaluate_on_walle.py

## 数据加载

- asep/data/asepv1_dataset.py
- asep/app/download_dataset.py

## 模型权重

- 无内置权重；模型为仓库内 PLM+GNN 结构（asep/model/），数据经 asep/app/download_dataset.py 从 Zenodo 下载

## 评测基准

- experiments/EpiPred/evaluate.py
- experiments/ESMFold/evaluate.py
- experiments/MaSIF-site/evaluate.py
- experiments/inference/evaluate.sh
- experiments/*/metrics-summary.csv

## 文档

- README.md
- DataCard.md

## 课题关联

- C004 binder/PPI
- C008 基准校准
- C011 评估协议

## 与论文/课题的组合方式

- 配
- 合
-  
- A
- s
- E
- P
-  
- 论
- 文
- （
- a
- r
- X
- i
- v
- :
- 2
- 4
- 0
- 7
- .
- 1
- 8
- 1
- 8
- 4
- ）
- 复
- 现
- 抗
- 体
- -
- 抗
- 原
- 表
- 位
- 预
- 测
- 全
- 部
- 基
- 线
- ；
- 其
- 数
- 据
- 划
- 分
- 与
-  
- e
- p
- i
- t
- o
- p
- e
- -
- g
- r
- o
- u
- p
-  
- 划
- 分
- 可
- 直
- 接
- 作
- 为
-  
- C
- 0
- 0
- 4
-  
- b
- i
- n
- d
- e
- r
-  
- 评
- 测
- 协
- 议
- ，
- 也
- 可
- 作
- 为
- 多
- 方
- 法
- 基
- 准
- 校
- 准
- （
- C
- 0
- 0
- 8
- ）
- 的
- 现
- 成
- 案
- 例
