# cataai/posex

- **仓库：** [https://github.com/cataai/posex](https://github.com/cataai/posex)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 完整七步评测管线 + HF 数据集一键下载说明 + 约20个 docking 工具的独立环境文件，开箱可跑出与 leaderboard 可比的结果
- **能力：** benchmark、protocol、data_loader

## 仓库摘要

PoseX 是蛋白-配体 Self-Docking / Cross-Docking 基准数据集与七步完整评测管线（生成CSV→格式转换→运行docking→提取输出→能量最小化→结构对齐→PoseBusters 计分），覆盖约 20 种 docking 工具（Boltz/Chai/AF3/DiffDock/NeuralPlexer 等），配套 HuggingFace 数据集与在线 leaderboard（dock-lab.tech）。

## 入口脚本

- scripts/run_boltz/run_boltz.sh
- scripts/run_chai/run_chai.py
- scripts/run_alphafold3/run_alphafold3.sh
- scripts/run_diffdock/run_diffdock.sh
- scripts/calculate_benchmark_result.sh
- dataset/main.py

## 数据加载

- dataset/main.py
- dataset/create_custom_set.py
- scripts/convert_to_model_input.py

## 模型权重

- 无内置权重；按 environments/ 下各工具环境文件（boltz-1.txt、chai-1.txt、rfaa.yaml 等）安装外部 docking 模型，权重走各工具官方下载

## 评测基准

- scripts/generate_docking_benchmark.py
- scripts/calculate_benchmark_result.py（PoseBusters 指标）
- scripts/complex_structure_alignment.py

## 文档

- README.md
- dataset/README.md

## 课题关联

- C16
- C004
- C008
- C011

## 与论文/课题的组合方式

- 直
- 接
- 作
- 为
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
- 与
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
- 评
- 测
- 的
- 标
- 准
- 协
- 议
- ：
- 把
- 生
- 成
- 模
- 型
- 产
- 出
- 的
- 配
- 体
- /
- 复
- 合
- 物
- 喂
- 入
-  
- r
- u
- n
- _
- *
-  
- 脚
- 本
- 与
-  
- P
- o
- s
- e
- B
- u
- s
- t
- e
- r
- s
-  
- 评
- 测
- 脚
- 本
- ，
- 获
- 得
- 跨
- 工
- 具
- 可
- 比
- 指
- 标
- ；
- 亦
- 可
- 用
- 于
-  
- C
- 0
- 0
- 8
- /
- C
- 0
- 1
- 1
-  
- 基
- 准
- 校
- 准
- 与
- 评
- 估
- 协
- 议
- 研
- 究
- 的
- 实
- 体
-  
- b
- e
- n
- c
- h
- m
- a
- r
- k
- 。
