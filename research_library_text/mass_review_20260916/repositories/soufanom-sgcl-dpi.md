# soufanom/sgcl-dpi

- **仓库：** [https://github.com/soufanom/sgcl-dpi](https://github.com/soufanom/sgcl-dpi)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **语言：** Python
- **复用度：** medium —— 特征生成→相似图构建→课程学习训练的代码链完整且有样例 CSV，但全量 STITCH 数据与 features.pkl 需自行生成/获取，无权重、无评测脚本
- **能力：** training_pipeline、data_loader、database

## 仓库摘要

SGCL-DPI：药物-蛋白相互作用（DPI）预测框架，融合药物/蛋白结构相似性图与 GCN，采用由易到难的课程学习策略提升泛化（数据源为 STITCH）。

## 入口脚本

- gcns/sgcl_dpi.py（主训练脚本）
- simgraphmaker/main.py

## 数据加载

- helpers/stitch_data_parser.py
- simgraphmaker/simgraphmaker.py
- simgraphmaker/feature_similarity_computer.py

## 模型权重

- 无预训练权重

## 评测基准

- （无）

## 文档

- README.md
- requirements.txt
- Data/SimilarityGraphs/（相似度图样例 CSV）

## 课题关联

- C004 binder/PPI

## 与论文/课题的组合方式

- 其
- 结
- 构
- 相
- 似
- 性
- 图
- +
- 课
- 程
- 学
- 习
- 的
- 思
- 路
- 可
- 用
- 于
-  
- C
- 0
- 0
- 4
-  
- 蛋
- 白
- -
- 配
- 体
- 结
- 合
- 预
- 测
- 的
- 基
- 线
- ；
- S
- T
- I
- T
- C
- H
-  
- 解
- 析
- 器
- 可
- 复
- 用
- 为
- 药
- 物
- -
- 蛋
- 白
- 配
- 对
- 数
- 据
- 构
- 建
- 工
- 具
- ，
- 配
- 合
- 多
- 端
- 点
- 课
- 题
- （
- C
- 0
- 0
- 3
- ）
- 做
- 特
- 征
- 工
- 程
- 。
