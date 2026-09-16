# juewangthu/clape-smb

- **仓库：** [https://github.com/juewangthu/clape-smb](https://github.com/juewangthu/clape-smb)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 仓库直接内置训练数据（txt 序列+标签）与全部 ckpt 权重（多种子+k 折），inference.py 可对任意蛋白序列 txt 直接预测，开箱可跑
- **能力：** training_pipeline、inference、data_loader、benchmark

## 仓库摘要

CLAPE-SMB：基于 ESM-2 预训练编码器+对比学习的蛋白质-小分子结合位点预测框架（CLAPE 系列成员），内置 SJC（sc-PDB+JOINED+COACH420 整合）与自建 UniProtSMB 数据集及多随机种子、k 折交叉验证训练权重。

## 入口脚本

- triplet.py
- inference.py
- pre.py

## 数据加载

- data.py
- count.py

## 模型权重

- Models/SJC/random_seed/*.ckpt
- Models/UniProtSMB/random_seed/*.ckpt
- Models/UniProtSMB/k_folds/fold1-9.ckpt

## 评测基准

- Raw_data/Standard datasets/（chen11/coach420/joined/scpdb）
- Raw_data/SJC/
- Raw_data/UniProtSMB/

## 文档

- README.md
- example.txt

## 课题关联

- C016 docking
- C008 基准校准
- C011 评估协议

## 与论文/课题的组合方式

- 与
-  
- C
- L
- A
- P
- E
-  
- 系
- 列
- 论
- 文
- 组
- 合
- 复
- 现
- 小
- 分
- 子
- 结
- 合
- 位
- 点
- 预
- 测
- 基
- 准
- （
- C
- H
- E
- N
- 1
- 1
- /
- C
- O
- A
- C
- H
- 4
- 2
- 0
- /
- J
- O
- I
- N
- E
- D
- /
- s
- c
- -
- P
- D
- B
- ）
- ；
- 其
-  
- k
-  
- 折
- +
- 多
- 种
- 子
- 权
- 重
- 与
- 类
- 别
- 不
- 平
- 衡
-  
- f
- o
- c
- a
- l
-  
- l
- o
- s
- s
-  
- 可
- 直
- 接
- 用
- 于
-  
- C
- 0
- 0
- 8
-  
- 基
- 准
- 校
- 准
- 与
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
- 研
- 究
- 中
- 的
- 种
- 子
- 方
- 差
- 分
- 析
