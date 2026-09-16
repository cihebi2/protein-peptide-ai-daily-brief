# wan-mlab/samp

- **仓库：** [https://github.com/wan-mlab/samp](https://github.com/wan-mlab/samp)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 训练与独立测试数据全部内置，Tutorial notebook 可直接跑通轻量模型，依赖极少；缺点是无 LICENSE、文档欠完整（目录导航 under construction）
- **能力：** data_loader、inference

## 仓库摘要

SAMP（Briefings in Functional Genomics 2024）用比例化拆分氨基酸组成（PSAAC）序列特征 + 集成随机投影做 AMP 预测与大规模筛选；仓库内置按物种来源（人/细菌/两栖/植物）分层的训练集与独立测试集。

## 入口脚本

- Tutorial.ipynb
- test_version1.ipynb

## 数据加载

- SAMP/_feature.py（PSAAC 等特征）
- buildFeatures.R（R 特征构建）

## 模型权重

- SAMP/_model.py（集成 RP 模型，notebook 内现场训练，无独立权重文件）

## 评测基准

- SAMP/_evaluation.py
- Independent_Dataset/（独立测试集）

## 文档

- README.md
- Tutorial.ipynb
- environment.yml

## 课题关联

- C001

## 与论文/课题的组合方式

- 其
- 按
- 物
- 种
- 来
- 源
- 分
- 层
- 的
- 独
- 立
- 测
- 试
- 集
- （
- 人
- /
- 细
- 菌
- /
- 两
- 栖
- /
- 植
- 物
- 正
- 负
- 样
- 本
- ）
- 是
-  
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
- 现
- 成
- 的
- 条
- 件
- 分
- 组
- 基
- 准
- 数
- 据
- ；
- P
- S
- A
- A
- C
- +
- 集
- 成
- 随
- 机
- 投
- 影
- 可
- 作
- 轻
- 量
- 传
- 统
- 基
- 线
- ，
- 校
- 验
- 深
- 度
- 模
- 型
- （
- 如
-  
- M
- u
- l
- t
- i
- A
- M
- P
- ）
- 的
- 真
- 实
- 增
- 益
- （
- 支
- 撑
-  
- C
- 0
- 1
- 3
- ）
- 。
