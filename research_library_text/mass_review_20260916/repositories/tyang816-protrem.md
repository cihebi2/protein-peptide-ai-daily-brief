# tyang816/protrem

- **仓库：** [https://github.com/tyang816/protrem](https://github.com/tyang816/protrem)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** CC BY-NC-ND 4.0
- **语言：** Python
- **复用度：** medium —— 推理管线、数据准备 shell 脚本与环境文件完整且同源序列数据有 HF 全量链接，但模型权重获取路径未在 README 中明示、需依赖 plmc/EVcouplings 外部工具链
- **能力：** data_loader、inference、benchmark、protocol

## 仓库摘要

VenusREM（ISMB/ECCB 2025，ProteinGym substitution 榜第一）：检索增强的突变效应预测模型，显式引入 MSA 同源序列与结构信息，支持零 shot 突变适合度计算并已集成入 VenusFactory2。

## 入口脚本

- compute_fitness.py

## 数据加载

- src/data/
- data/proteingym_v1/
- script/get_sav.py
- src/data/get_sav.py

## 模型权重

- 模型权重未在 README 明示直链；同源序列数据经 HuggingFace AI4Protein/VenusREM 数据集下载（a2m/a3m tar.gz）

## 评测基准

- script/compute_fitness.sh
- script/get_substitutions.sh
- script/data_format_convert.sh
- script/get_structure_aln_foldseek.sh

## 文档

- README.md
- environment.yml
- src/single_config_monomer.txt

## 课题关联

- C005
- C011
- C001

## 与论文/课题的组合方式

- C
- 0
- 0
- 5
-  
- 表
- 型
- /
- 突
- 变
- 效
- 应
- 课
- 题
- 可
- 用
- 其
-  
- c
- o
- m
- p
- u
- t
- e
- _
- f
- i
- t
- n
- e
- s
- s
- .
- p
- y
-  
- 对
- 自
- 建
-  
- D
- M
- S
- /
- A
- M
- P
-  
- 突
- 变
- 库
- 做
- 零
-  
- s
- h
- o
- t
-  
- 适
- 合
- 度
- 打
- 分
- ；
- P
- r
- o
- t
- e
- i
- n
- G
- y
- m
-  
- 评
- 测
- 协
- 议
- （
- s
- c
- r
- i
- p
- t
- /
-  
- 下
- 全
- 套
- ）
- 可
- 直
- 接
- 作
- 为
-  
- C
- 0
- 1
- 1
-  
- 评
- 估
- 协
- 议
- 课
- 题
- 的
- 参
- 照
- 实
- 现
- 。
