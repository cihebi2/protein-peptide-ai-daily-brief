# willhua127/genzyme

- **仓库：** [https://github.com/willhua127/genzyme](https://github.com/willhua127/genzyme)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** CC-BY-NC-4.0（禁商用）
- **语言：** Python
- **复用度：** high —— 训练/推理/复现脚本齐全，checkpoint 在 Google Drive 提供，改动 SMILES 即可定制设计任务；但依赖 ESM3 访问权限与较重的依赖栈（UniCore/OpenMM）。
- **能力：** data_loader、training_pipeline、inference、benchmark

## 仓库摘要

GENzyme 是反应条件化的从头酶设计模型（arXiv 2411.16694），基于流匹配与 ESM3，可按任意底物/产物 SMILES 生成催化口袋、酶与酶-底物复合物，支持精修/重定位，内置 UniMol Docking v2 结合模块。

## 入口脚本

- generate.py
- inference.py
- reproduce.py
- train.py

## 数据加载

- data/loader.py
- data/data.py
- data/esm_utils.py

## 模型权重

- genzyme.ckpt: Google Drive（README 提供链接）下载至 genzyme_ckpt/；推理需 ESM3 访问权限；结合模块需 UniCore(UniMol v2) 权重

## 评测基准

- evaluation/metrics.py
- evaluation/loss.py
- reproduce.py
- generated/（含 EnzymeFlow/ZymCTRL 基线产物）

## 文档

- README.md
- genzyme_ckpt/README.md
- configs.py
- gen_configs.py

## 课题关联

- C007条件生成
- C16docking
- C004binder/PPI

## 与论文/课题的组合方式

- 配
- 合
-  
- a
- r
- X
- i
- v
-  
- 2
- 4
- 1
- 1
- .
- 1
- 6
- 6
- 9
- 4
-  
- 复
- 现
- 反
- 应
- 条
- 件
- 化
- 酶
- 设
- 计
- ；
- 与
-  
- E
- n
- z
- y
- m
- e
- F
- l
- o
- w
- /
- Z
- y
- m
- C
- T
- R
- L
-  
- 基
- 线
- 产
- 物
- 同
- 仓
- 便
- 于
-  
- C
- 0
- 1
- 3
-  
- 基
- 线
- 对
- 比
- ；
- U
- n
- i
- M
- o
- l
-  
- v
- 2
-  
- 结
- 合
- 打
- 分
- 模
- 块
- 可
- 复
- 用
- 于
-  
- C
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
- 评
- 估
- 与
-  
- C
- 0
- 0
- 4
-  
- 结
- 合
- 剂
- 筛
- 选
- 课
- 题
- 。
