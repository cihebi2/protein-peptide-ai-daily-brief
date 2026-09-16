# dsimb/arid-sf

- **仓库：** [https://github.com/dsimb/arid-sf](https://github.com/dsimb/arid-sf)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python（含 Cython 扩展）
- **复用度：** high —— 开箱可跑的完整打分管线：预训练权重内置、示例数据、conda 安装说明、HADDOCK3 对接格式转换脚本齐全，MIT 许可
- **能力：** inference、benchmark、protocol

## 仓库摘要

ARID-sf：抗原-抗体复合物构象打分工具（scoring function），ARID v2.0 基于 ESM-C 嵌入 + 界面体素/Cython 距离特征，可对大量对接 pose（如 HADDOCK3 输出）并行打分重排。

## 入口脚本

- ARIDv2.0/score_round.py
- ARIDv2.0/score_refs.py
- ARIDv2.0/scorer.py

## 数据加载

- ARIDv2.0/create_interface_features_v1.py
- ARIDv2.0/lookup_dict.py
- ARIDv2.0/get_esm_embeddings.py

## 模型权重

- ARIDv2.0/ARID_20_Std.pt
- ARIDv2.0/ARID_20_Std_preprint.pt（预训练打分模型直接内置仓库）

## 评测基准

- example/models/1a14/（抗体-抗原 PDB pose 示例集）
- example/outputs/

## 文档

- README.md

## 课题关联

- C016 docking
- C004 binder/PPI

## 与论文/课题的组合方式

- 与
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
-  
- 及
-  
- d
- o
- c
- k
- i
- n
- g
-  
- 课
- 题
- 组
- 合
- ：
- 用
-  
- H
- A
- D
- D
- O
- C
- K
- 3
-  
- t
- o
- p
- o
- a
- a
-  
- 生
- 成
-  
- O
- P
- L
- S
-  
- U
- A
-  
- 格
- 式
- 复
- 合
- 物
- 后
- ，
- 用
-  
- A
- R
- I
- D
-  
- 对
- 数
- 千
-  
- p
- o
- s
- e
-  
- 打
- 分
- 重
- 排
- （
- s
- c
- o
- r
- e
- _
- r
- o
- u
- n
- d
- .
- p
- y
- ）
- ，
- 可
- 作
-  
- C
- 0
- 1
- 6
-  
- d
- o
- c
- k
- i
- n
- g
-  
- 课
- 题
- 的
- 独
- 立
- 重
- 打
- 分
- 基
- 线
- 或
- 评
- 估
- 器
- 。
