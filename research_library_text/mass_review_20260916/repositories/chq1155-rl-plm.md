# chq1155/rl-plm

- **仓库：** [https://github.com/chq1155/rl-plm](https://github.com/chq1155/rl-plm)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 三条任务管线代码完整（训练/生成/评测/分析），数据与 checkpoint 有官方 Google Drive 发布且带 SHA256 校验清单，任务级 README 齐全
- **能力：** training_pipeline、inference、benchmark、data_loader

## 仓库摘要

论文《The Forgetting-Learning Trade-off: Making Reinforcement Learning Work for Protein Language Models》官方代码，用 DPO/PPO/GRPO 对蛋白质语言模型做强化学习，覆盖抗菌肽生成（ProGen2 策略）、PhoQ 激酶突变优化（ESM 策略）和抗体 CDR 突变优化三条管线，并提供 pass@k、ESR、Dual-Reward ESR 等能力诊断指标。

## 入口脚本

- amp_design/dpo.py
- amp_design/ppo.py
- amp_design/grpo.py
- amp_design/progen2hf/run.py
- antibody_mutation/eval.py
- kinase_mutation/

## 数据加载

- amp_design/dataset.py
- antibody_mutation/dataset.py

## 模型权重

- 无内置权重；数据与预训练 checkpoint 经 Google Drive 分发（README 链接），ARTIFACTS.md 提供 SHA256 校验

## 评测基准

- analysis/metrics.py
- antibody_mutation/eval.py
- amp_design/progen2hf/eval.py

## 文档

- README.md
- ARTIFACTS.md
- amp_design/README.md
- analysis/README.md

## 课题关联

- C001 AMP条件活性
- C007 条件生成
- C004 binder/PPI
- C013 基线新颖性

## 与论文/课题的组合方式

- 结
- 合
- 论
- 文
- 用
-  
- A
- M
- P
-  
- 生
- 成
- 管
- 线
- 复
- 现
-  
- R
- L
-  
- 对
-  
- P
- L
- M
-  
- 的
- 能
- 力
- 扩
- 展
- /
- 收
- 缩
- 诊
- 断
- （
- E
- S
- R
- 、
- D
- u
- a
- l
- -
- R
- e
- w
- a
- r
- d
-  
- E
- S
- R
- ）
- ；
- 其
-  
- r
- e
- w
- a
- r
- d
-  
- h
- a
- c
- k
- i
- n
- g
-  
- 检
- 测
- 协
- 议
- 可
- 直
- 接
- 移
- 植
- 到
-  
- C
- 0
- 0
- 1
- /
- C
- 0
- 0
- 7
-  
- 的
- 条
- 件
- 活
- 性
- 生
- 成
- 评
- 测
- ，
- 作
- 为
- 奖
- 励
- 模
- 型
- 可
- 靠
- 性
- 的
- 校
- 准
- 基
- 线
