# aaandy-zhu/tablevlm

- **仓库：** [https://github.com/aaandy-zhu/tablevlm](https://github.com/aaandy-zhu/tablevlm)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** medium —— 推理与评测代码完整且内置 MMTab 测试集（6K/22K），但训练依赖 LlamaFactory 与自备 LVLM 基座，且领域为表格理解，与课题族无数据交集
- **能力：** inference、benchmark

## 仓库摘要

ICML 2026 Spotlight《Decoupling Skeleton and Flesh》官方实现：轻量多模态表格理解与推理框架，含 DiSCo（解耦结构-内容对齐）与 Table-GLS（全局到局部结构引导推理）两个组件，基于 LVLM 在 MMTab 基准上推理评测。与生物医药课题族无关联。

## 入口脚本

- DiSCo/scripts/run_mmtab_understanding.sh
- TableGLS/scripts/run_tablegls_stage1.sh
- TableGLS/scripts/run_tablegls_stage2.sh
- TableGLS/scripts/run_tablegls_stage3.sh

## 数据加载

- DiSCo/alignment_data/
- DiSCo/test_data/MMTab-eval_understanding_test_data_6K.json
- TableGLS/test_data/MMTab-eval_test_data_22K.json

## 模型权重

- 无内置权重；基座 LVLM 需自备（依赖 transformers/vllm/LlamaFactory 生态）

## 评测基准

- evaluation/MMTab_evaluation.py
- evaluation/eval.sh
- DiSCo/src/eval_mmtab_understanding.py
- TableGLS/src/eval_mmtab_vllm_tablegls_stage1-3.py

## 文档

- README.md

## 课题关联

- （无）

## 与论文/课题的组合方式

- 与
-  
- I
- C
- M
- L
-  
- 论
- 文
- 组
- 合
- 复
- 现
-  
- M
- M
- T
- a
- b
-  
- 表
- 格
- 理
- 解
- /
- 推
- 理
- 评
- 测
- ；
- 对
- 课
- 题
- 族
- 无
- 直
- 接
- 复
- 用
- 点
- ，
- 评
- 测
- 脚
- 本
- 组
- 织
- 方
- 式
- （
- 分
- 阶
- 段
-  
- e
- v
- a
- l
-  
- +
-  
- 独
- 立
-  
- e
- v
- a
- l
- u
- a
- t
- i
- o
- n
-  
- 目
- 录
- ）
- 可
- 作
- 工
- 程
- 参
- 考
