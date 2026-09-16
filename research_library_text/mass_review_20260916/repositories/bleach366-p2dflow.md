# bleach366/p2dflow

- **仓库：** [https://github.com/bleach366/p2dflow](https://github.com/bleach366/p2dflow)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 完整管线（数据处理/训练/推理/评测），提供预训练权重（Google Drive/HuggingFace）与预处理数据集（ATLAS selected_dataset）下载链接，conda 环境文件齐全，开箱可跑推理。
- **能力：** data_loader、training_pipeline、inference、benchmark、visualization

## 仓库摘要

P2DFlow 是基于 ESMFold 的 SE(3) 流匹配蛋白构象系综生成模型（JCTC 2024），可从序列生成蛋白结构系综以研究蛋白动力学与功能。

## 入口脚本

- experiments/train_se3_flows.py
- experiments/inference_se3_flows.py

## 数据加载

- data/pdb_dataloader.py
- data/process_pdb_files.py
- dataset/download.py
- dataset/traj_analyse_select.py

## 模型权重

- 预训练 checkpoint: Google Drive(README 提供) pretrained.ckpt → ./weights；HuggingFace: BLEACH366/P2DFlow

## 评测基准

- analysis/eval_result.py
- analysis/pca_analyse.py
- analysis/Ramachandran_plot.py
- analysis/metrics.py

## 文档

- README.md
- environment.yml

## 课题关联

- C007条件生成
- C011评估协议

## 与论文/课题的组合方式

- 配
- 合
- 作
- 者
-  
- J
- C
- T
- C
-  
- 2
- 0
- 2
- 4
-  
- 论
- 文
- 复
- 现
- 构
- 象
- 系
- 综
- 生
- 成
- ；
- 其
-  
- v
- a
- l
- i
- d
- i
- t
- y
- /
- f
- i
- d
- e
- l
- i
- t
- y
- /
- d
- y
- n
- a
- m
- i
- c
- s
-  
- 评
- 测
- 脚
- 本
- 可
- 作
- 为
-  
- C
- 0
- 1
- 1
-  
- 评
- 估
- 协
- 议
- 的
- 参
- 考
- 实
- 现
- ；
- S
- E
- (
- 3
- )
-  
- 流
- 匹
- 配
- +
- E
- S
- M
-  
- 表
- 征
- 的
- 数
- 据
- 处
- 理
- 链
- 可
- 为
- 条
- 件
- 生
- 成
- 类
- 课
- 题
- （
- C
- 0
- 0
- 7
- ）
- 提
- 供
- 管
- 线
- 模
- 板
- 。
