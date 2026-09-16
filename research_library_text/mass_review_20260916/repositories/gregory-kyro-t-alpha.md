# gregory-kyro/t-alpha

- **仓库：** [https://github.com/gregory-kyro/t-alpha](https://github.com/gregory-kyro/t-alpha)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 训练/推理/MC-Dropout 微调脚本齐全，预训练权重与测试集有 Zenodo 官方下载，还有 Colab notebook 可直接运行推理
- **能力：** training_pipeline、inference、data_loader

## 仓库摘要

T-ALPHA：蛋白质-配体结合亲和力预测深度学习模型（多模态特征+分层 Transformer，含 EGNN/DMaSIF 等组件），支持预测结构而非晶体结构输入，并提供基于 Monte Carlo Dropout 的不确定性估计与免实验数据的自学习蛋白质特异性对齐微调方法（JCIM 2025）。

## 入口脚本

- scripts/train.py
- src/training/train_model.py
- src/inference/perform_inference.py
- src/inference/mc_dropout.py

## 数据加载

- src/data/full_model_dataset.py

## 模型权重

- 无内置权重；预训练模型参数与测试数据托管于 Zenodo（records/14510963，README 给出下载链接）

## 评测基准

- src/inference/perform_inference.py
- src/inference/mc_dropout.py
- T-ALPHA.ipynb

## 文档

- README.md
- T-ALPHA.ipynb

## 课题关联

- C016 docking
- C010 校准弃权

## 与论文/课题的组合方式

- 按
-  
- J
- C
- I
- M
-  
- 论
- 文
- 复
- 现
- 蛋
- 白
- -
- 配
- 体
- 亲
- 和
- 力
- 打
- 分
- 及
-  
- S
- A
- R
- S
- -
- C
- o
- V
- -
- 2
-  
- M
- p
- r
- o
- /
- E
- G
- F
- R
-  
- 化
- 合
- 物
- 排
- 序
- ；
- 其
-  
- M
- C
- -
- D
- r
- o
- p
- o
- u
- t
-  
- 不
- 确
- 定
- 性
- 输
- 出
- 可
- 作
- 为
-  
- C
- 0
- 1
- 0
-  
- 校
- 准
- /
- 弃
- 权
- 课
- 题
- 在
- 小
- 分
- 子
- 打
- 分
- 域
- 的
- 不
- 确
- 定
- 性
- 基
- 线
- 方
- 法
