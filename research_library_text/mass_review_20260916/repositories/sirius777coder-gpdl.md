# sirius777coder/gpdl

- **仓库：** [https://github.com/sirius777coder/gpdl](https://github.com/sirius777coder/gpdl)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 三步设计管线完整（example.sh 参数详解）、内置 inpainting 权重、标准 motif-scaffolding 基准集与 benchmark notebook、免依赖 Colab；环境依赖 ESMFold/openfold 较重但资产齐全
- **能力：** inference、training_pipeline、benchmark、data_loader

## 仓库摘要

GPDL：蛋白质语言模型监督的 motif-scaffolding 设计方法，给定 motif 残基拓扑/序列生成全新高质量 scaffold 骨架，采用 seeding-固定骨架设计-优化三步 MCMC 流程，内置 ProteinMPNN fork 与 Colab notebook。发表于 Int J Biol Macromol 2025。

## 入口脚本

- example.sh
- sample_sequences.py
- GPDL_colab.ipynb
- gpdl_hallucination/inference_v1.py
- gpdl_hallucination/inference_v2.py

## 数据加载

- gpdl_inpainting/customize_data.py
- data/（fasta/pdb/esm_pdb_denovo 等）

## 模型权重

- gpdl_inpainting/checkpoints/inpaint_weight_11.pt（内置权重）

## 评测基准

- gpdl_inpainting/benchmark.ipynb
- gpdl_inpainting/benchmark_set/（1BCF/1PRW/1QJG/1YCR/2KL8/3IXT/4JHW/4ZYP/5IUS/5TPN 等 motif-scaffolding 标准基准 PDB）

## 文档

- README.md
- GPDL_colab.ipynb

## 课题关联

- C004 binder/PPI
- C008基准校准

## 与论文/课题的组合方式

- 与
- 蛋
- 白
- 设
- 计
- 课
- 题
- 组
- 合
- ：
- b
- e
- n
- c
- h
- m
- a
- r
- k
- _
- s
- e
- t
-  
- 可
- 直
- 接
- 用
- 作
-  
- m
- o
- t
- i
- f
- -
- s
- c
- a
- f
- f
- o
- l
- d
- i
- n
- g
- /
- 骨
- 架
- 设
- 计
- 课
- 题
- （
- 含
-  
- C
- 0
- 0
- 4
-  
- 功
- 能
- 位
- 点
- 保
- 持
- 设
- 计
- ）
- 的
- 统
- 一
- 评
- 估
- 集
- 并
- 与
-  
- R
- F
- d
- i
- f
- f
- u
- s
- i
- o
- n
-  
- 等
- 对
- 比
- ；
- G
- P
- D
- L
-  
- 三
- 步
- 管
- 线
- 可
- 作
- 为
-  
- s
- c
- a
- f
- f
- o
- l
- d
-  
- 生
- 成
- 基
- 线
- 。
