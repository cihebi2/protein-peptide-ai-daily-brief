# 3biocompbio/abagym

- **仓库：** [https://github.com/3biocompbio/abagym](https://github.com/3biocompbio/abagym)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** 自定义非商用（README 声明 non-commercial use only，无标准 LICENSE 文件）
- **语言：** 无代码（纯数据仓库，CSV+PDB）
- **复用度：** high —— 纯数据资产但完整开箱：全部突变 CSV、元数据与复合物 PDB 结构随仓发布，含 MinMax/RankQuartile 归一化分数列，可直接用于训练与评测，无需运行任何管线。
- **能力：** database

## 仓库摘要

AbAgym 是人工整理的抗体-抗原复合物突变数据集（mAbs 2025）：68 个深度突变扫描(DMS)数据集+复合物 3D 结构，约 32.4 万非冗余突变（含 3.65 万界面突变），支持抗体设计与免疫逃逸预测方法的开发评测；FoldX 基准结构在 Zenodo。

## 入口脚本

- （无）

## 数据加载

- AbAgym_data_full.csv.zip
- AbAgym_data_non-redundant.csv.zip
- AbAgym_data_non-redundant_interface.csv
- AbAgym_metadata.csv
- PDB_files.zip

## 模型权重

- 无模型；FoldX 预测结构: Zenodo record 17328791（README 提供，受 FoldX 许可约束）

## 评测基准

- AbAgym_data_full_interface.csv (37361 界面突变基准)
- AbAgym_data_non-redundant_interface.csv (36541 非冗余界面突变基准)

## 文档

- README.md

## 课题关联

- C004binder/PPI
- C003多端点
- C008基准校准
- C011评估协议

## 与论文/课题的组合方式

- 配
- 合
-  
- m
- A
- b
- s
-  
- 2
- 0
- 2
- 5
-  
- 论
- 文
- 做
- 抗
- 体
- -
- 抗
- 原
- 突
- 变
- 效
- 应
- 预
- 测
- 基
- 准
- ；
- 不
- 同
-  
- a
- s
- s
- a
- y
-  
- 分
- 数
- 范
- 围
- 不
- 一
- 、
- 需
- 跨
- 数
- 据
- 集
- 归
- 一
- 化
- 的
- 特
- 点
- 天
- 然
- 适
- 合
-  
- C
- 0
- 0
- 3
-  
- 多
- 端
- 点
- 与
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
- 课
- 题
- ；
- 界
- 面
- 突
- 变
- 子
- 集
- 可
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
-  
- 设
- 计
- 的
- 评
- 估
- 基
- 准
- 。
