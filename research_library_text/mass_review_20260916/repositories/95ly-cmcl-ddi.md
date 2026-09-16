# 95ly/cmcl-ddi

- **仓库：** [https://github.com/95ly/cmcl-ddi](https://github.com/95ly/cmcl-ddi)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** low —— 代码不完整：main.py 引用的 parms_setting.py、instantiation.py（模型定义）缺失，无 README/requirements；仅数据预处理与训练循环可用
- **能力：** training_pipeline、data_loader、benchmark

## 仓库摘要

CMCL-DDI：基于对比学习（ Likely 跨模态/图对比）的药物-药物相互作用（DDI）预测 PyTorch 代码，在 DrugBank 与 Twosides 数据上以 AUC/AP/F1 等指标训练评估。

## 入口脚本

- main.py（引用 parms_setting 与 instantiation 模块）

## 数据加载

- data_preprocess.py（load_data，networkx+torch_geometric 图构建）

## 模型权重

- 无；且模型定义文件 instantiation.py/parms_setting.py 未随仓库提供

## 评测基准

- train.py 内含 roc_auc/average_precision/f1 等评估逻辑（DrugBank/Twosides 基准）

## 文档

- （无）

## 课题关联

- C003多端点

## 与论文/课题的组合方式

- 与
- 多
- 端
- 点
- 课
- 题
- 关
- 联
- 弱
- ：
- d
- a
- t
- a
- /
-  
- 内
- 置
-  
- D
- r
- u
- g
- B
- a
- n
- k
- 与
- T
- w
- o
- s
- i
- d
- e
- s
-  
- D
- D
- I
-  
- 数
- 据
- （
- .
- r
- a
- r
-  
- 压
- 缩
- 包
- ）
- 可
- 解
- 压
- 后
- 供
-  
- D
- D
- I
-  
- 多
- 标
- 签
- 预
- 测
- 课
- 题
- 复
- 用
- ，
- 但
- 管
- 线
- 本
- 身
- 需
- 补
- 齐
- 缺
- 失
- 模
- 块
- 才
- 能
- 跑
- 通
- 。
