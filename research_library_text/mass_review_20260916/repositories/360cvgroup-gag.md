# 360cvgroup/gag

- **仓库：** [https://github.com/360cvgroup/gag](https://github.com/360cvgroup/gag)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** medium —— 三阶段（DAPT→专家SFT→注入训练）+路由评测代码与配置齐全，数据集有 HuggingFace 版本，但基座模型与本地目录布局需自备组装；依赖栈较重（Qwen3+多嵌入模型）
- **能力：** training_pipeline、inference、data_loader、benchmark

## 仓库摘要

GAG（arXiv 2601.08209）：Generation-Augmented Generation——将私有领域专业知识视为辅助模态，通过多槽潜记忆、逐槽跨层融合与门控残差投影注入冻结基座 LLM（Qwen3），并附 PPR 原型即插即用路由支持混合域部署；在催化材料与免疫佐剂两个科学私域 QA 基准上评测。

## 入口脚本

- src/domain_adaptation/continue_pretrain.py
- src/domain_adaptation/train_domain_expert_sft.py
- src/language_modeling/train.py
- scripts/run_adjuvant_sft.sh
- scripts/run_material_stage3.sh

## 数据加载

- src/data_pipeline/
- config/data_pipeline/*.yaml

## 模型权重

- 无内置权重；基座模型需自备 Qwen3-1.7B/8B、scibert、all-mpnet（README 目录约定），数据集在 HuggingFace rongjili/GAG

## 评测基准

- src/eval/compute_generation_metrics.py
- src/eval/oracle_gag/
- src/eval/ppr/
- config/gag_eval/*.yaml

## 文档

- README.md
- config/
- scripts/

## 课题关联

- C010 校准弃权

## 与论文/课题的组合方式

- 按
- 论
- 文
- 复
- 现
- 材
- 料
- /
- 佐
- 剂
- 双
- 域
-  
- Q
- A
-  
- 与
- 混
- 合
- 域
- 路
- 由
- 基
- 准
- ；
- 其
-  
- P
- P
- R
-  
- 原
- 型
- 路
- 由
- 的
- 可
- 靠
- 选
- 择
- 性
- 激
- 活
- 机
- 制
- 与
-  
- C
- 0
- 1
- 0
-  
- 的
- 弃
- 权
- /
- 选
- 择
- 性
- 预
- 测
- 同
- 构
- ，
- 可
- 作
- 为
- 混
- 合
- 专
- 家
- 场
- 景
- 下
-  
- a
- b
- s
- t
- e
- n
- t
- i
- o
- n
-  
- 策
- 略
- 的
- 方
- 法
- 参
- 照
