# astraea2xu/uamrl

- **仓库：** [https://github.com/astraea2xu/uamrl](https://github.com/astraea2xu/uamrl)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** medium —— 训练管线完整（PyG 依赖明确），但需自备药物 .sdf 与靶点 .pdb 数据，无数据下载链接与预训练权重
- **能力：** data_loader、training_pipeline

## 仓库摘要

UAMRL：多粒度不确定性感知的多模态表示学习，用于药物-靶点亲和力（DTA）预测，输入为药物 .sdf 图表示与靶点 .pdb 距离矩阵。

## 入口脚本

- code/training.py
- code/create_drug_graph.py
- code/create_target_distance_matrix.py
- code/config.py

## 数据加载

- code/create_drug_graph.py
- code/create_target_distance_matrix.py

## 模型权重

- 无预置权重，需运行 code/training.py 自行训练

## 评测基准

- （无）

## 文档

- README.md
- code/README.md

## 课题关联

- C004

## 与论文/课题的组合方式

- 可
- 作
- 为
-  
- C
- 0
- 0
- 4
-  
- 药
- 物
- -
- 靶
- 点
- 亲
- 和
- 力
- 预
- 测
- 的
- 对
- 照
- 基
- 线
- ；
- 其
- 不
- 确
- 定
- 性
- 感
- 知
- 多
- 模
- 态
- 融
- 合
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
- /
- P
- P
- I
-  
- 亲
- 和
- 力
- 打
- 分
- 任
- 务
- ，
- 与
-  
- D
- T
- A
-  
- 论
- 文
- 结
- 果
- 对
- 照
- 复
- 现
- 。
