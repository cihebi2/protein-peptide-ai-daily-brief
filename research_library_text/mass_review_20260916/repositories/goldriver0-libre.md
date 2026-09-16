# goldriver0/libre

- **仓库：** [https://github.com/goldriver0/libre](https://github.com/goldriver0/libre)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 训练/评测/推理脚本、已训练权重（model.pt）和示例数据齐备，管线开箱可跑；仅需自行生成 ESM 嵌入（脚本已提供）。小瑕疵：README 提到的顶层 run.py 未见、无 LICENSE、根目录残留 __pycache__
- **能力：** training_pipeline、inference、data_loader、benchmark

## 仓库摘要

LiBRe（Ligand-aware Binding Residue predictor）：基于序列的配体感知结合残基预测模型，融合 ESM 蛋白残基级嵌入与 RDKit/PyG 配体图特征，用 CNN-LSTM 预测蛋白序列上的配体结合残基。仓库附带已训练权重 model.pt（5.2MB）与示例训练/测试数据。

## 入口脚本

- src/train.py
- src/evaluate.py
- src/models/libre.py
- data/residue_embeddings.py（README 写作 residue_embedding.py，实际文件名稍异）
- data/ligand_featurizer.py

## 数据加载

- src/utils.py（特征载入）
- data/residue_embeddings.py
- data/ligand_featurizer.py

## 模型权重

- models/model.pt（已含训练好的权重，约 5.2MB）

## 评测基准

- src/evaluate.py（在测试集输出指标）
- data/test/test_example.csv

## 文档

- README.md
- docs/images/model_architecture.jpg

## 课题关联

- C004 binder/PPI（配体-蛋白结合残基/界面预测，可直接用作 binder 结合位点证据模块）
- C013基线新颖性（轻量 CNN-LSTM+配体特征可作为结合残基预测的简单基线）

## 与论文/课题的组合方式

- 与
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
- 课
- 题
- （
- C
- 0
- 0
- 4
- ）
- 组
- 合
- ：
- 用
- 内
- 置
- 权
- 重
- 对
- 目
- 标
- 蛋
- 白
- +
- 配
- 体
-  
- S
- M
- I
- L
- E
- S
-  
- 直
- 接
- 推
- 理
- 结
- 合
- 残
- 基
- ，
- 为
-  
- b
- i
- n
- d
- e
- r
-  
- 设
- 计
- 提
- 供
- 接
- 触
- 面
- 先
- 验
- ；
- 示
- 例
-  
- C
- S
- V
-  
- 流
- 程
- （
- E
- S
- M
-  
- 嵌
- 入
- →
- 配
- 体
- 图
- 特
- 征
- →
- t
- r
- a
- i
- n
- /
- e
- v
- a
- l
- u
- a
- t
- e
- ）
- 也
- 可
- 整
- 体
- 迁
- 移
- 到
-  
- A
- M
- P
- /
- 毒
- 性
- 肽
- 的
- 结
- 合
- 靶
- 点
- 标
- 注
- 任
- 务
- 。
