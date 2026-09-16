# dchen0212/trimole_hybrid

- **仓库：** [https://github.com/dchen0212/trimole_hybrid](https://github.com/dchen0212/trimole_hybrid)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** medium —— 代码与审计文档完整但明确排除官方数据集、训练权重与缓存 embedding，非一键复跑包，需自备 TDC 数据
- **能力：** training_pipeline、inference、benchmark、data_loader

## 仓库摘要

多模态分子 ADMET 预测平台（SMILES 序列/KPGT 图/UniMol 3D/化学先验多分支融合 + 经典模型集成），面向 TDC ADMET 22 端点基准，本仓库为论文手稿的源码与审计包。

## 入口脚本

- code/trimole_ept_swap_v1/run_xl_prediction_blend_all22_v1.py
- code/trimole_ept_swap_v1/run_xl_metric_calibrated_blend_all22_v2.py
- code/trimole_hybrid/trimole_inference_ablation_all22_v1.py

## 数据加载

- code/trimole_hybrid/（核心包，数据需从 TDC 外部获取）
- code/KPGT/（图分支编码器源码依赖）

## 模型权重

- 无（README 明确排除训练权重与序列化模型）

## 评测基准

- supplementary_tables/Table_S1_TDC_ADMET22_benchmark.csv
- docs/MODEL_FAMILY_INDEX.md
- docs/PULL_COMPLETENESS_AUDIT.md

## 文档

- README.md
- ENVIRONMENT.md
- CODE_AVAILABILITY.md
- supplementary/supplementary.pdf

## 课题关联

- C003
- C008
- C011

## 与论文/课题的组合方式

- 作
- 为
-  
- C
- 0
- 0
- 3
-  
- 多
- 端
- 点
-  
- A
- D
- M
- E
- T
-  
- 的
- 强
- 基
- 线
- 与
-  
- T
- D
- C
-  
- 基
- 准
- 参
- 照
- ；
- 其
- 『
- 仅
- 用
- 训
- 练
- /
- 验
- 证
- 证
- 据
- 选
- 端
- 点
- 、
- 官
- 方
- 测
- 试
- 集
- 只
- 做
- 最
- 终
- 报
- 告
- 』
- 的
- 评
- 估
- 纪
- 律
- 可
- 直
- 接
- 移
- 植
- 到
-  
- C
- 0
- 0
- 8
- /
- C
- 0
- 1
- 1
-  
- 课
- 题
- 的
- 评
- 估
- 协
- 议
- 设
- 计
- 。
