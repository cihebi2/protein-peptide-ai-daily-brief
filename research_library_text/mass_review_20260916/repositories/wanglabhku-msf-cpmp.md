# wanglabhku/msf-cpmp

- **仓库：** [https://github.com/wanglabhku/msf-cpmp](https://github.com/wanglabhku/msf-cpmp)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** medium —— 附带完整环肽渗透性数据集（CycPeptMPDB_Peptide_PAMPA.csv）与全套 ML 基线及数据划分脚本，但 README 所述深度学习主模型（model_comcat.py/data_pretrofit.py）缺失，核心 MSF 融合模型无法复现
- **能力：** training_pipeline、data_loader、benchmark

## 仓库摘要

MSF-CPMP：港大 Wang Lab 的多源特征融合模型，预测环肽膜渗透性（CycPeptMPDB PAMPA，6491 条环肽数据）。提供 8 种传统机器学习基线（XGBoost/LGBM/CatBoost/RF/SVM/KNN/DT/GaussianNB）与十折交叉验证数据处理脚本；README 提到的深度学习部分代码未出现在仓库中。

## 入口脚本

- src/machine_learning/XGBoost.py
- src/machine_learning/LGBM.py
- src/machine_learning/CatBoost.py
- src/machine_learning/rf.py
- src/machine_learning/knn.py
- src/machine_learning/DT.py
- src/machine_learning/GaussianNB.py
- src/machine_learning/svm(rbf).py

## 数据加载

- datasets_process/data_deeplearning_process.py
- datasets_process/data_machinelearning_process.py

## 模型权重

- 无权重文件（传统 ML 基线随训随用）

## 评测基准

- 十折交叉验证内嵌于各 ML 脚本
- datasets/data_deep_learning/sd.txt
- datasets/data_machine_learning/sds.txt

## 文档

- README.md
- environment.yml

## 课题关联

- C001 AMP条件活性（环肽膜渗透性是与 AMP 膜作用活性直接相关的物性端点）
- C005表型（PAMPA 渗透表型预测）
- C011评估协议（十折交叉验证划分与基线评测流程可复用）

## 与论文/课题的组合方式

- 与
- 环
- 肽
- /
- A
- M
- P
-  
- 课
- 题
- （
- C
- 0
- 0
- 1
- /
- C
- 0
- 0
- 5
- ）
- 组
- 合
- ：
- 6
- 4
- 9
- 1
-  
- 条
-  
- P
- A
- M
- P
- A
-  
- 环
- 肽
- 数
- 据
- 可
- 直
- 接
- 作
- 为
- 渗
- 透
- 性
- 端
- 点
- 并
- 入
- 多
- 端
- 点
- 肽
- 设
- 计
- 数
- 据
- 池
- ；
- 8
-  
- 个
-  
- s
- k
- l
- e
- a
- r
- n
-  
- 系
- 基
- 线
- 可
- 快
- 速
- 建
- 立
- 渗
- 透
- 性
- 预
- 测
- 的
- 基
- 线
- 新
- 颖
- 性
- 对
- 照
- （
- C
- 0
- 1
- 3
- ）
- 。
