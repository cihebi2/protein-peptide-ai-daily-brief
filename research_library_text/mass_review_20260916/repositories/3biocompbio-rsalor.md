# 3biocompbio/rsalor

- **仓库：** [https://github.com/3biocompbio/rsalor](https://github.com/3biocompbio/rsalor)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— pip 可装的成熟工具包，附 Colab notebook、CLI、Python API 与示例数据，开箱即用
- **能力：** inference、data_loader、visualization

## 仓库摘要

RSALOR（PyPI 包）：用溶剂可及性（RSA）× MSA 进化信号（LOR）的乘积评分预测蛋白错义突变效应，可自动获取/生成 MSA 与结构并输出 DMS 热图。

## 入口脚本

- rsalor/（CLI: rsalor fasta pdb chain -o out.csv；Python API: rsalor.MSA）
- colab_notebook_RSALOR.ipynb

## 数据加载

- rsalor/（内置 MSA/PDB 解析模块，支持 .fasta/.a2m/.a3m 与 .pdb/.cif）

## 模型权重

- 无神经网络权重（物理/进化评分方法，无需训练）

## 评测基准

- test_data/（内置示例 6acv_A fasta+pdb）

## 文档

- README.md
- pyproject.toml
- setup.py

## 课题关联

- C004

## 与论文/课题的组合方式

- 为
-  
- b
- i
- n
- d
- e
- r
- /
- P
- P
- I
- （
- C
- 0
- 0
- 4
- ）
- 或
- 活
- 性
- 改
- 造
- 类
- 课
- 题
- 提
- 供
- 零
- 训
- 练
- 的
- 突
- 变
- 效
- 应
- 先
- 验
- 评
- 分
- ：
- 可
- 作
- 为
-  
- D
- M
- S
-  
- 实
- 验
- 或
- 深
- 度
- 突
- 变
- 模
- 型
- 的
- 对
- 照
- 基
- 线
- ，
- 也
- 可
- 为
- 条
- 件
- 活
- 性
- 课
- 题
- （
- C
- 0
- 0
- 1
- ）
- 生
- 成
- 突
- 变
- 候
- 选
- 的
- 快
- 速
- 过
- 滤
- 分
- 。
