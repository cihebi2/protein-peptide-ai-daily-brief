# yongchand/reliable-ba

- **仓库：** [https://github.com/yongchand/reliable-ba](https://github.com/yongchand/reliable-ba)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— train→infer→analyze 全管线完整，附带小样本示例数据集与一键 demo 脚本，训练/验证/测试 CSV 内置；只需自备引擎打分与嵌入即可扩展
- **能力：** training_pipeline、inference、data_loader、visualization、benchmark

## 仓库摘要

RELIABLE-BA：融合四个分子对接引擎（GNINA/BIND/FlowDock/DynamicBind）的可靠性感知 MoNIG（Mixture of Normal-Inverse-Gamma）模型，对蛋白-配体复合物输出结合亲和力预测及校准的认知/偶然不确定度和逐引擎可靠性，main.py 提供 train/infer/analyze 三模式。

## 入口脚本

- main.py
- examples/run_example.sh
- examples/generate_embeddings.py

## 数据加载

- src/drug_dataset_emb.py
- data/train_pdbs.csv
- data/validation_pdbs.csv
- data/test_pdbs.csv

## 模型权重

- 无预置权重；train 模式产出 saved_models/best_MoNIG_emb.pt，README 描述输入需自备 SMILES+真实亲和力+各引擎打分列

## 评测基准

- src/analyze_uncertainty.py
- src/inference_drug_discovery.py
- examples/run_example.sh

## 文档

- README.md
- examples/

## 课题关联

- C016 docking
- C010 校准弃权
- C003 多端点

## 与论文/课题的组合方式

- 直
- 接
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
- 的
- 分
- 子
- 对
- 接
- 域
- 实
- 验
- 载
- 体
- ：
- M
- o
- N
- I
- G
-  
- 的
- 认
- 知
- /
- 偶
- 然
- 不
- 确
- 定
- 性
- 分
- 解
- 与
- 逐
- 引
- 擎
- 可
- 靠
- 性
- 权
- 重
- 可
- 用
- 于
- 多
- 源
- 预
- 测
- 融
- 合
- +
- 选
- 择
- 性
- 预
- 测
- 研
- 究
- ；
- K
- d
- /
- K
- i
-  
- 混
- 合
- 端
- 点
- 输
- 入
- 也
- 与
-  
- C
- 0
- 0
- 3
-  
- 多
- 端
- 点
- 课
- 题
- 契
- 合
