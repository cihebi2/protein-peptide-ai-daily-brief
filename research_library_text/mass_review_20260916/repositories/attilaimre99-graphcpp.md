# attilaimre99/graphcpp

- **仓库：** [https://github.com/attilaimre99/graphcpp](https://github.com/attilaimre99/graphcpp)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 完整训练/交叉验证/预测管线，独立测试集 CSV 与训练 checkpoint 均内置，含 environment.yml 与 Dockerfile，开箱可复现；但仓库无 LICENSE 文件
- **能力：** data_loader、training_pipeline、inference、benchmark、visualization

## 仓库摘要

GraphCPP 用图神经网络（GraphSAGE + PyTorch Lightning）预测细胞穿膜肽（CPP），发表于 Br. J. Pharmacol. 2025，附带 Streamlit 预测面板与 Docker 部署。

## 入口脚本

- main.py
- cv.py
- dashboard.py
- uncertainty.py
- config.py

## 数据加载

- graphcpp/dataset.py

## 模型权重

- model/checkpoints/epoch=22-step=69.ckpt（仓库内置训练权重）
- model/hparams.yaml
- model/metrics.csv

## 评测基准

- cv.py（默认10折交叉验证）
- notebooks/analyse_hp_search_metrics.ipynb
- notebooks/tsne.ipynb

## 文档

- README.md
- environment.yml
- cpu.yml
- predict.yml
- docker-commands.txt

## 课题关联

- C001
- C002

## 与论文/课题的组合方式

- 作
- 为
- 肽
- 活
- 性
- /
- 穿
- 膜
- 性
-  
- G
- N
- N
-  
- 基
- 线
- 与
-  
- C
- 0
- 0
- 1
- （
- A
- M
- P
- 条
- 件
- 活
- 性
- ）
- 、
- C
- 0
- 0
- 2
- （
- 肽
- 毒
- 性
- ）
- 课
- 题
- 的
- 预
- 测
- 器
- 对
- 比
- ；
- 其
- 内
- 置
- 独
- 立
- 测
- 试
- 集
- 与
-  
- 1
- 0
-  
- 折
-  
- C
- V
-  
- 脚
- 本
- 可
- 复
- 用
- 为
- 肽
- 性
- 质
- 评
- 测
- 协
- 议
- （
- 支
- 撑
-  
- C
- 0
- 1
- 1
- ）
- ，
- S
- t
- r
- e
- a
- m
- l
- i
- t
-  
- 面
- 板
- 可
- 复
- 用
- 为
- 课
- 题
- 组
- 预
- 测
- 演
- 示
- 界
- 面
- 。
