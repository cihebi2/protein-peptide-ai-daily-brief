# idruglab/adcnet

- **仓库：** [https://github.com/idruglab/adcnet](https://github.com/idruglab/adcnet)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 训练权重（.h5）与 ESM-2 嵌入 pkl、data.xlsx 数据全部内嵌仓库，class.py/inference.py 可直接复现；缺点是无 LICENSE、TensorFlow 2.3 旧环境、代码组织扁平
- **能力：** training_pipeline、inference、data_loader

## 仓库摘要

ADCNet：面向抗体偶联药物（ADC）性质预测的半监督学习模型，用 ESM-2 提取抗体重链/轻链/抗原嵌入，结合 DAR 值等特征预测 ADC 活性（论文配套，含 Web 服务器）。

## 入口脚本

- class.py
- inference.py
- ESM-2.py

## 数据加载

- dataset.py

## 模型权重

- classification_weights/ADC_9.h5（推理权重，17MB，仓库内）
- medium3_weights/bert_weightsMedium_20.h5（训练中间权重，13MB，仓库内）

## 评测基准

- （无）

## 文档

- README.md
- py37.yaml（环境清单）

## 课题关联

- C003 多端点
- C004 binder/PPI

## 与论文/课题的组合方式

- 其
-  
- f
- i
- l
- e
- s
- /
-  
- 内
- 的
- 抗
- 体
- -
- 抗
- 原
-  
- E
- S
- M
- -
- 2
-  
- 嵌
- 入
- 与
-  
- A
- D
- C
-  
- 标
- 注
- 数
- 据
- （
- D
- A
- R
- 、
- 活
- 性
- ）
- 可
- 直
- 接
- 作
- 为
- 多
- 端
- 点
- 抗
- 体
- 性
- 质
- 预
- 测
- （
- C
- 0
- 0
- 3
- ）
- 或
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
- （
- C
- 0
- 0
- 4
- ）
- 课
- 题
- 的
- 小
- 规
- 模
- 基
- 准
- 数
- 据
- 复
- 用
- ；
- E
- S
- M
- -
- 2
-  
- 嵌
- 取
- 流
- 程
- 可
- 移
- 植
- 到
-  
- A
- M
- P
-  
- 活
- 性
- 预
- 测
- （
- C
- 0
- 0
- 1
- ）
- 。
