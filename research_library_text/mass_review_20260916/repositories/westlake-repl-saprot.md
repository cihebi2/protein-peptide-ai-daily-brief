# westlake-repl/saprot

- **仓库：** [https://github.com/westlake-repl/saprot](https://github.com/westlake-repl/saprot)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 全任务微调/评测框架代码完整（Hydra config 齐全），预训练权重（35M/650M/1.3B）在 HuggingFace 公开，且曾登顶 ProteinGym 公共榜单，是可直接复用的成熟基建
- **能力：** training_pipeline、inference、data_loader、benchmark

## 仓库摘要

SaProt 官方实现（ICLR 2024 spotlight，NBT 2025）：结构感知蛋白质语言模型，词表为氨基酸+Foldseek 3Di 结构 token，支持预训练/微调、零样本突变效应预测、蛋白嵌入、逆向折叠及十余种下游任务（ClinVar/DeepLoc/EC/GO/HumanPPI/MetalIonBinding/ProteinGym/Thermostability 等）。

## 入口脚本

- scripts/training.py
- bin/README.md

## 数据加载

- dataset/lmdb_dataset.py
- dataset/mutation_zeroshot_dataset.py
- dataset/saprot/saprot_classification_dataset.py
- dataset/saprot/saprot_ppi_dataset.py
- dataset/saprot/saprot_regression_dataset.py
- dataset/saprot/saprot_seq_design_dataset.py

## 模型权重

- 权重经 HuggingFace 分发：westlake-repl/SaProt_35M_AF2、SaProt_650M_PDB、SaProt_1.3B_AF2 等（README 列出），weights/PLMs/ 内为下载说明

## 评测基准

- config/ProteinGym/
- config/ClinVar/
- config/Contact/
- config/DeepLoc/
- config/EC/
- config/GO/
- config/HumanPPI/
- config/MetalIonBinding/
- config/Thermostability/

## 文档

- README.md
- example/
- config/
- environment.sh

## 课题关联

- C005 表型
- C004 binder/PPI
- C008 基准校准
- C011 评估协议
- C013 基线新颖性

## 与论文/课题的组合方式

- 按
-  
- I
- C
- L
- R
- /
- N
- B
- T
-  
- 论
- 文
- 在
-  
- P
- r
- o
- t
- e
- i
- n
- G
- y
- m
- 、
- C
- l
- i
- n
- V
- a
- r
- 、
- H
- u
- m
- a
- n
- P
- P
- I
-  
- 等
- 任
- 务
- 上
- 复
- 现
-  
- S
- a
- P
- r
- o
- t
-  
- 基
- 线
- ；
- 可
- 作
- 为
-  
- C
- 0
- 0
- 5
-  
- 表
- 型
- 预
- 测
- 与
-  
- C
- 0
- 0
- 4
-  
- P
- P
- I
-  
- 课
- 题
- 的
- 结
- 构
- 感
- 知
- 特
- 征
- 提
- 取
-  
- b
- a
- c
- k
- b
- o
- n
- e
- ，
- 其
- 零
- 样
- 本
- 突
- 变
- 效
- 应
- 评
- 测
- 流
- 程
- 可
- 直
- 接
- 接
- 入
-  
- C
- 0
- 0
- 8
- /
- C
- 0
- 1
- 1
-  
- 的
- 基
- 准
- 协
- 议
- 比
- 较
