# wwzll123/esm-nbr

- **仓库：** [https://github.com/wwzll123/esm-nbr](https://github.com/wwzll123/esm-nbr)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** medium —— 已训练模型与基准数据齐全、推理开箱可用，但代码打包在 zip 内且无训练管线
- **能力：** inference、data_loader

## 仓库摘要

ESM-NBR：基于 ESM-2 蛋白语言模型特征 + 多任务学习，快速预测蛋白序列上 DNA/RNA 结合残基（含可调 dna/rna 阈值），附数据集与补充材料。

## 入口脚本

- ESM-NBR-standalone.zip 内 prediction.py（CLI：python prediction.py fasta device save_dir model_type ...）

## 数据加载

- dataset/（YK17、DRNA1068 训练/测试 fasta 与标签 txt）

## 模型权重

- ESM-NBR-standalone.zip 内 YK17.model、DRNA1068.model（各约 6.5MB，已训练模型）

## 评测基准

- dataset/ 内置测试集（DNA-129/RNA-117 Test）
- suppl-ESM-NBR(12.1).pdf

## 文档

- README.md

## 课题关联

- （无）

## 与论文/课题的组合方式

- 其
- 『
- E
- S
- M
- -
- 2
-  
- 特
- 征
-  
- +
-  
- 多
- 任
- 务
- 双
- 阈
- 值
- 』
- 的
- 残
- 基
- 级
- 结
- 合
- 预
- 测
- 协
- 议
- 可
- 迁
- 移
- 到
-  
- A
- M
- P
- /
- b
- i
- n
- d
- e
- r
-  
- 结
- 合
- 位
- 点
- 标
- 注
- 类
- 课
- 题
- ，
- 作
- 为
- 特
- 征
- 提
- 取
- 与
- 阈
- 值
- 化
- 决
- 策
- 的
- 参
- 考
- 实
- 现
- 。
