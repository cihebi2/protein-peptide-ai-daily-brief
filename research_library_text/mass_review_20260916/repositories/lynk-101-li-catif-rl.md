# lynk-101-li/catif-rl

- **仓库：** [https://github.com/lynk-101-li/catif-rl](https://github.com/lynk-101-li/catif-rl)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 编号脚本化的四阶段完整管线（数据构建→监督→GDC→GRPO），含冒烟测试 CI、复现文档、case study 与预训练权重下载说明；数据集与权重需按 README 下载
- **能力：** training_pipeline、inference、benchmark、data_loader、protocol

## 仓库摘要

CatIF-RL（JCIM，DOI 10.1021/acs.jcim.6c01587）官方实现：将图离散扩散逆向折叠模型改造成活性导向的酶序列生成器——GDC 生成式数据策展 + KL 正则 GRPO 三轮强化学习，以 kcat 预测器集成打分，在保持折叠兼容性（recovery/RMSD）下提升预测催化活性约 4 倍。

## 入口脚本

- scripts/01_build_dataset.sh
- scripts/02_train_enzymeif.sh
- scripts/03_run_gdc.sh
- scripts/04_train_catif.sh
- scripts/05a_rl_round1.sh
- scripts/06_sample_benchmark.sh
- catif_rl/sampling/infer.py

## 数据加载

- catif_rl/data/dataset.py
- catif_rl/data/brenda.py
- catif_rl/data/cath_imem.py
- catif_rl/data/download_pdb.py
- catif_rl/data/esmfold_backbones.py

## 模型权重

- checkpoints/README.md 提供预训练权重下载（如 catif_rl_R3_epoch02.pt）；外部依赖 DLKcat/UniKP/CataPro 与 GraDe-IF 由 scripts/00_setup_external.sh 克隆

## 评测基准

- catif_rl/evaluation/（recovery.py、structural.py、success_rate.py、statistics.py、baselines.py）
- scripts/06_sample_benchmark.sh（5 seed × 11 方法基准）

## 文档

- README.md
- docs/reproducing_paper.md
- docs/grpo_algorithm.md
- docs/inpainting_algorithm.md
- docs/dataset_construction.md
- notebooks/
- case_study/

## 课题关联

- C001 AMP条件活性
- C007 条件生成
- C011 评估协议
- C013 基线新颖性

## 与论文/课题的组合方式

- 这
- 是
- '
- 活
- 性
- 导
- 向
- 条
- 件
- 生
- 成
- '
- 方
- 法
- 论
- 的
- 直
- 接
- 模
- 板
- ：
- 把
-  
- k
- c
- a
- t
-  
- 集
- 成
- 换
- 成
-  
- A
- M
- P
-  
- 活
- 性
- /
- 毒
- 性
- 预
- 测
- 器
- 即
- 可
- 迁
- 移
- 到
-  
- C
- 0
- 0
- 1
- /
- C
- 0
- 0
- 2
- ；
- 其
-  
- G
- D
- C
- （
- 生
- 成
- -
- 过
- 滤
- -
- 策
- 展
- ）
- +
-  
- K
- L
-  
- 正
- 则
-  
- G
- R
- P
- O
-  
- 流
- 程
- 与
-  
- 1
- 1
-  
- 方
- 法
- 基
- 线
- 对
- 比
- 协
- 议
- 可
- 整
- 体
- 复
- 用
- 于
-  
- C
- 0
- 0
- 7
-  
- 与
-  
- C
- 0
- 1
- 3
-  
- 课
- 题
- 。
