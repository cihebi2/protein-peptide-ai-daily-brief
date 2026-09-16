# xiaolin-yang-s/gasi-dta

- **仓库：** [https://github.com/xiaolin-yang-s/gasi-dta](https://github.com/xiaolin-yang-s/gasi-dta)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 训练+测试管线完整、Davis/KIBA 基准数据随仓库内置、README 给出全部运行命令；无 LICENSE 与预训练权重，但按命令可完整复现
- **能力：** training_pipeline、data_loader、benchmark

## 仓库摘要

GASI-DTA：利用相互作用信息的多分支神经网络，用于药物-靶点结合亲和力（DTA）预测，在 Davis/KIBA 基准及 S1/S2/S3 冷启动设置下评测。

## 入口脚本

- source/train_test.py
- source/train_test_S1.py
- source/train_test_S2.py
- source/train_test_S3.py

## 数据加载

- source/data_preprocess.py
- source/GraphInput.py（药物分子图+靶点图构建）
- source/data/davis/
- source/data/kiba/

## 模型权重

- 无预训练权重，模型从零训练（train_test.py 一条命令完成）

## 评测基准

- Davis/KIBA 基准交叉验证与训练测试
- source/data/S1_split.py、S2_split.py（冷启动药物/靶点划分协议）

## 文档

- README.md
- source/data/README.md

## 课题关联

- C003多端点
- C011评估协议

## 与论文/课题的组合方式

- 与
- 评
- 估
- 协
- 议
- 课
- 题
- （
- C
- 0
- 1
- 1
- ）
- 组
- 合
- ：
- S
- 1
- /
- S
- 2
- /
- S
- 3
-  
- 冷
- 启
- 动
- 划
- 分
- 脚
- 本
- 可
- 直
- 接
- 移
- 植
- 到
- 其
- 他
- 配
- 体
- -
- 蛋
- 白
- 预
- 测
- 课
- 题
- ，
- 检
- 验
- 模
- 型
- 在
- 未
- 见
- 药
- 物
- /
- 靶
- 点
- 上
- 的
- 泛
- 化
- ；
- D
- a
- v
- i
- s
- /
- K
- I
- B
- A
-  
- 内
- 置
- 数
- 据
- 可
- 作
- 亲
- 和
- 力
- 多
- 指
- 标
- （
- M
- S
- E
- /
- C
- I
-  
- 等
-  
- m
- e
- t
- r
- i
- c
- s
- .
- p
- y
- ）
- 基
- 准
- 。
