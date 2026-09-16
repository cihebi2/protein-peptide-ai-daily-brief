# 3244we/question-rewriter

- **仓库：** [https://github.com/3244we/question-rewriter](https://github.com/3244we/question-rewriter)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none（顶层无 LICENSE；仅 direct-preference-optimization/ 子目录带原 DPO 仓库许可）
- **语言：** Python
- **复用度：** medium —— K-QA/OQA 路线代码与部分数据集齐备、DPO 训练配置完整，但 TruthfulQA 部分依赖未放出的 judge 模型、需 Llama3 HF 授权与 17-40GB 显存，data/ 结果目录为占位文件
- **能力：** training_pipeline、inference、data_loader

## 仓库摘要

Question-Rewriter（arXiv 2408.10573）：用 DPO 训练 LLM 问题改写器，通过改写用户问题提升下游回答质量与真实性，在 TruthfulQA/K-QA/OQA 三个问答集上实验；DPO 训练代码改自 eric-mitchell/direct-preference-optimization。

## 入口脚本

- original_kqa.py / original_oqa.py / original_tqa.py（生成原始答案）
- rewrite_kqa.py / rewrite_oqa.py / rewrite_tqa.py（改写生成）
- generate_dpo_kqa.py / generate_dpo_oqa.py / generate_dpo_tqa.py（构造 DPO 数据）
- direct-preference-optimization/train.py（DPO/SFT 训练，FSDP+LoRA）
- test_kqa.py / test_oqa.py / test_tqa.py

## 数据加载

- direct-preference-optimization/preference_datasets.py

## 模型权重

- 无内嵌权重：底座为 Llama3-8B（需 HF 授权）、Gemma/Mistral/Zephyr-7B/ChatGPT 接口；TruthfulQA judge 模型论文发表后才放出，相关代码暂缺

## 评测基准

- datasets/OQA/oasst1_{train,val,test}.csv
- datasets/TruthfulQA/finetune_{info,truth}.jsonl
- test_result/

## 文档

- README.md（分步复现命令）
- img/pps_new.png（方法图）
- requirements.txt（cuda 11.8/python3.8）

## 课题关联

- （无）

## 与论文/课题的组合方式

- 与
- 生
- 物
- 医
- 药
- 课
- 题
- 族
- 无
- 直
- 接
- 关
- 联
- ；
- 其
- '
- 改
- 写
- 输
- 入
- 以
- 改
- 善
- 下
- 游
- 回
- 答
- '
- 的
-  
- D
- P
- O
-  
- 流
- 程
- 方
- 法
- 论
- 上
- 可
- 迁
- 移
- 为
- 分
- 子
- 文
- 本
- 描
- 述
- 改
- 写
- /
- 提
- 示
- 优
- 化
- 的
- 参
- 照
- ，
- 但
- 属
- 间
- 接
- 借
- 鉴
- 。
