# zhangruochi/pepland

- **仓库：** [https://github.com/zhangruochi/pepland](https://github.com/zhangruochi/pepland)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **语言：** Python
- **复用度：** high —— 预训练探针 checkpoint 随仓库内置，推理脚本+配置齐全，评测数据集（结合/CPP/溶解）全部随仓发布；注意本地克隆工作树为空（内容在 git 对象中，需 git checkout 恢复）。
- **能力：** data_loader、training_pipeline、inference、benchmark、visualization

## 仓库摘要

PepLand 是覆盖标准与非标准氨基酸的大规模肽预训练表征模型（多视图异构图 GNN，两阶段预训练+AdaFrag 碎片化），用于肽属性预测：PPI 结合、穿膜性(CPP)、溶解性、可合成性等。

## 入口脚本

- inference.py
- pretrain_masking.py
- trainer.py

## 数据加载

- data/eval/ (c/nc-binding、CPP、Sol 评测数据)
- data/pretrained/
- data/further_training/
- splitters.py

## 模型权重

- cpkt/linear_pred_atoms/data/model.pth、cpkt/linear_pred_bonds/data/model.pth（线性探针 checkpoint 内置，MLflow 格式）

## 评测基准

- data/eval/statistics.py
- configs/test.yaml
- configs/bbbp.json
- configs/esol.json

## 文档

- README.md
- inference/README.md
- environment.yaml

## 课题关联

- C001AMP条件活性
- C002肽毒性
- C004binder/PPI
- C013基线新颖性

## 与论文/课题的组合方式

- 配
- 合
-  
- a
- r
- X
- i
- v
-  
- 2
- 3
- 1
- 1
- .
- 0
- 4
- 4
- 1
- 9
-  
- 复
- 现
- 肽
- 表
- 征
- 预
- 训
- 练
- 与
- 属
- 性
- 预
- 测
- ；
- 非
- 标
- 准
- 氨
- 基
- 酸
- 处
- 理
- 与
- 多
- 端
- 点
- 属
- 性
- 数
- 据
- 可
- 直
- 接
- 作
- 为
-  
- C
- 0
- 0
- 1
- /
- C
- 0
- 0
- 2
-  
- 课
- 题
- 的
- 表
- 征
- 基
- 线
- 与
- 数
- 据
- 源
- ，
- 结
- 合
- 数
- 据
- 集
- 支
- 撑
-  
- C
- 0
- 0
- 4
-  
- 肽
- 结
- 合
- 剂
- 预
- 测
- 。
