# yangling0818/binddm

- **仓库：** [https://github.com/yangling0818/binddm](https://github.com/yangling0818/binddm)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** medium —— 训练/采样/评测/docking 基线脚本完整（conda 环境文件齐备），但 CrossDocked 数据需按 TargetDiff 流程自备且无预训练权重
- **能力：** data_loader、training_pipeline、inference、benchmark、protocol

## 仓库摘要

BindDM（AAAI 2024）：结合自适应扩散模型用于基于结构的药物设计，从蛋白-配物复合物中抽取子复合物来增强口袋内 3D 分子生成的结合适配性。

## 入口脚本

- train.py
- sample.py
- evaluate.py
- scripts/train_diffusion.py
- scripts/sample_diffusion.py
- scripts/sample_for_pocket.py

## 数据加载

- datasets/pl_pair_dataset.py
- datasets/pl_data.py
- utils/data.py

## 模型权重

- 无预置权重；数据准备沿用 TargetDiff 仓库的 CrossDocked 处理流程

## 评测基准

- scripts/dock_baseline.py
- scripts/dock_testset.py
- scripts/evaluate_diffusion.py
- scripts/likelihood_est_diffusion.py

## 文档

- README.md
- binddm.yaml
- configs/

## 课题关联

- C016
- C004
- C008

## 与论文/课题的组合方式

- 可
- 与
-  
- C
- B
- G
- B
- e
- n
- c
- h
-  
- 组
- 合
- ：
- B
- i
- n
- d
- D
- M
-  
- 作
- 为
- 口
- 袋
- 条
- 件
-  
- 3
- D
-  
- 生
- 成
- 方
- 法
- 接
- 入
-  
- C
- B
- G
- B
- e
- n
- c
- h
-  
- 的
- 统
- 一
- 评
- 测
- （
- C
- 0
- 0
- 8
- /
- C
- 0
- 1
- 6
- ）
- ，
- 其
-  
- d
- o
- c
- k
- _
- b
- a
- s
- e
- l
- i
- n
- e
- /
- d
- o
- c
- k
- _
- t
- e
- s
- t
- s
- e
- t
-  
- 脚
- 本
- 可
- 复
- 用
- 为
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
- 估
- 协
- 议
- 组
- 件
- 。
