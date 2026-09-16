# lzlinn801/spgo

- **仓库：** [https://github.com/lzlinn801/spgo](https://github.com/lzlinn801/spgo)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 本地含训练 FASTA、权重有 GDrive 链接、训练+生成脚本齐全；扣分项：无 LICENSE、仓库极简、SignalP6 需外部获取
- **能力：** training_pipeline、inference、protocol

## 仓库摘要

SPgo：Sec 型信号肽从头设计混合模型——N 区/C 区用规则模板、疏水 H 区用 BERT+BiLSTM 生成，支持 top-k/top-p 采样与 SignalP6 功能验证。

## 入口脚本

- Model/training.py
- Model/Sequence_generation.py

## 数据加载

- Data/dataset.fasta（本地已含 FASTA 训练数据）

## 模型权重

- checkpoint 经 README 中 Google Drive 链接下载（1ElvvCBtIcbXLl4MakJ6_VIGdzHD1nV6W）

## 评测基准

- SignalP6 外部验证流程（README 描述，需另行安装 SignalP6）

## 文档

- README.md
- requirements.txt

## 课题关联

- C001
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
- 借
- 鉴
- 其
- '
- 规
- 则
- 约
- 束
- 生
- 成
- 区
- +
- 学
- 习
- 生
- 成
- 区
- '
- 的
- 混
- 合
- 策
- 略
- （
- 条
- 件
- 先
- 验
- +
- 神
- 经
- 生
- 成
- ）
- ；
- 生
- 成
- 的
- 信
- 号
- 肽
- 拼
- 接
- 目
- 标
- 蛋
- 白
- 后
- 经
-  
- S
- i
- g
- n
- a
- l
- P
- 6
-  
- 验
- 证
- 的
- 协
- 议
- 可
- 直
- 接
- 搬
- 用
- 到
-  
- A
- M
- P
-  
- 分
- 泌
- 表
- 达
- 设
- 计
- 。
