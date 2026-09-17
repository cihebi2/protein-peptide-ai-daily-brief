# chemprop/chemprop

- **仓库：** [https://github.com/chemprop/chemprop](https://github.com/chemprop/chemprop)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1038/s41586-023-06887-8
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 积极维护的标准工业级工具（PyPI/conda 可装、CI 测试、readthedocs、MIT）：数据划分/多任务/超参优化/不确定性估计模块齐全，examples 教程完备，可直接作为分子与肽性质预测的强基线和生产级管线。
- **能力：** data_loader、training_pipeline、inference、benchmark、protocol

## 仓库摘要

Chemprop：面向分子性质预测的消息传递神经网络（D-MPNN）标准软件包（当前为 v2 重写版），提供训练/预测/超参优化/指纹/不确定性估计的完整 CLI 与 Python API。关联论文用它预测抗菌活性并结合可解释性发现了对 MRSA/VRE 选择性生效的新抗生素结构类别。

## 入口脚本

- chemprop/cli/main.py
- chemprop/cli/train.py
- chemprop/cli/predict.py
- chemprop/cli/hpopt.py
- chemprop/cli/fingerprint.py
- chemprop/cli/convert.py

## 数据加载

- chemprop/data/dataloader.py
- chemprop/data/datasets.py
- chemprop/data/splitting.py
- chemprop/data/samplers.py
- chemprop/data/collate.py
- chemprop/featurizers/

## 模型权重

- 无内置权重；README 引用 Zenodo Halicin 检查点（10.5281/zenodo.6527882）及 ADMET-AI 预训练模型（swansonk14/admet_ai）

## 评测基准

- tests/
- examples/（教程 notebook：multi_task、active_learning、hpopting、不确定性相关等）

## 文档

- README.md
- docs/（readthedocs）
- CONTRIBUTING.md
- examples/

## 课题关联

- C002肽毒性（分子/肽毒性与活性预测核心引擎）
- C003多端点（multi_task 教程与多任务损失原生支持）
- C013基线新颖性（社区标准强基线模型）
- C008基准校准（自带数据划分协议与测试）
- C010校准弃权（uncertainty 模块可支撑基于不确定性的弃权）
- L3肽性质（图神经网络性质预测）

## 与论文/课题的组合方式

- 与 DOI 10.1038/s41586-023-06887-8 组合：用 Chemprop 集成 + interpret 子结构解释复现 MRSA 选择性抗生素发现流程；在课题组合中作为多端点活性/毒性预测基线，其 uncertainty 估计与规范 splitting 协议可直接服务 C008/C010 的校准与弃权研究。
