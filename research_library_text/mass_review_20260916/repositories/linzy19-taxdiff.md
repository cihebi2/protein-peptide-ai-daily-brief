# linzy19/taxdiff

- **仓库：** [https://github.com/linzy19/taxdiff](https://github.com/linzy19/taxdiff)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT（代码）；数据集 CC-BY-NC 4.0
- **语言：** Python
- **复用度：** medium —— 推理脚本完整且条件生成（tax-id 标签）用法清晰，但仓库内权重为占位符需去 HF 下载，训练代码与训练数据未发布（待论文接收）
- **能力：** inference、data_loader

## 仓库摘要

TaxDiff：分类学（taxon）引导的蛋白质序列生成扩散模型（DiT 架构 + patchify attention），首个按分类学条件可控生成蛋白质序列的模型，arXiv 2024。仓库仅发布推理代码。

## 入口脚本

- sample_protein.py

## 数据加载

- data_reader/decoder.py
- data_reader/Taxonnmic_classfication.xlsx（tax-id 查询表）

## 模型权重

- ckpt/0012802_eval.pt 为 2 字节占位文件；真实权重与 UniRef50 训练 fasta 需从 HuggingFace linzy19/TaxDiff 下载

## 评测基准

- （无）

## 文档

- README.md
- imgs/

## 课题关联

- C007条件生成

## 与论文/课题的组合方式

- 与
- 条
- 件
- 生
- 成
- 课
- 题
- （
- C
- 0
- 0
- 7
- ）
- 组
- 合
- ：
- 下
- 载
-  
- H
- F
-  
- 权
- 重
- 后
- 用
-  
- s
- a
- m
- p
- l
- e
- _
- p
- r
- o
- t
- e
- i
- n
- .
- p
- y
-  
- 按
- 分
- 类
- 学
-  
- t
- a
- x
- -
- i
- d
-  
- 条
- 件
- 生
- 成
- 蛋
- 白
- 序
- 列
- ，
- 其
- '
- 离
- 散
- 条
- 件
- 标
- 签
- 引
- 导
- 扩
- 散
- '
- 的
- 控
- 制
- 器
- 设
- 计
- 可
- 直
- 接
- 迁
- 移
- 到
-  
- A
- M
- P
-  
- 条
- 件
- 活
- 性
- 生
- 成
- （
- C
- 0
- 0
- 1
- ）
- 的
- 条
- 件
- 模
- 块
- 。
