# aalto-quml/tda_graph_product

- **仓库：** [https://github.com/aalto-quml/tda_graph_product](https://github.com/aalto-quml/tda_graph_product)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** medium —— 预处理→训练→表达力实验的代码完整（依赖 OGB/TUDataset 可自动下载），但无 LICENSE、部分 notebook 标注含 bug 的旧版本，与药物课题距离较远
- **能力：** training_pipeline、benchmark、data_loader

## 仓库摘要

NeurIPS 2025《On topological descriptors for graph products》官方仓库：研究持久同调（PH）与欧拉特征（EC）在图盒积上的表达能力，给出定理 4/5 的计算算法并在真实图分类数据集（NCI1 等）上做 GNN+拓扑特征实验。

## 入口脚本

- main.py
- train.py
- precompute_data.py

## 数据加载

- datasets.py

## 模型权重

- 无预训练权重

## 评测基准

- expressivity/run_brec.py
- expressivity/run_cayley.py
- notebooks/Theorem_4.ipynb
- notebooks/Theorem_5.ipynb

## 文档

- README.md
- notebooks/
- runtime/

## 课题关联

- （无）

## 与论文/课题的组合方式

- 拓
- 扑
- 描
- 述
- 子
- （
- P
- H
- /
- E
- C
- ）
- 可
- 作
- 为
- 分
- 子
- 图
- 特
- 征
- 的
- 增
- 强
- 项
- 尝
- 试
- 接
- 入
-  
- C
- 0
- 0
- 2
-  
- 肽
- 毒
- 性
- /
- C
- 0
- 0
- 3
-  
- 多
- 端
- 点
- 课
- 题
- 的
- 图
- 模
- 型
- ；
- 定
- 理
- 复
- 现
-  
- n
- o
- t
- e
- b
- o
- o
- k
-  
- 可
- 验
- 证
- 特
- 征
- 表
- 达
- 能
- 力
- 。
- 当
- 前
- 与
- 课
- 题
- 族
- 无
- 直
- 接
- 关
- 联
- ，
- 属
- 备
- 用
- 工
- 具
- 。
