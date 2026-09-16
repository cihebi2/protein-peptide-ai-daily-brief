# 3dfin/3dfin

- **仓库：** [https://github.com/3dfin/3dfin](https://github.com/3dfin/3dfin)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **语言：** Python
- **复用度：** medium —— 工程成熟、pip 可装且有 GUI/CLI/多平台分发，但属林业遥感领域软件，仓库不含数据/权重，与分子/蛋白课题族无关
- **能力：** inference、visualization

## 仓库摘要

3DFin：地面激光点云自动 3D 森林清查软件（自动计算树木参数），提供 CloudCompare/QGIS 插件、Windows 独立程序与 Python 包，含 GUI 与 CLI 批处理。发表于 Forestry 2024。

## 入口脚本

- src/three_d_fin/（pip 包 three_d_fin，GUI/CLI 入口）

## 数据加载

- 点云数据由用户自备（软件本身不含数据）

## 模型权重

- 无模型权重（几何算法软件，非机器学习权重）

## 评测基准

- tests/

## 文档

- README.md
- src/three_d_fin/documentation/documentation.pdf（用户手册）
- CHANGELOG.md
- CONTRIBUTING.md

## 课题关联

- （无）

## 与论文/课题的组合方式

- 与
- 本
- 课
- 题
- 族
- （
- A
- M
- P
- /
- 毒
- 性
- /
- b
- i
- n
- d
- e
- r
- /
- 条
- 件
- 生
- 成
- /
- 评
- 估
- 协
- 议
- 等
- ）
- 无
- 直
- 接
- 关
- 联
- ，
- 不
- 建
- 议
- 纳
- 入
- 课
- 题
- 组
- 合
- ；
- 仅
- 当
- 涉
- 及
- 点
- 云
- 几
- 何
- 处
- 理
- 时
- 参
- 考
- 。
