# 5k5000/cldetection2023

- **仓库：** [https://github.com/5k5000/cldetection2023](https://github.com/5k5000/cldetection2023)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **语言：** Python
- **复用度：** medium —— 四步流程脚本与定制的 mmpose 包完整、可复现获奖方案，但数据集无再分发权需申请，且与生物医药肽设计课题无数据复用点
- **能力：** training_pipeline、inference、data_loader、visualization

## 仓库摘要

MICCAI 2023 CLDetection 挑战赛（头颈部 X 线影像解剖标志点定位）SUTD-VLG 队获奖方案，基于 MMPose 的 step1-4 全流程（环境验证→COCO 格式转换→训练评测→测试可视化），技术报告见 arXiv:2309.17143。属医学影像关键点检测领域，与肽/蛋白课题族无直接关联。

## 入口脚本

- step1_test_mmpose.py
- step2_prepare_coco_dataset.py
- step3_train_and_evaluation.py
- step4_test_and_visualize.py
- inference_single_image.py

## 数据加载

- step2_prepare_coco_dataset.py
- cldetection_utils.py
- configs/CLdetection2023/

## 模型权重

- 无内置权重；训练数据 train_stack.mha/train-gt.json 需向 grand-challenge 官网申请获取

## 评测基准

- step3_train_and_evaluation.py
- step4_test_and_visualize.py

## 文档

- README.md
- install_env.sh

## 课题关联

- （无）

## 与论文/课题的组合方式

- 与
-  
- a
- r
- X
- i
- v
-  
- 技
- 术
- 报
- 告
- 组
- 合
- 可
- 复
- 现
- 医
- 学
- 影
- 像
- 地
- 标
- 检
- 测
- 冠
- 军
- 方
- 案
- ；
- 对
- 课
- 题
- 族
- 仅
- 方
- 法
- 论
- 参
- 考
- （
- 多
- 指
- 标
- 排
- 行
- 榜
- 评
- 测
- 经
- 验
- ）
- ，
- 无
- 直
- 接
- 生
- 物
- 资
- 产
- 可
- 复
- 用
