# yinjunbo/cfpgen

- **仓库：** [https://github.com/yinjunbo/cfpgen](https://github.com/yinjunbo/cfpgen)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **语言：** Python
- **复用度：** medium —— 工程化极完整（生成/训练/评测/多精度 DDP 配置俱全、官方权重与数据均有明确下载链接），但权重与数据集均在 Google Drive 需自行下载、vendor/esm 子模块未初始化；就仓库本体而言属代码全而资产外置
- **能力：** training_pipeline、inference、benchmark、data_loader

## 仓库摘要

CFP-Gen（ICML 2025）：基于扩散语言模型（DPLM 底座）的组合式功能蛋白生成，可同时以 GO/IPR/EC 功能注释、序列 motif 与骨架结构为条件做从头蛋白设计、功能性逆折叠与多功能蛋白设计。Lightning+Hydra 工程化完整。

## 入口脚本

- cfpgen_generate.py
- dplm_generate.py
- train.py
- test.py

## 数据加载

- src/byprot/datamodules/
- scripts/create_dataset.ipynb
- scripts/download_cath.sh

## 模型权重

- 四个预训练 checkpoint 经 Google Drive 提供：cfpgen-650m（GO/IPR/motif）、cfpgen-650m-enzyme（EC）、cfpgen-if-zs（骨架逆折叠零样本）、dplm-650m（再训练底座）；数据集 cfpgen_general_dataset（103,939 蛋白/375 GO/1154 IPR）与 uniprot_bb_coords 亦为 Google Drive 链接

## 评测基准

- eval/eval_go.py
- eval/eval_ec.py
- eval/eval_ipr.py
- eval/eval_mmd.py
- eval/metrics/（conditional/similarity/spectrum）
- analysis/cal_tmscore.py
- analysis/cal_plddt_tmscore.py
- analysis/eval_motif_scaffold.py

## 文档

- README.md（含模型表与数据/权重下载）
- configs/（Hydra 全套）
- install.sh
- requirements.txt

## 课题关联

- C007条件生成（多模态可组合条件生成的标杆实现：注释+motif+骨架）
- C004 binder/PPI（功能性逆折叠 cfpgen-if-zs，条件于骨架生成序列）
- C005表型（GO/EC 功能端点作为条件与评测对象）

## 与论文/课题的组合方式

- 与
-  
- I
- C
- M
- L
-  
- 2
- 0
- 2
- 5
-  
- 论
- 文
- 组
- 合
- ：
- 下
- 载
-  
- c
- f
- p
- g
- e
- n
- -
- 6
- 5
- 0
- m
-  
- 即
- 可
- 复
- 现
-  
- G
- O
- /
- I
- P
- R
-  
- 条
- 件
- 生
- 成
- 与
- 多
- 功
- 能
- 蛋
- 白
- 设
- 计
- ；
- C
- 0
- 0
- 7
-  
- 课
- 题
- 可
- 直
- 接
- 以
- 其
-  
- A
- G
- F
- M
- /
- R
- C
- F
- E
-  
- 条
- 件
- 机
- 制
- 为
- 对
- 照
- 或
- 底
- 座
- ，
- 把
-  
- A
- M
- P
-  
- 活
- 性
- /
- 毒
- 性
- 等
- 新
- 端
- 点
- 做
- 成
- 可
- 组
- 合
- 条
- 件
- 微
- 调
- （
- 配
- 合
-  
- d
- p
- l
- m
- -
- 6
- 5
- 0
- m
-  
- 再
- 训
- 练
- 路
- 径
- ）
- 。
