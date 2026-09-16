# merck/ablef

- **仓库：** [https://github.com/merck/ablef](https://github.com/merck/ablef)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **语言：** Python
- **复用度：** medium —— 预处理/聚类/训练/调参/holdout 代码链完整，但数据与权重均不在仓库；构象系综预处理依赖商业 MOE 或需自行搭建 ImmuneBuilder+OpenMM 开源管线
- **能力：** data_loader、training_pipeline、inference、visualization

## 仓库摘要

AbLEF（Merck，Bioinformatics 2024）融合抗体语言模型表示（AbLang/ProtBERT/ProtBERT-BFD）与 3D 构象系综的 LEF（CNN-transformer）表征，预测抗体热力学相关性质（如 hicrt、tagg）。

## 入口脚本

- src/train_tune.py（训练+Ray Tune 调参）
- src/holdout.py（留出集评测）
- clusters/main.py（DBSCAN 构象聚类）
- data/preprocess.py
- data/ensemble.py（OpenMM 系综生成）

## 数据加载

- src/DataLoader.py
- data/preprocess.py
- data/preprocess_graphs

## 模型权重

- README 提及 models/weights 下有 hicrt/tagg 已训模型，但仓库内无 models/ 目录（需联系作者）；ProtBERT/AbLang 语言模型需 git-lfs 安装到 config/

## 评测基准

- src/holdout.py

## 文档

- README.md
- alef.yml
- config/setup.json
- config/resprop.json

## 课题关联

- C004

## 与论文/课题的组合方式

- 用
- 于
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
- /
- 抗
- 体
- 课
- 题
- 的
- 可
- 开
- 发
- 性
- （
- 热
- 稳
- 定
- 性
- 、
- 聚
- 集
- 倾
- 向
- ）
- 预
- 测
- 环
- 节
- ：
- 先
- 设
- 计
- 后
- 过
- 滤
- ；
- 其
- 『
- 序
- 列
- 语
- 言
- 模
- 型
-  
- +
-  
- 结
- 构
- 系
- 综
- 融
- 合
- 』
- 思
- 路
- 可
- 迁
- 移
- 到
-  
- b
- i
- n
- d
- e
- r
-  
- 多
- 构
- 象
- 建
- 模
- ；
- 注
- 意
-  
- G
- P
- L
- -
- 3
- .
- 0
-  
- 传
- 染
- 性
- 对
- 组
- 合
- 分
- 发
- 的
- 限
- 制
- 。
