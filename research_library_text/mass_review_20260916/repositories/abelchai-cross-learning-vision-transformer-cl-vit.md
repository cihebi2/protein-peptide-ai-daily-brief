# abelchai/cross-learning-vision-transformer-cl-vit

- **仓库：** [https://github.com/abelchai/cross-learning-vision-transformer-cl-vit](https://github.com/abelchai/cross-learning-vision-transformer-cl-vit)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** low —— 仅两个模型定义文件与 CSV 元数据，缺训练/评测主脚本与图像数据（需自备 PlantVillage），属论文配套碎片代码
- **能力：** training_pipeline、benchmark、visualization

## 仓库摘要

CL-ViT / FF-ViT：植物病害零样本（unseen crop-disease 组合）识别的视觉 Transformer 方法，含自监督 pretext 任务与合成特征融合（Neurocomputing 2024）。

## 入口脚本

- model/CL-ViT.py
- model/FF-ViT.py

## 数据加载

- dataset/csv_CLViT/
- dataset/csv_FFViT/（PlantVillage 图像元数据 CSV，图像需另行下载）

## 模型权重

- README 提供 ViT base 预训练权重下载链接（timm jx_vit_base_p16_224）

## 评测基准

- README Results 部分（多作物-病害零样本基准）

## 文档

- README.md
- requirements_clvit.txt
- requirements_ffvit.txt

## 课题关联

- C005

## 与论文/课题的组合方式

- 其
- 『
- s
- e
- e
- n
- /
- u
- n
- s
- e
- e
- n
-  
- 组
- 合
- 零
- 样
- 本
- 划
- 分
-  
- +
-  
- S
- S
- L
-  
- p
- r
- e
- t
- e
- x
- t
- 』
- 协
- 议
- 可
- 类
- 比
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
- 泛
- 化
- 课
- 题
- （
- u
- n
- s
- e
- e
- n
-  
- 条
- 件
- 泛
- 化
- 评
- 测
- 设
- 计
- ）
- ，
- 但
- 代
- 码
- 完
- 整
- 度
- 低
- 仅
- 作
- 参
- 考
- 。
