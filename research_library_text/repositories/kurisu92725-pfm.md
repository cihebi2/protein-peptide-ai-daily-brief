# kurisu92725/pfm

- **仓库：** [https://github.com/kurisu92725/pfm](https://github.com/kurisu92725/pfm)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 训练/采样/评测全管线齐全，.pth 权重直接内置仓库，预处理数据有 Google Drive 下载链接，评测含 Vina docking
- **能力：** data_loader、training_pipeline、inference、benchmark

## 仓库摘要

Perturbed Flow Matching for Structure-Based Drug Design 官方实现：基于扰动流匹配的口袋条件 3D 分子生成，在 CrossDocked2020 上训练，用 AutoDock Vina 做 docking 评测。

## 入口脚本

- scripts/train_fm.py
- scripts/sample_fm.py
- scripts/evaluate_fm.py

## 数据加载

- datasets/pl_pair_dataset.py
- scripts/data_preparation/split_pl_dataset.py

## 模型权重

- model_params/pfm.pth
- model_params/h_predictor.pth
- model_params/x_predictor.pth（仓库内置训练权重）

## 评测基准

- utils/evaluation/eval_atom_type.py
- utils/evaluation/eval_bond_length.py
- scripts/evaluate_fm.py（--docking_mode vina_score 打分）

## 文档

- README.md
- requirements.txt

## 课题关联

- C007
- C16

## 与论文/课题的组合方式

- 可
- 直
- 接
- 复
- 用
- 其
- 『
- 生
- 成
- →
- 采
- 样
- →
- V
- i
- n
- a
-  
- 打
- 分
- 』
- 闭
- 环
- 作
- 为
-  
- C
- 0
- 0
- 7
-  
- 条
- 件
- 生
- 成
- 与
-  
- C
- 1
- 6
-  
- d
- o
- c
- k
- i
- n
- g
-  
- 课
- 题
- 的
- 基
- 线
- 方
- 法
- 与
- 评
- 测
- 脚
- 手
- 架
- ；
- E
- G
- N
- N
-  
- 主
- 干
- 也
- 可
- 迁
- 移
- 做
- 其
- 它
-  
- 3
- D
-  
- 生
- 成
- 任
- 务
- 。
