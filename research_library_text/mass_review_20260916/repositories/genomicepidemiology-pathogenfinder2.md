# genomicepidemiology/pathogenfinder2

- **仓库：** [https://github.com/genomicepidemiology/pathogenfinder2](https://github.com/genomicepidemiology/pathogenfinder2)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **语言：** Python
- **复用度：** medium —— 管线、测试与文档完整且含 Dockerfile（dockerfile_PF2），但预训练权重、ProtT5 模型及 Prodigal/DIAMOND 外部可执行需按文档另行获取
- **能力：** inference、data_loader、training_pipeline、protocol

## 仓库摘要

PathogenFinder2 用 Prodigal 预测蛋白 + ProtT5 蛋白质语言模型嵌入 + 卷积/注意力深度网络（4模型集成）预测细菌基因组对人致病能力，CLI 含 predict/train/infer_proteomeLM 四模式，可输出注意力热点蛋白与致病性景观映射，是 DTU CGE web 服务同款代码。

## 入口脚本

- src/pathogenfinder2/main.py
- src/pathogenfinder2/cli.py
- bin/（CLI 入口）

## 数据加载

- src/pathogenfinder2/data
- data/PathogenFinder2_dataset（含 METADATA_2024strain.tsv）
- data/configs/config_train.json

## 模型权重

- 预训练权重经 --weightsModel 参数加载（仓库内未见权重文件，按文档下载）；ProtT5 嵌入模型按 --protT5Path 指定

## 评测基准

- test/（完整 pytest 套件：test_gpu_inference.py、test_engine.py、test_landscape.py 等）
- test/configs/config_inference.json

## 文档

- README.md
- docs/Installation.md
- docs/Test.md
- docs/DataPF2.md
- TODOS.md

## 课题关联

- C005

## 与论文/课题的组合方式

- 作
- 为
- 『
- 蛋
- 白
- 质
- 语
- 言
- 模
- 型
- 嵌
- 入
- →
- 表
- 型
- 分
- 类
- +
- 注
- 意
- 力
- 可
- 解
- 释
- 』
- 的
- 成
- 熟
- 范
- 式
- 参
- 考
- ，
- 可
- 迁
- 移
- 到
-  
- C
- 0
- 0
- 5
-  
- 表
- 型
- 课
- 题
- 或
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
- 建
- 模
- （
- 按
- 条
- 件
- /
- 物
- 种
- 分
- 组
- 做
- 嵌
- 入
- 分
- 类
- ）
- ；
- 其
-  
- H
- D
- F
- 5
-  
- 蛋
- 白
- 质
- 组
- 嵌
- 入
- 预
- 生
- 成
- 流
- 程
- （
- i
- n
- f
- e
- r
- _
- p
- r
- o
- t
- e
- o
- m
- e
- L
- M
- ）
- 值
- 得
- 复
- 用
- 。
