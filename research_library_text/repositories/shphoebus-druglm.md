# shphoebus/druglm

- **仓库：** [https://github.com/shphoebus/druglm](https://github.com/shphoebus/druglm)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 一键下载预计算 embedding 与基准数据，多架构 DTI 基线齐全，命令行统一入口，CSV 划分文件内置
- **能力：** data_loader、training_pipeline、inference、benchmark

## 仓库摘要

DrugLM：把 BGE/E5/GTE 等大语言模型文本 embedding 引入药物-靶点相互作用（DTI）预测的统一框架，系统评测 6 种下游架构（MLP-DTI、DeepConvDTI、GraphDTA、LightGCN/NGCF、BACPI）。

## 入口脚本

- run_lm_model.py
- run_downstream_task.py
- download_data_embeddings.py

## 数据加载

- LM_finetune/finetune_bge|e5|gte/runner.py+trainer.py
- BACPI/code/main.py
- GNN_DTI/main.py
- GraphDTA/training_validation.py

## 模型权重

- 预计算 LM embedding 经 download_data_embeddings.py 下载（.pt）

## 评测基准

- DeepConvDTI/evaluate_performance.py
- GNN_DTI/evaluate_filtered.py
- GraphDTA/evaluate_graphdta_filtered.py

## 文档

- README.md
- requirements.txt

## 课题关联

- C004
- C013

## 与论文/课题的组合方式

- 作
- 为
-  
- C
- 0
- 0
- 4
-  
- b
- i
- n
- d
- e
- r
- /
- P
- P
- I
- （
- D
- T
- I
- ）
- 课
- 题
- 的
- 现
- 成
- 基
- 线
- 矩
- 阵
- ：
- 6
-  
- 种
- 架
- 构
-  
- +
-  
- 3
-  
- 种
-  
- L
- M
-  
- e
- m
- b
- e
- d
- d
- i
- n
- g
-  
- 的
- 交
- 叉
- 对
- 比
- 可
- 直
- 接
- 复
- 现
- ，
- 用
- 于
- 检
- 验
- 新
- 模
- 型
- 相
- 对
- 基
- 线
- 的
- 新
- 颖
- 性
- /
- 增
- 益
- （
- C
- 0
- 1
- 3
- ）
- 。
