# zjufanlab/msformer

- **仓库：** [https://github.com/zjufanlab/msformer](https://github.com/zjufanlab/msformer)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 微调评测脚本 + 教程 notebook + 12 个内置 TDC 数据集 + 预训练权重 GDrive 链接 + 数据集版本表（COCONUT/MoleculeNet/TDC 0.4.1）齐全，可复现性强；仅缺 LICENSE
- **能力：** training_pipeline、inference、data_loader、benchmark、visualization

## 仓库摘要

MSformer：基于元结构（质谱启发碎片化）的天然产物分子表示学习模型，Transformer 层级编码，在 40 万天然产物（2.34 亿元结构）上预训练，在 14 个 MoleculeNet/TDC 基准上达 SOTA，支持片段级注意力归因可视化。发表于 Anal Chem 2025。

## 入口脚本

- run_classification_tdc.sh
- run_classification_molnet.sh
- msformer/MSFinetune.py

## 数据加载

- msformer/masskg.py（元结构/碎片生成）
- data/data/（12 个 TDC HTS 数据集内置：HIV、SARS-CoV-2 3CLpro、KCnQ2、毒蕈碱受体等 .tab）
- notebooks/download_tdc_datasets.ipynb

## 模型权重

- 预训练模型需从 Google Drive 下载（README 链接）；models/version_1795625 仅含训练日志与空 checkpoints

## 评测基准

- run_classification_molnet.sh（BBBP/Tox21/ClinTox/BACE/SIDER）
- run_classification_tdc.sh（10 个 TDC HTS 任务）

## 文档

- readme.md
- notebooks/Tutorial1.ipynb
- notebooks/download_tdc_datasets.ipynb

## 课题关联

- C002肽毒性
- C003多端点
- C005表型
- C008基准校准

## 与论文/课题的组合方式

- 与
- 多
- 端
- 点
- /
- 毒
- 性
- 课
- 题
- 组
- 合
- ：
- 内
- 置
-  
- T
- o
- x
- 2
- 1
- /
- C
- l
- i
- n
- T
- o
- x
- /
- H
- I
- V
- /
- T
- D
- C
- -
- H
- T
- S
-  
- 数
- 据
- 可
- 直
- 接
- 做
- 多
- 端
- 点
- 基
- 准
- ；
- M
- S
- f
- o
- r
- m
- e
- r
-  
- 可
- 作
- 为
- 分
- 子
- 表
- 示
- 基
- 线
- 与
-  
- G
- R
- O
- V
- E
- R
- /
- M
- o
- l
- B
- E
- R
- T
-  
- 对
- 比
- ，
- 注
- 意
- 力
- 归
- 因
- 可
- 视
- 化
- 支
- 持
- 活
- 性
- 片
- 段
- 解
- 释
- 。
