# aalto-quml/pipe

- **仓库：** [https://github.com/aalto-quml/pipe](https://github.com/aalto-quml/pipe)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none（顶层无 LICENSE；上游 RePHINE/SPE 各自的许可需分别查看）
- **语言：** Python
- **复用度：** medium —— ZINC/Alchemy 训练评测管线与 YAML 配置齐全，但环境依赖 RePHINE 与 SPE 两个上游仓库、无 LICENSE、无预训练权重
- **能力：** training_pipeline、data_loader、benchmark

## 仓库摘要

PIPE：将结构位置编码（SPE）与持续同调表示（RePHINE）结合的图神经网络方法（ICML 2025），在 ZINC/Alchemy 分子图回归基准上训练评测，仓库为 RePHINE 与 SPE 两个上游项目的整合。

## 入口脚本

- SPE/run.sh
- SPE/zinc/runner.py
- SPE/alchemy/runner.py
- RePHINE/runners/run_main.py

## 数据加载

- SPE/src/data_utils/
- SPE/src/preprocessing.py
- SPE/data/
- RePHINE/datasets/

## 模型权重

- 无预训练权重（runner 训练即用，ZINC/Alchemy 由脚本获取）

## 评测基准

- SPE/configs/（ZINC、Alchemy 图回归配置与多种 PE 方法对比）
- SPE/drugood/（OGB DrugOOD 域泛化配置）

## 文档

- README.md
- pipe_2d.png

## 课题关联

- C003多端点

## 与论文/课题的组合方式

- 与
- 分
- 子
- 性
- 质
- 预
- 测
- 课
- 题
- 组
- 合
- ：
- 其
-  
- c
- o
- n
- f
- i
- g
- s
-  
- 提
- 供
- 多
- 种
- 位
- 置
- 编
- 码
- +
- 拓
- 扑
- 特
- 征
- 的
- 统
- 一
- 对
- 比
- 框
- 架
- ，
- 可
- 将
-  
- P
- I
- P
- E
- /
- R
- e
- P
- H
- I
- N
- E
-  
- 特
- 征
- 接
- 入
- 多
- 端
- 点
- 分
- 子
- 预
- 测
- （
- C
- 0
- 0
- 3
- ）
- 或
-  
- A
- M
- P
-  
- 图
- 模
- 型
- 作
- 为
- 结
- 构
- 编
- 码
- 增
- 强
- 消
- 融
- 实
- 验
- 。
