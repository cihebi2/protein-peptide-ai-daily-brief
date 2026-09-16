# xl-s224/aamfm

- **仓库：** [https://github.com/xl-s224/aamfm](https://github.com/xl-s224/aamfm)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 三阶段训练+生成+评测脚本齐全，checkpoint 托管在 HuggingFace，RAbD 评测集与参考 PDB 内嵌仓库；需外部 GearNet 特征文件与 US-align 可执行文件
- **能力：** training_pipeline、inference、benchmark、data_loader、protocol

## 仓库摘要

AAMFM（arXiv 2607.20057）官方实现：抗原条件抗体多模态基础模型，联合建模抗体序列与结构、条件于抗原几何与表位注释，经 CPT→SFT→Cal-DPO（校准偏好优化）三阶段训练，输入抗原+表位 mask+框架序列生成 CDR 序列与完整抗体结构。

## 入口脚本

- scripts/run_cpt.sh
- scripts/run_sft.sh
- scripts/run_dpo.sh
- scripts/run_generate.sh
- scripts/run_evaluate.sh
- scripts/run_compute_pll.sh

## 数据加载

- src/eval/runtime_data.py
- datasets/（含内嵌 RAbD 评测集 rabd.json 与参考 PDB）

## 模型权重

- HuggingFace checkpoint：GENTEL-Lab/AAMFM；GearNet 抗原特征 Google Drive 下载至 datasets/eval/rabd/gearnet_node_features.pt

## 评测基准

- src/eval/evaluate.py
- src/eval/compute_pll.py
- src/eval/generate.py
- datasets/eval/rabd/（RAbD 基准）

## 文档

- README.md
- requirements.txt
- assets/aamfm-overview.png

## 课题关联

- C004 binder/PPI
- C007 条件生成
- C010 校准弃权
- C011 评估协议

## 与论文/课题的组合方式

- C
- 0
- 0
- 4
-  
- 抗
- 体
- 设
- 计
- 课
- 题
- 的
- 主
- 力
- 复
- 现
- 对
- 象
- ：
- R
- A
- b
- D
-  
- 基
- 准
- +
- U
- S
- -
- a
- l
- i
- g
- n
-  
- 结
- 构
- 评
- 估
- +
- A
- n
- t
- i
- B
- E
- R
- T
- y
-  
- P
- L
- L
-  
- 组
- 成
- 完
- 整
- 评
- 估
- 协
- 议
- （
- C
- 0
- 1
- 1
- ）
- ；
- 其
-  
- C
- a
- l
- -
- D
- P
- O
-  
- 用
- 伪
- 似
- 然
- 约
- 束
- 做
- 校
- 准
- 偏
- 好
- 对
- 齐
- ，
- 与
-  
- C
- 0
- 1
- 0
-  
- 校
- 准
- 弃
- 权
- 课
- 题
- 的
- 方
- 法
- 论
- 直
- 接
- 可
- 组
- 合
- 。
