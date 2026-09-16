# bytedance/decompdiff

- **仓库：** [https://github.com/bytedance/decompdiff](https://github.com/bytedance/decompdiff)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** CC BY-NC 4.0
- **语言：** Python
- **复用度：** high —— 训练/采样/评测三段式完整管线，CrossDocked 处理数据集与训练 checkpoint 均提供 Google Drive 下载；依赖较重（rdkit/openbabel/vina）但均可安装；注意 CC BY-NC 4.0 非商用许可
- **能力：** training_pipeline、inference、benchmark、data_loader、protocol

## 仓库摘要

DecompDiff（NeurIPS 2023）官方实现：基于分解先验（参考先验/β先验+口袋分解）的扩散模型，用于基于结构的药物设计（SBDD），按蛋白口袋生成 3D 分子，并以 Vina docking 等指标评测。

## 入口脚本

- scripts/train_diffusion_decomp.py
- scripts/sample_diffusion_decomp.py

## 数据加载

- datasets/pl_data.py
- datasets/pl_pair_dataset.py
- utils/preprocess.py

## 模型权重

- 训练好的 checkpoint 提供 Google Drive 下载链接（README 内，Drive folder 1JAB5pp...）；仓库内无权重文件

## 评测基准

- scripts/evaluate_mol_from_meta_full.py

## 文档

- README.md
- configs/training.yml
- configs/sampling_drift.yml

## 课题关联

- C007 条件生成
- C016 docking
- C008 基准校准

## 与论文/课题的组合方式

- 与
-  
- T
- a
- r
- g
- e
- t
- D
- i
- f
- f
- /
- P
- o
- c
- k
- e
- t
- 2
- M
- o
- l
-  
- 等
- 论
- 文
- 基
- 线
- 直
- 接
- 可
- 比
- ：
- 用
- 其
-  
- e
- v
- a
- l
- u
- a
- t
- e
- _
- m
- o
- l
- _
- f
- r
- o
- m
- _
- m
- e
- t
- a
- _
- f
- u
- l
- l
- .
- p
- y
-  
- 的
-  
- V
- i
- n
- a
-  
- 评
- 测
- 协
- 议
- 统
- 一
- 复
- 评
- 生
- 成
- 模
- 型
- ，
- 或
- 复
- 用
- 其
- 口
- 袋
- 条
- 件
- 扩
- 散
- 框
- 架
- 改
- 造
- 为
- 多
- 端
- 点
- 条
- 件
- 生
- 成
- （
- C
- 0
- 0
- 3
- /
- C
- 0
- 0
- 7
- ）
- 的
-  
- b
- a
- c
- k
- b
- o
- n
- e
- 。
