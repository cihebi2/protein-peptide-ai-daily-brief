# 10ring/laa-net

- **仓库：** [https://github.com/10ring/laa-net](https://github.com/10ring/laa-net)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** other（SnT academic license，基于 MIT 附加学术使用限制）
- **语言：** Python
- **复用度：** medium —— 训练/数据管线完整且有 Dropbox 预训练权重，但训练评测需自备 FF++ 等大型视频数据集；与生物医药课题无关联，复用价值主要在方法论（显式注意力+跨数据集泛化评测协议）
- **能力：** training_pipeline、inference、data_loader

## 仓库摘要

LAA-Net（CVPR 2024）：面向高质量 deepfake 检测的局部伪影注意力网络，用多任务框架下的热图+自一致性显式注意力与 E-FPN 特征金字塔聚焦伪影区域，在 FF++/CDF/DFW/DFD/DFDC 跨数据集评测中泛化性强。属于计算机视觉/鉴伪领域，与生物医药课题族无直接关联。

## 入口脚本

- scripts/train.py
- scripts/train.sh
- scripts/train_efn.sh
- scripts/train_efn_adv.sh

## 数据加载

- datasets/pipelines/
- datasets/sbi/utils.py
- package_utils/images_crop.py

## 模型权重

- 无内置权重；BI/SBI 两种预训练权重经 Dropbox 链接分发（README 提供）

## 评测基准

- configs/
- scripts/train.sh

## 文档

- README.md
- dockerfiles/README.md
- Third_Party_License_Notice

## 课题关联

- （无）

## 与论文/课题的组合方式

- 与
-  
- C
- V
- P
- R
- 2
- 0
- 2
- 4
-  
- 论
- 文
- 组
- 合
- 可
- 复
- 现
-  
- d
- e
- e
- p
- f
- a
- k
- e
-  
- 跨
- 数
- 据
- 集
- 泛
- 化
- 基
- 准
- ；
- 对
- 课
- 题
- 族
- 的
- 启
- 示
- 限
- 于
- 其
- 跨
- 域
- 泛
- 化
- 评
- 测
- 协
- 议
- （
- i
- n
- -
- d
- a
- t
- a
- s
- e
- t
-  
- v
- s
-  
- c
- r
- o
- s
- s
- -
- d
- a
- t
- a
- s
- e
- t
-  
- A
- U
- C
- /
- A
- P
- ）
- ，
- 可
- 类
- 比
- 迁
- 移
- 到
-  
- C
- 0
- 1
- 1
-  
- 评
- 估
- 协
- 议
- 讨
- 论
- ，
- 但
- 无
- 直
- 接
- 生
- 物
- 数
- 据
- 复
- 用
- 点
