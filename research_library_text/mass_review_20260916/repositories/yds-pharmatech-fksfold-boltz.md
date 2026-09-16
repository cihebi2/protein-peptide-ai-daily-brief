# yds-pharmatech/fksfold-boltz

- **仓库：** [https://github.com/yds-pharmatech/fksfold-boltz](https://github.com/yds-pharmatech/fksfold-boltz)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT（README 声明；仓库内无独立 LICENSE 文件）
- **语言：** Python
- **复用度：** high —— 可 pip 安装（pip install -e .[cuda]）、Pythonic 与 CLI 双入口、输入样例与评测脚本齐全、Boltz 权重自动下载，推理开箱可跑；训练数据需按 scripts/process 自备
- **能力：** inference、training_pipeline、benchmark

## 仓库摘要

FKSFold-Boltz（YDS-Pharmatech，bioRxiv 2025.05.03.651455）在 Boltz（AlphaFold3 类扩散模型）推理时施加 Feynman-Kac 引导（界面 iptm 评分 + 梯度引导 + 粒子重采样），改进分子胶诱导三元复合物结构预测，boltz-fks CLI 与 Boltz 生态兼容。

## 入口脚本

- examples/fks_steering.py
- examples/fks_steering.sh
- src/boltz/main.py
- boltz-fks predict CLI
- scripts/train/train.py

## 数据加载

- src/boltz（Boltz 数据管线）
- examples/（prot/ligand/pocket/multimer/cyclic_prot/affinity 等 yaml+fasta 输入样例）

## 模型权重

- Boltz 权重沿官方机制自动下载；examples/msa 附带 MSA 样例

## 评测基准

- scripts/eval/run_evals.py
- scripts/eval/aggregate_evals.py
- tests/（model 回归与 kernel 测试）

## 文档

- README.md
- examples/
- pyproject.toml

## 课题关联

- C16
- C004
- C007

## 与论文/课题的组合方式

- C
- 0
- 0
- 4
- /
- C
- 1
- 6
-  
- 课
- 题
- 的
- 直
- 接
- 工
- 具
- ：
- 对
- 分
- 子
- 胶
- /
- b
- i
- n
- d
- e
- r
-  
- 三
- 元
- 复
- 合
- 物
- 做
-  
- F
- K
-  
- 引
- 导
- 结
- 构
- 预
- 测
- 与
- 界
- 面
- 评
- 分
- ；
- 其
- 『
- 推
- 理
- 时
-  
- F
- e
- y
- n
- m
- a
- n
- -
- K
- a
- c
-  
- 引
- 导
- 控
- 制
- 扩
- 散
- 』
- 思
- 路
- 可
- 迁
- 移
- 到
- 其
- 他
- 生
- 成
- 模
- 型
- 的
- 条
- 件
- 控
- 制
- （
- C
- 0
- 0
- 7
- ）
- ，
- 与
-  
- P
- o
- s
- e
- X
-  
- 评
- 测
- 协
- 议
- 组
- 合
- 形
- 成
- 预
- 测
- -
- 评
- 测
- 闭
- 环
- 。
