# willhua127/enzymeflow

- **仓库：** [https://github.com/willhua127/enzymeflow](https://github.com/willhua127/enzymeflow)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** CC-BY-NC-4.0
- **语言：** Python
- **复用度：** medium —— 训练/推理/评测代码与 demo notebook 完整，评测数据部分内置（rfdiffaa_generated 等），但完整训练数据需按 README 自行准备、权重需从 Google Drive 下载 mini 版，依赖较重（OpenMM/mdtraj 等）
- **能力：** data_loader、training_pipeline、inference、benchmark

## 仓库摘要

EnzymeFlow 通过流匹配（flow-matching）与共进化动力学（MSA 预训练 MSAFormer）生成反应特异的酶催化口袋：给定反应底物生成结合口袋结构，再结合逆折叠设计序列。NeurIPS 系工作，含与 RFDiffAA/LigandMPNN 的基线对比。

## 入口脚本

- train_ddp.py
- inference.py
- sampling.py
- process_data.py
- enzymeflow_demo.ipynb
- unseen_reaction.ipynb

## 数据加载

- data/data.py
- data/loader.py
- data/utils.py
- flowmatch/flowmatcher.py

## 模型权重

- mini-EnzymeFlow checkpoint 在 Google Drive（README 给出链接），需下载放入 ./checkpoint；仓库内无权重文件

## 评测基准

- evaluation/metrics.py
- evaluation/loss.py
- eval_configs.py
- data/eval-data_cutoff-0.1_unique-subs-enz_100.csv
- data/metadata_eval.csv
- data/rfdiffaa_generated/（RFDiffAA 基线生成样本与 LigandMPNN/CLEAN 预测结果）

## 文档

- README.md
- enzymeflow_demo.ipynb
- unseen_reaction.ipynb

## 课题关联

- C007
- C004

## 与论文/课题的组合方式

- 条件生成课题（C007）的方法学模板：'条件分子+flow-matching 结构生成+逆折叠'三段式可直接迁移到肽 binder 条件生成；其 RFDiffAA/LigandMPNN/CLEAN 的基线评测协议可复用作生成结构质量与功能注释的评估流程。
