# abbasmammadov/vfm

- **仓库：** [https://github.com/abbasmammadov/vfm](https://github.com/abbasmammadov/vfm)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** medium —— 训练/采样/评测管线完整、2D checkerboard demo 权重内置可快速验证，但 ImageNet 级实验需自备数据、预训练骨干与 H100 级 GPU（FlashAttention-3 JVP 内核）
- **能力：** training_pipeline、inference、benchmark、data_loader

## 仓库摘要

Variational Flow Maps（Oxford/Caltech/NVIDIA，arXiv 2603.07276）联合学习噪声适配器 q(z|y) 与流图 f(z)，以变分目标实现一步/少步条件生成，面向逆问题后验采样（超分/修复/高斯与运动模糊）与 ImageNet 级生成，宣称比迭代扩散/流模型快数量级。

## 入口脚本

- train_adapter.py（accelerate 训练）
- sample_inverse.py（条件采样）
- generate.py
- samplers.py
- checkerboard/train_vfm.py（2D demo）

## 数据加载

- preprocessing/dataset.py
- preprocessing/dataset_tools.py
- inverse_problems/（超分/修复/模糊/FastMRI 前向算子）

## 模型权重

- checkerboard/checkpoints/fm_model.pt 与 mf_model.pt（2D 玩具示例权重内置）
- DMFT-B/2|L/2|XL/2 骨干从预训练 ckpt 微调（--pretrained）

## 评测基准

- checkerboard/compute_metrics.py
- preprocessing/calculate_metrics.py（FID）
- inverse_problems/test_inverse.py
- scripts/generate_fid.sh

## 文档

- README.md
- preprocessing/README.md
- scripts/train_imagenet.sh
- scripts/slurm/

## 课题关联

- C007

## 与论文/课题的组合方式

- 其
- 『
- 学
- 习
- 初
- 始
- 噪
- 声
- 分
- 布
- 而
- 非
- 引
- 导
- 轨
- 迹
- 』
- 的
- 一
- 步
- 条
- 件
- 生
- 成
- 范
- 式
- 可
- 迁
- 移
- 到
-  
- C
- 0
- 0
- 7
- ：
- 把
- 流
- 图
- 骨
- 干
- 替
- 换
- 为
-  
- S
- E
- (
- 3
- )
-  
- 蛋
- 白
- /
- 分
- 子
- 生
- 成
- 模
- 型
- （
- 如
-  
- M
- M
- D
- i
- f
- f
-  
- 骨
- 干
- ）
- 、
- 把
- 观
- 测
-  
- y
-  
- 换
- 成
- 活
- 性
- /
- 结
- 构
- 约
- 束
- ，
- 即
- 可
- 做
- 一
- 步
- 条
- 件
- 设
- 计
- 与
- 结
- 构
- 逆
- 问
- 题
- （
- 如
- 从
- 结
- 构
- 约
- 束
- 反
- 推
- 序
- 列
- -
- 构
- 象
- ）
- 。
