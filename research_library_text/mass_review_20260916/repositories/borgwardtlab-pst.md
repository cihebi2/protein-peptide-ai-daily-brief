# borgwardtlab/pst

- **仓库：** [https://github.com/borgwardtlab/pst](https://github.com/borgwardtlab/pst)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** BSD-3-Clause
- **语言：** Python
- **复用度：** high —— 训练/微调/表示提取管线完整，预训练权重可下载，下游任务数据由 torchdrug/proteinshake 拉取，配置化(Hydra)工程规范
- **能力：** data_loader、training_pipeline、inference、benchmark

## 仓库摘要

蛋白质结构变换器（PST）：用 GNN 结构提取器把 8Å 残基邻域结构信息注入 ESM-2 等预训练蛋白语言模型，得到结构感知的蛋白表示，支持 GO/EC 功能预测与表示提取。

## 入口脚本

- train_pst.py
- scripts/pst_extract.py
- experiments/fixed/predict_gearnet.py
- experiments/finetune/finetune_gearnet.py

## 数据加载

- pst/dataset.py
- scripts/example_dataset.py

## 模型权重

- README 提供 pst_t6/t12/t30/t33 及 struct-only 共 8 个预训练权重下载链接（MPG datashare）

## 评测基准

- experiments/fixed/
- experiments/finetune/
- experiments/baselines/

## 文档

- README.md

## 课题关联

- C004

## 与论文/课题的组合方式

- 作
- 为
-  
- E
- S
- M
- -
- 2
-  
- 的
- 结
- 构
- 增
- 强
- 替
- 代
- 骨
- 干
- ，
- 为
-  
- b
- i
- n
- d
- e
- r
- /
- P
- P
- I
- （
- C
- 0
- 0
- 4
- ）
- 或
-  
- A
- M
- P
-  
- 活
- 性
- 课
- 题
- 提
- 供
- 残
- 基
- 级
- 结
- 构
- 感
- 知
-  
- e
- m
- b
- e
- d
- d
- i
- n
- g
- ，
- 可
- 与
-  
- G
- e
- a
- r
- N
- e
- t
-  
- 基
- 线
- 直
- 接
- 对
- 比
- 。
