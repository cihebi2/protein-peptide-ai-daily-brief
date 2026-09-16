# 1anj/deepmolm

- **仓库：** [https://github.com/1anj/deepmolm](https://github.com/1anj/deepmolm)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **语言：** Python
- **复用度：** medium —— 训练/微调/评测/推理脚本与 LLaVA 代码框架完整、许可证友好，但权重与数据目录均为空，需自备 Qwen2-VL-7B 底座和分子-文本数据集
- **能力：** training_pipeline、inference、data_loader、benchmark、visualization

## 仓库摘要

DeepMoLM：多模态分子大语言模型，融合高分辨率 2D 分子图像（SAM+CLIP DeepEncoder）与 3D 几何指纹（E3FP）经 Cross-Attention Fusion Projector 投影到 Qwen2-VL-7B，用于分子描述生成与性质预测。基于 LLaVA 训练框架，两阶段（对齐+generalist/specialist 微调）。

## 入口脚本

- scripts/train_molm.py
- scripts/infer.py
- scripts/run_stage1_align.sh
- scripts/run_stage2_finetune_chebi20.sh
- scripts/run_stage2_finetune_specialist_pubchem_prop.sh
- scripts/eval/run_eval.sh

## 数据加载

- scripts/data_preparation.py
- scripts/data_conversion.py
- llava/data/

## 模型权重

- checkpoints/ 与 data/ 目录为空；底座 Qwen2-VL-7B 与各阶段权重需自备（无直链）

## 评测基准

- scripts/eval/eval_molm.py
- scripts/eval/eval_molm_distributed.py
- scripts/eval/run_eval.sh
- scripts/eval/parse_results.py（ChEBI-20 分子 caption 等评测）

## 文档

- README.md（含架构图与训练流程）
- demo/
- imgs/

## 课题关联

- C003多端点
- C005表型

## 与论文/课题的组合方式

- 与
- 多
- 端
- 点
- /
- 表
- 型
- 课
- 题
- 组
- 合
- ：
- 其
-  
- p
- u
- b
- c
- h
- e
- m
-  
- 性
- 性
-  
- s
- p
- e
- c
- i
- a
- l
- i
- s
- t
-  
- 微
- 调
- 脚
- 本
- 可
- 改
- 造
- 为
- 多
- 端
- 点
- 性
- 质
- 预
- 测
- 的
- 多
- 任
- 务
-  
- L
- L
- M
-  
- 基
- 线
- ；
- C
- h
- E
- B
- I
- -
- 2
- 0
-  
- c
- a
- p
- t
- i
- o
- n
-  
- 评
- 测
- 协
- 议
- 可
- 复
- 用
- 于
- 分
- 子
- 文
- 本
- 生
- 成
- 评
- 估
- 。
