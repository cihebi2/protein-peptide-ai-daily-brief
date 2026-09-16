# haddocking/haddock3-paper-data

- **仓库：** [https://github.com/haddocking/haddock3-paper-data](https://github.com/haddocking/haddock3-paper-data)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **语言：** Python
- **复用度：** medium —— 四个 docking 工作流的输入数据、配置文件与分析脚本齐全，但需另行安装 HADDOCK3 软件本体才能复现 docking 运行。
- **能力：** data_loader、benchmark、visualization、protocol

## 仓库摘要

HADDOCK3 论文的配套数据仓库，包含四个用例工作流的输入数据与配置：抗体多界面靶向、蛋白-糖分子 docking、共识打分、复合物分析与热点残基检测（含 SKEMPI 对照）。

## 入口脚本

- complex-analysis/run_complex_analyses.sh
- antibody-patches-example/docking-4g6m-patches.cfg
- protein-glycan-example/unbound_vdw_na_clustrmsd.cfg

## 数据加载

- complex-analysis/compare_predictions.py
- protein-glycan-example/docking_run_analysis.py

## 模型权重

- 无模型权重；输入结构数据在各用例 data/ 目录（PDB、ambig.tbl、SKEMPI skempi_v2.csv 等）

## 评测基准

- complex-analysis/haddock3-alascan_VS_SKEMPI.csv
- consensus-scoring-example/emscoring.tsv
- consensus-scoring-example/voroscoring.tsv

## 文档

- README.md
- antibody-patches-example/README.md
- protein-glycan-example/README.md
- complex-analysis/README.md
- consensus-scoring-example/README.md

## 课题关联

- C16docking
- C004binder/PPI
- C011评估协议

## 与论文/课题的组合方式

- 配
- 合
-  
- H
- A
- D
- D
- O
- C
- K
- 3
-  
- 论
- 文
- 复
- 现
-  
- d
- o
- c
- k
- i
- n
- g
-  
- 工
- 作
- 流
- （
- 蛋
- 白
- -
- 糖
- 、
- 抗
- 体
- -
- 抗
- 原
- ）
- ；
- S
- K
- E
- M
- P
- I
-  
- 对
- 照
- 的
- 丙
- 氨
- 酸
- 扫
- 描
- 热
- 点
- 分
- 析
- 可
- 直
- 接
- 作
- 为
-  
- C
- 0
- 0
- 4
-  
- P
- P
- I
-  
- 热
- 点
- 预
- 测
- 课
- 题
- 的
- 评
- 估
- 基
- 准
- ；
- .
- c
- f
- g
-  
- 配
- 置
- 可
- 作
- 为
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
- 流
- 水
- 线
- 模
- 板
- 。
