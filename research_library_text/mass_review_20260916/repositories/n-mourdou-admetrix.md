# n-mourdou/admetrix

- **仓库：** [https://github.com/n-mourdou/admetrix](https://github.com/n-mourdou/admetrix)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** research_use_only（自定义 Research Use Only 许可，非 OSI 标准协议）
- **语言：** Python
- **复用度：** high —— 完整多目标生成管线：附带 REINVENT 预训练先验（reinvent.prior）、GuacaMol 训练 SMILES、多 seed 生成结果、骨架跳跃数据与评测模块；但需另装增强版 REINVENT4 fork 与 ADMET AI（Docker 可选），许可为 Research Use Only
- **能力：** training_pipeline、inference、benchmark、data_loader、visualization

## 仓库摘要

ADMETrix：将 REINVENT4 与 ADMET AI 集成的从头分子生成框架，在生成过程中对 27 个 ADMET 性质与 10 个理化描述符做实时多目标优化，并支持骨架跳跃（降毒性）与 GuacaMol 基准评测。ICANN 2025 AI for Drug Discovery Workshop 论文。

## 入口脚本

- src/admet_optimization.py
- src/scaffold_hopping.py
- src/admet_server.py
- src/ADMETrix_results.ipynb

## 数据加载

- src/utils.py
- src/conf/config.yaml（Hydra 配置）

## 模型权重

- src/priors/reinvent.prior（预训练 REINVENT 先验权重，已含）

## 评测基准

- src/evaluation/metrics.py
- src/evaluation/fcd_computation.py
- src/evaluation/kl_divergence.py
- src/evaluation/eval_utils.py

## 文档

- README.md（16KB，含架构图与快速开始）
- environment.yml
- Dockerfile.admet
- docker-compose.yml
- src/data/scaffold_hopping/scaffold_hopping.mp4

## 课题关联

- C003多端点（27 个 ADMET 端点+10 理化描述符的多目标优化是直接同构问题）
- C002肽毒性（含毒性降低的骨架跳跃示范，方法论可迁移）
- C007条件生成（性质约束下的从头生成）
- C008基准校准（GuacaMol FCD/KL 评测指标实现）

## 与论文/课题的组合方式

- 与
- 多
- 端
- 点
- 优
- 化
- 课
- 题
- （
- C
- 0
- 0
- 3
- ）
- 组
- 合
- ：
- 其
-  
- 2
- 7
-  
- 端
- 点
- 奖
- 励
- 加
- 权
- 方
- 案
- 与
-  
- G
- u
- a
- c
- a
- M
- o
- l
-  
- 评
- 测
- （
- F
- C
- D
- /
- K
- L
- ）
- 可
- 直
- 接
- 作
- 为
- 分
- 子
- 端
- 多
- 目
- 标
- 生
- 成
- 的
- 参
- 照
- 实
- 现
- ；
- 毒
- 性
- 骨
- 架
- 跳
- 跃
- （
- 双
- 氯
- 芬
- 酸
- 案
- 例
- ）
- 可
- 与
-  
- C
- 0
- 0
- 2
-  
- 联
- 用
- 研
- 究
- 毒
- 性
- 降
- 低
- 的
- 结
- 构
- 操
- 作
- 。
