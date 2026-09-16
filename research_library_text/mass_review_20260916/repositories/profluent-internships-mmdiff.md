# profluent-internships/mmdiff

- **仓库：** [https://github.com/profluent-internships/mmdiff](https://github.com/profluent-internships/mmdiff)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 训练/采样/评测完整闭环 + Zenodo 预训练检查点 + 数据构建 notebook；需自编译 US-align/qTMclust 与 RF2NA 环境用于评测
- **能力：** training_pipeline、inference、benchmark、data_loader

## 仓库摘要

MMDiff（NeurIPS MLSB 2023，Profluent）用 SE(3)-离散扩散联合生成核酸-蛋白复合物的序列与结构；Hydra+Lightning 工程模板，内置 ProteinMPNN 与 RoseTTAFold2NA fork 用于评测，Zenodo 提供预训练检查点。

## 入口脚本

- src/train.py
- src/sample.py
- configs/train.yaml
- configs/sample.yaml
- scripts/schedule.sh

## 数据加载

- src/data
- configs/data
- notebooks/creating_protein_na_datasets_from_the_pdb.py
- metadata/PDB_NA_Dataset.csv

## 模型权重

- checkpoints/（空目录，从 Zenodo DOI 10.5281/zenodo.8247932 下载 MMDiff_Release_Checkpoints.tar.gz）

## 评测基准

- eval_results/collect_eval_results.py
- eval_results/analyze_eval_results.py
- eval_results/analyze_grouped_eval_results.py
- tests/test_eval.py
- forks/RoseTTAFold2NA（结构评分）
- forks/ProteinMPNN（序列评分）

## 文档

- README.md（数据准备→聚类→训练→采样评测全流程文档）
- environment.yaml

## 课题关联

- C007
- C004

## 与论文/课题的组合方式

- C
- 0
- 0
- 7
-  
- 条
- 件
- 生
- 成
- 课
- 题
- 的
- 理
- 想
- 工
- 程
- 骨
- 架
- ：
- S
- E
- (
- 3
- )
- -
- 离
- 散
- 扩
- 散
- 实
- 现
-  
- +
-  
- H
- y
- d
- r
- a
-  
- 配
- 置
- 体
- 系
-  
- +
-  
- R
- F
- 2
- N
- A
- /
- P
- r
- o
- t
- e
- i
- n
- M
- P
- N
- N
-  
- 评
- 测
- 闭
- 环
- ，
- 可
- 直
- 接
- 改
- 造
- 为
- 蛋
- 白
- -
- 配
- 体
- /
- b
- i
- n
- d
- e
- r
-  
- 条
- 件
- 生
- 成
- ；
- 其
-  
- P
- D
- B
-  
- 复
- 合
- 物
- 数
- 据
- 构
- 建
- 流
- 程
- 亦
- 可
- 复
- 用
- 于
-  
- C
- 0
- 0
- 4
-  
- 数
- 据
- 集
- 工
- 程
- 。
