# jiayili11/multi-amp

- **仓库：** [https://github.com/jiayili11/multi-amp](https://github.com/jiayili11/multi-amp)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 训练/预测/设计三入口齐全，权重与数据托管于 HF 且目录结构说明明确；缺点是无 LICENSE、代码为扁平单层脚本
- **能力：** data_loader、training_pipeline、inference

## 仓库摘要

MultiAMP 三流架构预测抗菌肽：ESM-2(650M) 序列流 + BiLSTM 浅层流 + GVP-GNN 结构流经交叉注意力融合，联合分类/对比学习/二级结构重建损失；宣称在 <40% 序列同一性的远缘 AMP 上 MCC 超 SOTA 10%+，并用于海洋来源新 AMP 发现与梯度 motif 设计。

## 入口脚本

- train.py
- predict.py
- design.py

## 数据加载

- dataset.py
- data/README.md（train_amp 11970 / test_amp 5355 / ESMFold 结构目录格式说明）

## 模型权重

- HuggingFace https://huggingface.co/jiayi11/multi_amp（best_model_overall.pth 等检查点与训练/测试数据）

## 评测基准

- predict.py（验证集评估模式，按验证 AUC 保存最优）
- examples/test_sequences.fasta

## 文档

- README.md
- data/README.md

## 课题关联

- C001
- C013

## 与论文/课题的组合方式

- C
- 0
- 0
- 1
-  
- A
- M
- P
-  
- 条
- 件
- 活
- 性
- 课
- 题
- 的
- 直
- 接
-  
- S
- O
- T
- A
-  
- 无
- 条
- 件
- 基
- 线
- ：
- 先
- 复
- 现
- 其
- 分
- 类
- 性
- 能
- 上
- 限
- ，
- 再
- 引
- 入
- 条
- 件
- （
- 物
- 种
- /
- 环
- 境
- /
- 浓
- 度
- ）
- 标
- 签
- 做
- 条
- 件
- 化
- 改
- 造
- ；
- d
- e
- s
- i
- g
- n
- .
- p
- y
-  
- 的
- 梯
- 度
-  
- m
- o
- t
- i
- f
-  
- 策
- 略
- 可
- 嫁
- 接
- 到
-  
- C
- 0
- 0
- 7
-  
- 条
- 件
- 生
- 成
- 的
-  
- m
- o
- t
- i
- f
-  
- 约
- 束
- 设
- 计
- ；
- 远
- 缘
- (
- <
- 4
- 0
- %
- 同
- 一
- 性
- )
- 测
- 试
- 设
- 置
- 支
- 撑
-  
- C
- 0
- 1
- 3
-  
- 新
- 颖
- 性
- 评
- 估
- 。
