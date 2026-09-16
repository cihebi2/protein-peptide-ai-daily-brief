# bz99bz/m-3

- **仓库：** [https://github.com/bz99bz/m-3](https://github.com/bz99bz/m-3)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0（LICENSE 文件为 GPL-3.0；README 声称 MIT，以 LICENSE 文件为准）
- **语言：** Python
- **复用度：** high —— MPP/ 目录本地即含 10 个多模态性质预测 CSV（含 Tox21/ClinTox/Sider 毒性端点），完整 2000 万分子数据集有全量下载链接
- **能力：** database、data_loader

## 仓库摘要

M^3-20M：首个大规模多模态分子数据集（2000 万分子），覆盖 SMILES、2D 图、3D 结构、理化性质与文本描述，并附多模态分子性质预测（MPP）子集。

## 入口脚本

- tools/2D_images.py
- tools/PubMed.py
- Crawler_physicochemical_properties/Crawler_physicochemical_properties.py

## 数据加载

- Dataset/readme.md（大数据集经 Google Drive/HuggingFace(Alex99Gsy/M-3_Multi-Modal-Molecule)/百度云 下载）

## 模型权重

- 无模型，纯数据资产

## 评测基准

- Experiments/readme.md

## 文档

- README.md
- Dataset/readme.md
- Experiments/readme.md

## 课题关联

- C002
- C003
- C005

## 与论文/课题的组合方式

- T
- o
- x
- 2
- 1
- /
- C
- l
- i
- n
- T
- o
- x
- /
- S
- i
- d
- e
- r
-  
- 多
- 模
- 态
-  
- C
- S
- V
-  
- 可
- 直
- 接
- 作
- 为
-  
- C
- 0
- 0
- 2
-  
- 毒
- 性
- 预
- 测
- 与
-  
- C
- 0
- 0
- 3
-  
- 多
- 端
- 点
- 课
- 题
- 的
- 现
- 成
- 数
- 据
- 源
- ；
- 文
- 本
- 描
- 述
- 模
- 态
- 可
- 支
- 撑
- 分
- 子
- -
- 文
- 本
- 跨
- 模
- 态
- 生
- 成
- 复
- 现
- 。
