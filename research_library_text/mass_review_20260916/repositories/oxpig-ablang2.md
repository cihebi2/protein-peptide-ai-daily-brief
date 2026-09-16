# oxpig/ablang2

- **仓库：** [https://github.com/oxpig/ablang2](https://github.com/oxpig/ablang2)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** BSD-3-Clause
- **语言：** Python
- **复用度：** high —— pip install ablang2 即装即用，权重自动下载，官方 notebook 覆盖序列恢复/嵌入/打分用法；定位是开箱可用的推理组件（非训练管线）
- **能力：** inference

## 仓库摘要

AbLang-2：抗体特异性蛋白质语言模型（Oxford oxpig），针对抗体 germline 偏置优化，擅长建议远离 germline 的有效突变；支持 paired/unpaired 抗体序列（及 TCRLang TCR 版本）的残差嵌入、序列恢复与掩码填充。

## 入口脚本

- ablang2/pretrained.py
- ablang2/load_model.py（pip 包 ablang2 入口）

## 数据加载

- （无）

## 模型权重

- 仓库不含权重；ablang2.pretrained(model_to_use='ablang2-paired') 首次调用自动下载官方权重（含 TCRLang-Paired）

## 评测基准

- （无）

## 文档

- README.md
- notebooks/pretrained_module.ipynb
- notebooks/pretrained_module_tcrlang.ipynb

## 课题关联

- C004 binder/PPI
- C013基线新颖性

## 与论文/课题的组合方式

- 与
- 抗
- 体
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
-  
- A
- b
- L
- a
- n
- g
- 2
-  
- 做
-  
- C
- D
- R
-  
- 区
- 域
- 序
- 列
- 恢
- 复
- 与
-  
- g
- e
- r
- m
- l
- i
- n
- e
- -
- a
- w
- a
- y
-  
- 突
- 变
- 建
- 议
- （
- r
- e
- s
- t
- o
- r
- a
- t
- i
- o
- n
- .
- p
- y
- /
- s
- c
- o
- r
- e
- s
- .
- p
- y
- ）
- ，
- 或
- 抽
- 取
- 残
- 差
- 嵌
- 入
- 供
-  
- b
- i
- n
- d
- e
- r
-  
- 预
- 测
- 模
- 型
- 作
- 特
- 征
- ；
- 也
- 是
- 抗
- 体
-  
- L
- M
-  
- 的
- 标
- 准
- 对
- 比
- 基
- 线
- 。
