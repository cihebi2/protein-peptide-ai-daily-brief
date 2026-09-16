# jsunn-y/care

- **仓库：** [https://github.com/jsunn-y/care](https://github.com/jsunn-y/care)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 数据集+划分+基线排名结果齐全（Zenodo 双链接），评测协议完整可复现；注意：本地克隆工作树为空（checkout 损坏），内容完好保存在 git 对象中，使用前需重新 checkout
- **能力：** benchmark、data_loader、database、protocol

## 仓库摘要

CARE（NeurIPS D&B 2024）：酶功能预测的数据集与基准套件，任务1为按 EC 编号做酶序列分类、任务2为给定反应检索 EC，含按序列一致性（<30%、30-50%）划分的新颖性 splits。

## 入口脚本

- task1_baselines/（EC 分类基线脚本目录）
- task2_baselines/（EC 检索基线脚本目录）
- performance_evaluation.ipynb

## 数据加载

- generate_datasets_splits/（数据构建 notebook）
- processed_data/
- splits/

## 模型权重

- 无模型权重；处理后数据 Zenodo: https://zenodo.org/records/14004425，原始数据 Zenodo: https://zenodo.org/records/12207966

## 评测基准

- performance_evaluation.ipynb
- task1_baselines/results_summary/
- task2_baselines/results_summary/

## 文档

- README.md
- task1_baselines/
- task2_baselines/

## 课题关联

- C008
- C011
- C013

## 与论文/课题的组合方式

- 其按序列一致性划分 train/test 的做法是 C013 基线新颖性评估的直接模板
- 分级（EC 1-4 级）准确率的多层级评测协议可迁移到 C011 评估协议课题
- 基准+基线结果汇总的组织方式可作为 C008 基准校准课题的仓库架构参考
