# cedergrouphub/chgnet

- **仓库：** [https://github.com/cedergrouphub/chgnet](https://github.com/cedergrouphub/chgnet)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1038/s42256-023-00716-3
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** BSD-3-Clause (Modified BSD)
- **语言：** Python
- **复用度：** high —— pip可安装、预训练权重内置、推理/微调API清晰、有Colab示例notebook和完整测试套件，作为'预训练通用模型+微调'的软件工程范式可直接借用；但领域为无机晶体材料，与肽/蛋白课题族领域错配。
- **能力：** inference、training_pipeline、data_loader、benchmark、visualization

## 仓库摘要

CHGNet：在Materials Project 146k化合物/150万结构上预训练的电荷感知通用晶体图神经网络势（universal NNP），以近DFT精度预测能量/力/应力/磁矩，支持结构弛豫与分子动力学。官方PyPI包，工程质量高。

## 入口脚本

- chgnet/model/model.py（CHGNet.load() 加载预训练模型、predict_structure推理）
- chgnet/model/dynamics.py（结构弛豫/MD）
- chgnet/trainer/trainer.py（训练/微调Trainer）
- examples/run_md.py
- examples/make_graphs.py

## 数据加载

- chgnet/data/dataset.py（StructureData/GraphData等数据集类）
- chgnet/graph/converter.py（晶体->图转换）
- examples/QueryMPtrj.md（MPtrj数据集获取说明）

## 模型权重

- chgnet/pretrained/0.2.0、0.3.0、r2scan（三个预训练checkpoint随包分发，CHGNet.load()按名称加载）

## 评测基准

- tests/（test_model/test_trainer/test_relaxation/test_md等完整单元测试）
- README引用Matbench Discovery外部基准

## 文档

- README.md
- examples/basics.ipynb
- examples/fine_tuning.ipynb
- examples/dispersion.ipynb
- examples/crystaltoolkit_relax_viewer.ipynb
- citation.cff

## 课题关联

- 与肽/蛋白课题族领域错配（材料科学NNP）；间接参考：C008基准校准（Matbench Discovery外部基准评测实践）、L2蛋白语言模型（大规模预训练+迁移学习范式类比）

## 与论文/课题的组合方式

- 配论文10.1038/s42256-023-00716-3复现晶体性质预测/弛豫/MD；对本课题组的可复用点主要是工程范式：预训练权重随包分发+版本化load()、Trainer/数据集抽象、CI测试与Colab教程，可作为C008基准校准与L2/L3课题搭建可复现模型发布的模板。
