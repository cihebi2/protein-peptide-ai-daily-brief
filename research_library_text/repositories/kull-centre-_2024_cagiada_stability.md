# kull-centre/_2024_cagiada_stability

- **仓库：** [https://github.com/kull-centre/_2024_cagiada_stability](https://github.com/kull-centre/_2024_cagiada_stability)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **语言：** Python (Jupyter Notebook)
- **复用度：** medium —— 代码为 Colab 笔记本+论文 SI 数据，可复现分析与预测，但 Tsuboyama2023 核心实验 CSV 需另行从 Zenodo 下载；且本地克隆工作树为空（内容在 git 对象中，需 git checkout 恢复）。
- **能力：** inference、benchmark、data_loader、visualization

## 仓库摘要

论文《Predicting absolute protein folding stability using generative models》(Protein Science 2025) 配套代码与数据：用 ESM-IF 逆折叠生成模型从结构预测绝对折叠稳定性 ΔG，含 Colab 推理笔记本与全部实验数据集（Tsuboyama2023、Maxwell2005 等）。

## 入口脚本

- stab_ESM-IF.ipynb (Colab 推理)
- paper_SI/dG_pred_SI.ipynb (论文全部分析复现)

## 数据加载

- paper_SI/exp_scores/ (实验 dG 数据)
- paper_SI/dssp_pred/ (DSSP/RASA 特征)

## 模型权重

- ESM-IF 经 Colab 自动下载，无本地权重文件；Tsuboyama2023 大 CSV 需从论文 Zenodo 补充下载

## 评测基准

- paper_SI/dG_pred_SI.ipynb
- paper_SI/tsuboyama2023/
- paper_SI/maxwell2005/

## 文档

- README.md

## 课题关联

- C013基线新颖性
- C001AMP条件活性

## 与论文/课题的组合方式

- E
- S
- M
- -
- I
- F
-  
- 野
- 生
- 型
- 概
- 率
- 求
- 和
- →
- Δ
- G
-  
- 的
- 做
- 法
- 可
- 作
- 为
- 生
- 成
- 模
- 型
- 做
- 稳
- 定
- 性
- /
- 活
- 性
- 预
- 测
- 的
- 基
- 线
- 方
- 法
- （
- C
- 0
- 1
- 3
- 、
- C
- 0
- 0
- 1
-  
- 方
- 法
- 学
- 参
- 考
- ）
- ；
- T
- s
- u
- b
- o
- y
- a
- m
- a
- /
- M
- a
- x
- w
- e
- l
- l
-  
- 实
- 验
-  
- d
- G
-  
- 数
- 据
- 集
- 可
- 复
- 用
- 为
- 稳
- 定
- 性
- 多
- 端
- 点
- 评
- 估
- 的
- 外
- 部
- 基
- 准
- 。
