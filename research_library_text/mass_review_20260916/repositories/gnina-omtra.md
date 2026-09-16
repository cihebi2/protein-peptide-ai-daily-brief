# gnina/omtra

- **仓库：** [https://github.com/gnina/omtra](https://github.com/gnina/omtra)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **语言：** Python
- **复用度：** high —— 完整 CLI（omtra 命令）+ Docker + build 脚本 + PLINDER/CrossDocked 数据 pipeline + 权重下载说明 + 复现文档与 webapp，工程化程度高
- **能力：** data_loader、training_pipeline、inference、benchmark、visualization、protocol

## 仓库摘要

OMTRA：基于 flow-matching 的多任务生成模型（小分子+蛋白体系），支持 de novo 分子生成、pocket 条件分子设计、刚性 docking、药效团条件生成等多任务（MLSB 2025，arXiv:2512.05080）。

## 入口脚本

- cli.py
- routines/train.py
- routines/sample.py
- routines/gen_sample_cmds.py

## 数据加载

- omtra/data/
- omtra/dataset/
- omtra/load/
- omtra_pipelines/crossdocked_dataset/
- omtra_pipelines/plinder_dataset/
- omtra_pipelines/pharmit_dataset/
- omtra_pipelines/latent_dataset/

## 模型权重

- omtra/trained_models/（README 指定的权重下载目录，权重另行下载）

## 评测基准

- omtra/eval/
- omtra_pipelines/docking_eval/
- notebooks/docking_evaluation.ipynb
- configs/eval/
- docs/reproducing_results.md

## 文档

- readme.md
- docs/training.md
- docs/reproducing_results.md
- docs/pharmit_dataset.md
- omtra_webapp/START.md

## 课题关联

- C007
- C016
- C004

## 与论文/课题的组合方式

- C007 条件生成的多任务统一基线：pocket/药效团条件分子设计与 docking 共用一个 flow-matching 骨架，适合做条件化策略对比
- docking_eval 管线可直接复用为 C016 的评测组件
- 多任务条件范式可迁移到 binder/肽条件生成（C004）
