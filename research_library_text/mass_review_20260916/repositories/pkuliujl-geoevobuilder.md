# pkuliujl/geoevobuilder

- **仓库：** [https://github.com/pkuliujl/geoevobuilder](https://github.com/pkuliujl/geoevobuilder)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 单命令推理（uv pip install -e . + 下载 Se.pt）即可运行，示例 PDB/MSA 齐备，零 shot 无需训练
- **能力：** inference、data_loader、protocol

## 仓库摘要

GeoEvoBuilder（PNAS 2025）：零样本深度学习方法同时提升蛋白热稳定性与活性，结合基于结构的从头序列设计与 ESM2 蛋白语言模型，支持固定关键残基的部分设计与 MSA 引导设计。

## 入口脚本

- run_GeoEvoBuilder.py

## 数据加载

- MSA_Processing/run_sequenceprofile.py
- geoevobuilder/sampling.py

## 模型权重

- 权重 Se.pt 经北大网盘链接下载（disk.pku.edu.cn，提取码 xx7W），放置于 geoevobuilder/Se.pt

## 评测基准

- examples/（含 3mpc_A、3D80_A DHFR 设计示例与 MSA 文件）

## 文档

- README.md
- MSA_Processing/README.md
- pyproject.toml

## 课题关联

- C001
- C005
- C007

## 与论文/课题的组合方式

- C
- 0
- 0
- 1
-  
- 条
- 件
- 活
- 性
- 课
- 题
- 可
- 直
- 接
- 用
- 其
-  
- -
- -
- F
- i
- x
- e
- d
-  
- 残
- 基
- 固
- 定
- 机
- 制
- 做
- '
- 固
- 定
- 功
- 能
- 位
- 点
- 、
- 重
- 设
- 计
- 其
- 余
- 序
- 列
- '
- 的
- 条
- 件
- 设
- 计
- 实
- 验
- ；
- 其
- 热
- 稳
- 定
- 性
- +
- 活
- 性
- 双
- 目
- 标
- 零
- 样
- 本
- 评
- 估
- 可
- 接
- 入
-  
- C
- 0
- 0
- 5
-  
- 表
- 型
- /
- 功
- 能
- 验
- 证
- 论
- 文
- 对
- 照
- 。
