# 0answer0/slerpflow

- **仓库：** [https://github.com/0answer0/slerpflow](https://github.com/0answer0/slerpflow)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0（代码，继承自 FireFlow；FLUX.1-dev 权重为非商业许可）
- **语言：** Python
- **复用度：** medium —— 单文件入口+示例图+脚本齐全、方法即插即用，但依赖 HF 受限门控的 FLUX.1-dev 大权重与 GPU；无训练管线
- **能力：** inference

## 仓库摘要

SlerpFlow（ICML 2026 poster）为 FLUX 整流流（rectified flow）反演与图像编辑提供球面线插（Slerp）速度轨迹修正采样器，在同等 NFE 下比 FireFlow 基线编辑语义更准，单文件入口即用。

## 入口脚本

- run_slerp_edit.py
- run_rose_recon.sh
- run_mushroom.sh
- run_slerp 系列重建/编辑脚本

## 数据加载

- 无数据集；examples/source 内置示例图，examples/recon-result 与 edit-result 含结果对照

## 模型权重

- flux/（模型与采样器，slerp 位于 flux/sampling.py）；FLUX.1-dev 与 AE 权重从 HF black-forest-labs/FLUX.1-dev 下载或经 FLUX_DEV/AE 环境变量指定

## 评测基准

- 无正式 benchmark（examples 编辑/重建对比；--strategy fireflow 可复现基线）

## 文档

- README.md
- requirements.txt
- env.sh
- model_licenses/

## 课题关联

- C007

## 与论文/课题的组合方式

- 方
- 法
- 论
- 迁
- 移
- 型
- 资
- 产
- ：
- 『
- S
- l
- e
- r
- p
-  
- 修
- 正
- 速
- 度
- 场
-  
- +
-  
- 少
- 步
- 采
- 样
-  
- +
-  
- 反
- 演
- 编
- 辑
- 』
- 可
- 借
- 鉴
- 到
- 流
- 匹
- 配
- 蛋
- 白
- /
- 分
- 子
- 生
- 成
- （
- C
- 0
- 0
- 7
- ）
- 的
- 少
- 步
- 采
- 样
- 与
- 结
- 构
- 编
- 辑
- ，
- 例
- 如
- 与
-  
- M
- M
- D
- i
- f
- f
-  
- 扩
- 散
- 骨
- 架
- 或
-  
- V
- F
- M
-  
- 流
- 图
- 组
- 合
- 做
- 推
- 理
- 期
- 轨
- 迹
- 修
- 正
- ；
- 与
- 生
- 物
- 课
- 题
- 为
- 间
- 接
- 关
- 联
- 。
