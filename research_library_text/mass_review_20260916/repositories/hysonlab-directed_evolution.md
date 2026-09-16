# hysonlab/directed_evolution

- **仓库：** [https://github.com/hysonlab/directed_evolution](https://github.com/hysonlab/directed_evolution)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **语言：** Python
- **复用度：** high —— 训练+推理完整管线、pip 安装、8 个预处理的 DMS 适应度数据集直接内置，README 参数说明详细；仅 oracle 权重需自行训练（数据齐全可复现）
- **能力：** training_pipeline、inference、data_loader、benchmark

## 仓库摘要

MLDE：大语言模型（ESM 编码器）引导的定向进化蛋白质设计框架，训练 Attention1D oracle 预测序列适应度并引导离散进化搜索。发表于 IEEE TEVC 2024。

## 入口脚本

- scripts/train_decoder.py
- scripts/run_discrete_de.py
- scripts/run_de.sh
- de/directed_evolution.py

## 数据加载

- de/dataio/
- scripts/preprocess/

## 模型权重

- 无内置 checkpoint（exps/checkpoints 为空）；oracle 需用内置数据训练，编码器用 facebook/esm_t12_35M_UR5D（HuggingFace 下载）

## 评测基准

- preprocessed_data/（AAV、AMIE、avGFP、E4B、LGK、Pab1、TEM、UBE2I 共 8 个定向进化适应度数据集，含 CSV 与参考序列）

## 文档

- README.md
- assets/main.png

## 课题关联

- C005表型
- C013基线新颖性

## 与论文/课题的组合方式

- 与
- 蛋
- 白
- 适
- 应
- 度
- /
- 表
- 型
- 预
- 测
- 课
- 题
- （
- C
- 0
- 0
- 5
- ）
- 组
- 合
- ：
- 8
-  
- 个
- 内
- 置
-  
- D
- M
- S
-  
- 数
- 据
- 集
- 可
- 直
- 接
- 作
- 为
- 多
- 端
- 点
- /
- 适
- 应
- 度
- 预
- 测
- 的
- 基
- 准
- 数
- 据
- ；
- M
- L
- D
- E
-  
- 的
-  
- L
- L
- M
- +
- o
- r
- a
- c
- l
- e
-  
- 进
- 化
- 搜
- 索
- 管
- 线
- 可
- 作
- 为
- 序
- 列
- 设
- 计
- 类
- 课
- 题
- 的
- 强
- 基
- 线
- 对
- 照
- 。
