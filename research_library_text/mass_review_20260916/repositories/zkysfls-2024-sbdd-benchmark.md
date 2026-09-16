# zkysfls/2024-sbdd-benchmark

- **仓库：** [https://github.com/zkysfls/2024-sbdd-benchmark](https://github.com/zkysfls/2024-sbdd-benchmark)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** medium —— 统一评测与结果比较代码完整（MIT），但 16 个方法的实现分布在两套 conda 环境与外部依赖中，预处理数据/模型未在克隆工作区内，复现工作量大
- **能力：** benchmark、protocol、visualization

## 仓库摘要

《Structure-based Drug Design Benchmark: Do 3D Methods Really Dominate?》配套基准：16 种 SBDD/分子优化算法（GA/VAE/RL/HC/梯度/自回归/虚拟筛选）在 7 个任务上的统一评测与比较。

## 入口脚本

- evaluation.py
- results_compare.py

## 数据加载

- mol_opt_process.ipynb（数据处理）

## 模型权重

- README 称预处理数据与预训练模型随仓库提供（推测在 GitHub release/大文件，克隆内未含）

## 评测基准

- evaluation.py
- results_compare.py
- draw.ipynb

## 文档

- README.md
- environment_TestEnv.yml
- environment_TDCEnv.yml

## 课题关联

- C008 基准校准
- C011 评估协议
- C013 基线新颖性
- C016 docking

## 与论文/课题的组合方式

- 作
- 为
-  
- C
- 0
- 0
- 8
- /
- C
- 0
- 1
- 3
-  
- 的
- 基
- 线
- 池
- ：
- 1
- 6
-  
- 个
-  
- 2
- D
- /
- 3
- D
-  
- 方
- 法
- 的
- 配
- 置
- 与
- 评
- 测
- 口
- 径
- 可
- 直
- 接
- 借
- 用
- 来
- 检
- 验
- 新
- 方
- 法
- 相
- 对
- 基
- 线
- 的
- 新
- 颖
- 性
- ；
- 其
-  
- e
- v
- a
- l
- u
- a
- t
- i
- o
- n
- .
- p
- y
-  
- 的
- 统
- 一
- 指
- 标
- 栈
- 可
- 并
- 入
- 自
- 建
- 评
- 估
- 协
- 议
- （
- C
- 0
- 1
- 1
- ）
- 。
