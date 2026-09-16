# minkaixu/alidiff

- **仓库：** [https://github.com/minkaixu/alidiff](https://github.com/minkaixu/alidiff)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** medium —— 训练/采样/评测代码齐全，但数据需遵循 TargetDiff 流程自行准备，pretrained_models 目录为空，采样/评测结果需从 Google Drive 获取
- **能力：** training_pipeline、inference、benchmark、data_loader

## 仓库摘要

NeurIPS 2024 官方实现：用精确能量优化（IPO 偏好目标）对齐靶点感知分子扩散模型（基于 TargetDiff），通过 Vina docking 偏好数据提升生成分子的结合性能。

## 入口脚本

- scripts/train_ipo.py
- scripts/sample_diffusion.py
- scripts/batch_sample_diffusion.sh
- scripts/gen_data.py
- graphbap/bapnet.py（能量打分网络）

## 数据加载

- datasets/pdbbind.py
- datasets/pl_data.py
- datasets/protein_ligand.py
- datasets/pl_pair_dataset.py
- datasets/merge_dataset.py

## 模型权重

- pretrained_models/（空目录，需按 TargetDiff 流程准备底模）；采样与评测结果在 README 中 Google Drive 链接

## 评测基准

- scripts/evaluate_diffusion.py
- scripts/evaluate_from_meta.py
- scripts/dock_baseline.py
- scripts/dock_testset.py
- scripts/likelihood_est_diffusion.py

## 文档

- README.md
- configs/training_ipo.yml
- configs/sampling.yml
- configs/training_targetdpo.yml

## 课题关联

- C007
- C016
- C013

## 与论文/课题的组合方式

- 提供'偏好对齐（IPO）改造扩散模型'的完整参考实现，可迁移到条件生成课题（C007）中改造 binder/肽生成模型
- 其 Vina docking 评测与能量打分（bapnet）管线可复用于 C016 评测
- 对齐前后与基线的系统对比可作为 C013 基线比较的实验设计模板
