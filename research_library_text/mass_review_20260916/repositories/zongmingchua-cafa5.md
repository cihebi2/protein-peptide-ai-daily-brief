# zongmingchua/cafa5

- **仓库：** [https://github.com/zongmingchua/cafa5](https://github.com/zongmingchua/cafa5)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— pip 安装 + Kaggle 数据（含预计算嵌入，可跳过嵌入再生）+ CLI 三命令完整训练预测合并流程，含 pytest 测试与详尽文档
- **能力：** data_loader、training_pipeline、inference、benchmark、database、protocol

## 仓库摘要

PROTGOAT：CAFA5 蛋白功能预测竞赛第 4 名方案，融合 5 个蛋白语言模型嵌入 + 物种分类学 + PubMed 摘要 TF-IDF 文献特征，按 BPO/CCO/MFO 三个 GO 本体分别训练 25 网络集成。

## 入口脚本

- src/protgoat/cli.py（protgoat-train / protgoat-predict / protgoat-merge 命令）
- pyproject.toml

## 数据加载

- src/protgoat/data.py
- src/protgoat/embeddings/plm.py
- src/protgoat/embeddings/abstracts.py

## 模型权重

- 已发布嵌入与目标矩阵经 Kaggle 数据集 zmcxjt/cafa5-train-test-data 下载；checkpoint 为 .hdf5（TF<2.16）

## 评测基准

- src/protgoat/submission.py（CAFA TSV 提交格式）
- tests/（pytest 套件）

## 文档

- README.md
- docs/model.md
- docs/data.md
- notebooks/archive/（竞赛原始 notebook）

## 课题关联

- C005
- C011
- C003

## 与论文/课题的组合方式

- C
- 0
- 0
- 5
-  
- 功
- 能
- /
- 表
- 型
- 注
- 释
- 课
- 题
- 的
- 多
- 模
- 态
- 融
- 合
- （
- 序
- 列
-  
- P
- L
- M
-  
- +
-  
- 文
- 献
-  
- T
- F
- -
- I
- D
- F
- ）
- 范
- 式
- 可
- 直
- 接
- 复
- 现
- ；
- 其
- 按
- 本
- 体
- 分
- 域
- 训
- 练
-  
- +
-  
- C
- A
- F
- A
-  
- 提
- 交
- 格
- 式
- 生
- 成
- 是
-  
- C
- 0
- 1
- 1
-  
- 评
- 估
- 协
- 议
- 课
- 题
- 的
- 成
- 熟
- 参
- 照
- （
- F
- m
- a
- x
-  
- 评
- 测
- ）
- 。
