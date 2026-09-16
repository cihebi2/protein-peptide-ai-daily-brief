# oxpig/antifold

- **仓库：** [https://github.com/oxpig/antifold](https://github.com/oxpig/antifold)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** BSD-3-Clause
- **语言：** Python
- **复用度：** high —— pip 可安装、单 PDB 即可推理、模型权重有稳定下载链接、内嵌示例数据与 Colab；训练微调代码未含（仅推理），但作为抗体序列设计工具开箱可用
- **能力：** inference、data_loader、protocol

## 仓库摘要

AntiFold（Bioinformatics Advances）官方实现：基于 ESM-IF1 并在 SAbDab+OAS 抗体结构上微调的抗体逆向折叠模型，输入 VH/VL 或纳米抗体结构（可含抗原链）输出残基对数似然并可采样序列。

## 入口脚本

- antifold/main.py
- run_example.sh

## 数据加载

- antifold/if1_dataset.py
- data/pdbs/（内嵌示例 PDB）

## 模型权重

- model.pt 从 opig.stats.ox.ac.uk 下载（README 链接）；models/ 目录占位

## 评测基准

- test/tests.sh
- test/antibody_antigen.sh
- test/nanobody_antigen.sh

## 文档

- README.md
- notebook.ipynb
- notebooks/
- environment.yml

## 课题关联

- C004 binder/PPI
- C007 条件生成

## 与论文/课题的组合方式

- 可
- 直
- 接
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
- 序
- 列
- 采
- 样
- 器
- /
- 打
- 分
- 器
- ：
- 对
-  
- A
- A
- M
- F
- M
-  
- 等
- 生
- 成
- 模
- 型
- 产
- 出
- 的
- 抗
- 体
- 结
- 构
- 用
-  
- A
- n
- t
- i
- F
- o
- l
- d
-  
- 计
- 算
- 序
- 列
- 似
- 然
- 做
- 重
- 排
- 序
- ；
- 其
- 按
-  
- I
- M
- G
- T
-  
- 区
- 域
- 采
- 样
- 的
- 能
- 力
- 适
- 合
-  
- C
- D
- R
-  
- 区
- 域
- 条
- 件
- 设
- 计
- （
- C
- 0
- 0
- 7
- ）
- 。
