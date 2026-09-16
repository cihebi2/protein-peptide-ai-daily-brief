# dunni3/flowmol

- **仓库：** [https://github.com/dunni3/flowmol](https://github.com/dunni3/flowmol)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— MIT 许可，预训练权重运行时自动下载，test.py 一条命令采样+计算论文全套指标；QM9/GEOM 原始数据需自行下载但处理脚本齐全
- **能力：** training_pipeline、inference、benchmark、data_loader、visualization

## 仓库摘要

FlowMol3 官方实现：连续+离散（CTMC）流匹配模型，用于无条件 3D de novo 小分子生成，训练于 QM9/GEOM，附带分子生成质量评测（含 GFN2-xtb 能量优化评测）。

## 入口脚本

- train.py
- test.py

## 数据加载

- process_qm9.py
- process_geom.py
- get_data_valencies.py
- flowmol/（数据模块包内）

## 模型权重

- flowmol.load_pretrained() 运行时自动下载预训练模型至 flowmol/trained_models/；见 flowmol/trained_models/readme.md

## 评测基准

- dataset_metrics.py
- fm3_evals/（含 geometry/xtb_optimization.py、rmsd_energy.py）

## 文档

- readme.md
- qm9_guide.md
- fm3_evals/readme.md
- examples/flowmol_demo.ipynb

## 课题关联

- C007 条件生成
- C008 基准校准

## 与论文/课题的组合方式

- 作
- 为
-  
- 3
- D
-  
- 分
- 子
- 生
- 成
- 的
- 基
- 础
-  
- b
- a
- c
- k
- b
- o
- n
- e
- ：
- 在
- 其
- 流
- 匹
- 配
- 框
- 架
- 上
- 加
- 条
- 件
- 控
- 制
- （
- 口
- 袋
- /
- 活
- 性
- /
- 毒
- 性
- 端
- 点
- ）
- 可
- 支
- 撑
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
- 课
- 题
- ；
- 其
-  
- -
- -
- m
- e
- t
- r
- i
- c
- s
-  
- 与
-  
- f
- m
- 3
- _
- e
- v
- a
- l
- s
-  
- 指
- 标
- 栈
- 可
- 直
- 接
- 复
- 用
- 为
- 生
- 成
- 质
- 量
- 评
- 估
- 协
- 议
- （
- C
- 0
- 1
- 1
- ）
- 。
