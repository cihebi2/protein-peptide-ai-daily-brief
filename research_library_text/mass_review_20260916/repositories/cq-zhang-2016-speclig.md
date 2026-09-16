# cq-zhang-2016/speclig

- **仓库：** [https://github.com/cq-zhang-2016/speclig](https://github.com/cq-zhang-2016/speclig)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 训练/推理/评测全流程代码完整，提供训练好的 checkpoint 下载（清华云盘），conda 环境文件齐全；数据集需按 datasets/README.md 下载（LNR、CrossDocked2020），推理开箱可跑。
- **能力：** data_loader、training_pipeline、inference、benchmark、visualization

## 仓库摘要

SpecLig 是能量引导的层级模型，面向靶点蛋白同时设计高亲和力/高特异性小分子与肽类 3D 配体（全原子 VAE + 块级潜在扩散），含完整训练/推理/评测代码。

## 入口脚本

- train.py
- generate.py

## 数据加载

- data/peptide.py
- data/molecule.py
- data/moleonly.py
- data/dataset_wrapper.py
- data/mmap_dataset.py
- scripts/data_process

## 模型权重

- 训练权重: 清华云盘 release(README 提供) checkpoints/model.ckpt

## 评测基准

- scripts/metrics/peptide
- scripts/metrics/mol.sh
- evaluation/dockq.py
- evaluation/energy.py
- evaluation/bsr.py
- evaluation/rmsd.py
- evaluation/diversity.py

## 文档

- README.md
- datasets/README.md
- env_cuda117.yaml
- env_cuda121.yaml

## 课题关联

- C004binder/PPI
- C007条件生成
- C16docking

## 与论文/课题的组合方式

- 配
- 合
-  
- S
- p
- e
- c
- L
- i
- g
-  
- 论
- 文
- 复
- 现
- 靶
- 点
- 条
- 件
- 下
- 的
- 肽
- /
- 小
- 分
- 子
- 配
- 体
- 设
- 计
- ；
- 其
-  
- p
- e
- p
- t
- i
- d
- e
-  
- 评
- 测
- 管
- 线
- （
- P
- y
- R
- o
- s
- e
- t
- t
- a
-  
- 界
- 面
- 能
- 、
- D
- o
- c
- k
- Q
- 、
- B
- S
- R
- ）
- 可
- 直
- 接
- 接
- 入
-  
- C
- 0
- 0
- 4
-  
- b
- i
- n
- d
- e
- r
-  
- 课
- 题
- 做
- 基
- 线
- 对
- 比
- ，
- 条
- 件
- 生
- 成
- 范
- 式
- 亦
- 可
- 支
- 撑
-  
- C
- 0
- 0
- 7
- ；
- d
- o
- c
- k
- q
- .
- p
- y
-  
- 可
- 用
- 于
-  
- C
- 1
- 6
-  
- d
- o
- c
- k
- i
- n
- g
-  
- 打
- 分
- 复
- 用
- 。
