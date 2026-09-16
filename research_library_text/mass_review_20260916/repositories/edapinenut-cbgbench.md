# edapinenut/cbgbench

- **仓库：** [https://github.com/edapinenut/cbgbench](https://github.com/edapinenut/cbgbench)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **语言：** Python
- **复用度：** high —— 数据（CrossDocked2020 处理版 GDrive）、预训练权重、训练/采样/四类评测脚本与 docking 工具链（vina/plip）齐备，environment.yml 可复现环境
- **能力：** data_loader、training_pipeline、inference、benchmark、protocol

## 仓库摘要

CBGBench（ICLR 2025 spotlight）：靶点感知分子生成统一基准，单一代码框架整合 Pocket2Mol/GraphBP/DiffSBDD/DiffBP/TargetDiff/FLAG/D3FG 七种方法，覆盖 de novo、linker 设计、片段生长、骨架跃迁、侧链装饰五类任务。

## 入口脚本

- train.py
- sample.py
- generate.sh

## 数据加载

- repo/datasets/
- scripts/extract_pockets.py

## 模型权重

- 预训练 checkpoint 经 README 中 Google Drive 链接下载（含各 SOTA 方法）；SOTA 方法生成分子集亦有 GDrive 链接

## 评测基准

- evaluate_scripts/cal_chem_results.py
- evaluate_scripts/cal_geom_results.py
- evaluate_scripts/cal_intera_results.py
- evaluate_scripts/cal_sub_results.py
- evaluate_scripts/evaluate_chem_folder.py
- evaluate_scripts/evaluate_geom_folder.py
- evaluate_scripts/evaluate_interact_folder.py

## 文档

- README.MD
- docs/

## 课题关联

- C008
- C016
- C004

## 与论文/课题的组合方式

- 是
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
- 核
- 心
- 复
- 现
- 平
- 台
- ：
- 可
- 直
- 接
- 跑
- 通
-  
- 7
-  
- 方
- 法
-  
- x
-  
- 5
-  
- 任
- 务
- 的
- 统
- 一
- 评
- 测
- ，
- 报
- 告
- 化
- 学
- 性
- 质
- /
- 几
- 何
- /
- 相
- 互
- 作
- 用
- 三
- 类
- 指
- 标
- ，
- 为
- 新
- 方
- 法
- 提
- 供
- 标
- 准
- 化
- 对
- 照
- 。
