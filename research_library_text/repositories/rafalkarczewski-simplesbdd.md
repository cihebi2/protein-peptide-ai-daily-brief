# rafalkarczewski/simplesbdd

- **仓库：** [https://github.com/rafalkarczewski/simplesbdd](https://github.com/rafalkarczewski/simplesbdd)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none（顶层无 LICENSE；仅 moflow/ 子目录带 License.md）
- **语言：** Python
- **复用度：** medium —— 打分模型与质心模型权重已在 checkpoints 内、训练数据 CSV 附带，但主数据集 CrossDocked2020 与 MoFlow 权重需自行下载，评测环境依赖 python2.7（Pocket2Mol 协议），复现有一定工程门槛
- **能力：** training_pipeline、inference、benchmark、data_loader

## 仓库摘要

SimpleSBDD（AISTATS 2025 oral）：基于简单 EGNN 打分模型+配体质心预测器的结构导向药物设计（SBDD）基线，支持三种模式——老药重定位(DR)、经 MoFlow 的新药生成(ND)与性质优化(PO)，并用 Vina 对接与 Pocket2Mol 协议评测。

## 入口脚本

- sampling.py
- moflow_sampling.py
- train_scoring_model.py
- train_com_model.py

## 数据加载

- utils.py
- moflow/data/data_loader.py
- moflow/data/smile_to_graph.py
- moflow/data/data_frame_parser.py

## 模型权重

- checkpoints/com_model_state_dict.pt
- checkpoints/scoring_model_state_dict.pt（均已含预训练权重）；MoFlow ZINC 权重需按官方仓库说明另行下载至 moflow/mflow/results

## 评测基准

- evaluation/evaluate.py（Pocket2Mol 协议，需 python2.7 环境）
- evaluation/docking.py
- evaluation/scoring_func.py
- evaluation_utils.py
- results_table.png

## 文档

- README.md
- SimpleSBDD_no_ws.png（模型图）
- moflow/README.md
- requirements.txt

## 课题关联

- C16 docking（Vina 对接评分贯穿训练与评测，docking.py 可复用）
- C004 binder/PPI（蛋白口袋配体生成=小分子 binder 设计同构问题）
- C007条件生成（PO 模式做性质导向优化）
- C008基准校准（SBDD 标准评测协议实现）

## 与论文/课题的组合方式

- 与
-  
- A
- I
- S
- T
- A
- T
- S
- '
- 2
- 5
-  
- 论
- 文
- 组
- 合
- 复
- 现
- 三
- 种
-  
- S
- B
- D
- D
-  
- 模
- 式
- ；
- 其
-  
- V
- i
- n
- a
-  
- 打
- 分
- 数
- 据
- (
- b
- i
- n
- d
- i
- n
- g
- _
- a
- f
- f
- i
- n
- i
- t
- y
- .
- c
- s
- v
- )
- +
- E
- G
- N
- N
-  
- 打
- 分
- 器
- 可
- 作
- 为
-  
- C
- 0
- 0
- 4
- /
- C
- 1
- 6
-  
- 课
- 题
- 的
- 快
- 速
- 亲
- 和
- 度
- 代
- 理
- 评
- 估
- 器
- ，
- 比
- 逐
- 次
- 跑
- 全
- 流
- 程
-  
- d
- o
- c
- k
- i
- n
- g
-  
- 便
- 宜
- 得
- 多
- 。
