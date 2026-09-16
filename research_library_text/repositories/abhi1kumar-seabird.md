# abhi1kumar/seabird

- **仓库：** [https://github.com/abhi1kumar/seabird](https://github.com/abhi1kumar/seabird)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** medium —— 工程完整（配置/权重/日志齐全、MIT），但属自动驾驶 3D 检测领域，数据集需注册获取，与分子/蛋白课题族无关
- **能力：** training_pipeline、inference、benchmark、visualization

## 仓库摘要

SeaBird（CVPR 2024）：鸟瞰图分割 + Dice Loss 改进单目 3D 大物体检测，含 PanopticBEV（KITTI-360 单相机）与 HoP（nuScenes 多相机）两个子项目及完整模型动物园。

## 入口脚本

- PanopticBEV/（单相机 KITTI-360 管线）
- HoP/（多相机 nuScenes 管线，mmdet3d 配置）

## 数据加载

- KITTI-360 与 nuScenes 数据需自行注册获取（mmdet3d 标准数据管线）

## 模型权重

- README Model Zoo 提供各阶段 gdrive 权重与日志下载链接（KITTI-360 Val/Test、nuScenes 多分辨率）

## 评测基准

- KITTI-360 / nuScenes 榜单评测（AP_Lrg、mAP、NDS 等指标表）

## 文档

- README.md（含 demo、配置、权重链接）

## 课题关联

- （无）

## 与论文/课题的组合方式

- 与
- 本
- 课
- 题
- 族
- 无
- 直
- 接
- 关
- 联
- ；
- 其
- '
- D
- i
- c
- e
-  
- L
- o
- s
- s
-  
- 对
- 噪
- 声
- 与
- 大
- 目
- 标
- 的
- 稳
- 健
- 性
- '
- 理
- 论
- 分
- 析
- 可
- 作
- 为
- 损
- 失
- 函
- 数
- 稳
- 健
- 性
- 研
- 究
- 的
- 方
- 法
- 论
- 参
- 考
- ，
- 但
- 不
- 纳
- 入
- 课
- 题
- 组
- 合
- 。
