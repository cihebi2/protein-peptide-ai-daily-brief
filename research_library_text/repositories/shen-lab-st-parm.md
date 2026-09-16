# shen-lab/st-parm

- **仓库：** [https://github.com/shen-lab/st-parm](https://github.com/shen-lab/st-parm)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0（GPLv3 与商业双许可）
- **语言：** Python
- **复用度：** medium —— 训练/评测脚本齐全（slurm 脚本+trainer 实现），但数据与基座模型需从 Zenodo 下载，还依赖 safe-rlhf、TemBERTure 等多个外部仓库；存在较多 .backup/_old 版本文件，工程整洁度一般。
- **能力：** training_pipeline、inference、benchmark、data_loader

## 仓库摘要

ST-PARM 是基于 TRL/PEFT 与模型算术(language-model-arithmetic)的蛋白语言模型偏好/奖励训练框架，做带分数回归与课程学习的多目标序列设计，含 GFP 稳定性评测（TemBERTure、MosPro）与 Pareto 指标评估。

## 入口脚本

- code/training/train_st_parm.py
- code/training/train_st_parm_prollama.py
- code/training/train_pref_arm.py

## 数据加载

- code/data/relabel.py
- code/data/score_dataset_parallel.py
- MosPro/datasets/

## 模型权重

- ProLLaMA-GFP-merged 基座与数据在 Zenodo record 17850331（README 提供）；依赖外部 ProLLaMA/TemBERTure

## 评测基准

- code/evaluation/generate_outputs.py
- code/evaluation/compute_reward_GFP.py
- code/evaluation/pareto_metrics.py
- eval/eval_all_ckpts.sh

## 文档

- README.md
- requirements.txt

## 课题关联

- C003多端点
- C007条件生成
- C005表型

## 与论文/课题的组合方式

- P
- a
- r
- e
- t
- o
-  
- 指
- 标
- 与
- 多
- 目
- 标
- 奖
- 励
- 训
- 练
- 可
- 直
- 接
- 支
- 撑
-  
- C
- 0
- 0
- 3
-  
- 多
- 端
- 点
- 课
- 题
- 的
- 建
- 模
- 与
- 评
- 估
- ；
- G
- F
- P
-  
- 稳
- 定
- 性
- 条
- 件
- 生
- 成
- 流
- 程
- 可
- 迁
- 移
- 到
-  
- C
- 0
- 0
- 7
-  
- 与
-  
- C
- 0
- 0
- 5
-  
- 表
- 型
- 相
- 关
- 课
- 题
- 的
- 序
- 列
- 设
- 计
- 基
- 线
- 。
