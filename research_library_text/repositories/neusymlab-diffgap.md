# neusymlab/diffgap

- **仓库：** [https://github.com/neusymlab/diffgap](https://github.com/neusymlab/diffgap)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 训练/采样/评测全流程脚本与 pipeline 包装齐全，checkpoint 与评测元数据在 HuggingFace 发布；数据按 TargetDiff 流程自备（CrossDocked/PDBbind 需下载），conda 环境文件齐全。
- **能力：** data_loader、training_pipeline、inference、benchmark、visualization

## 仓库摘要

论文《Bridging the Gap between Learning and Inference for Diffusion-Based Molecule Generation》官方实现，改进扩散分子生成的学习-推理差距，内含 TargetDiff 与 BindDM 两个完整子项目（训练/采样/Vina docking 评测），并附 PDBbind 额外实验。

## 入口脚本

- pipeline.py
- binddm/pipeline.py
- targetdiff/pipeline.py
- dataset_prepare.py

## 数据加载

- binddm/datasets/pl_data.py
- binddm/datasets/pl_pair_dataset.py
- binddm/scripts/data_preparation/
- targetdiff/scripts/data_preparation/

## 模型权重

- checkpoint 与评测 meta 文件: HuggingFace Minter/DiffGap（README 提供）；targetdiff/pretrained_models/ 为空目录

## 评测基准

- binddm/scripts/evaluate_diffusion.py
- binddm/scripts/dock_testset.py
- binddm/scripts/male-es.py
- targetdiff/scripts/evaluate_diffusion.py

## 文档

- README.md
- binddm/README.md
- targetdiff/README.md
- env.yml

## 课题关联

- C007条件生成
- C16docking
- C011评估协议

## 与论文/课题的组合方式

- 配
- 合
-  
- a
- r
- X
- i
- v
-  
- 2
- 4
- 1
- 1
- .
- 0
- 5
- 4
- 7
- 2
-  
- 复
- 现
- 口
- 袋
- 条
- 件
- 分
- 子
- 生
- 成
- 与
-  
- V
- i
- n
- a
-  
- d
- o
- c
- k
- i
- n
- g
-  
- 评
- 测
- ；
- 其
-  
- H
- i
- g
- h
-  
- A
- f
- f
- i
- n
- i
- t
- y
- /
- D
- i
- v
- e
- r
- s
- i
- t
- y
- /
- J
- S
- D
-  
- 指
- 标
- 计
- 算
- 与
-  
- m
- e
- t
- a
-  
- 文
- 件
- 工
- 作
- 流
- 可
- 作
- 为
-  
- C
- 0
- 1
- 1
-  
- 分
- 子
- 生
- 成
- 评
- 估
- 协
- 议
- 模
- 板
- ，
- d
- o
- c
- k
- i
- n
- g
-  
- 评
- 测
- 脚
- 本
- 可
- 复
- 用
- 于
-  
- C
- 1
- 6
- 。
