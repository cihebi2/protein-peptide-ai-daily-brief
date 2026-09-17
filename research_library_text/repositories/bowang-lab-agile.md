# bowang-lab/agile

- **仓库：** [https://github.com/bowang-lab/agile](https://github.com/bowang-lab/agile)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1038/s41467-024-50619-z
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python (PyTorch 1.12 + torch-geometric)
- **复用度：** high —— MIT许可，预训练权重与论文数据(微调集+候选库CSV)随仓库分发，config yaml驱动全流程，requirements锁定版本；但依赖较旧(torch1.12+cu113/pyg)且分子图非肽链表征，跨域复用需替换分子表示层
- **能力：** 分子图对比学习预训练(MolCLR迁移)、可电离脂质递送效力回归预测(多细胞系)、组合虚拟脂质库构建(A×B×C组分SMILES)、自建数据预训练/微调配置化训练管线、推理结果可视化与Ugi反应虚拟筛选

## 仓库摘要

AGILE（AI-Guided Ionizable Lipid Engineering）：面向 LNP 介导 mRNA 递送的可电离脂质迭代开发深度学习平台（Nature Communications 2024, Cui/Ma/Wang Lab @ UofT 官方代码）。核心为 MolCLR 预训练的分子图对比学习 GNN，先在 60k 组合虚拟脂质库上预训练，再按细胞系（HeLa、Raw）微调回归预测脂质递送效力，配合组合脂质库设计-合成-筛选闭环，将新脂质开发周期从数月/数年压缩至数周。含预训练权重、微调/候选库数据(data.zip)与 Ugi 三组分反应虚拟筛选 notebook。

## 入口脚本

- pretrain.py (config_pretrain.yaml 驱动)
- finetune.py (config_finetune.yaml 驱动)
- infer_vis.py (推理与可视化)
- ugi_3CR_agile_reaction_virtual.ipynb (Ugi三组分反应虚拟筛选示例)

## 数据加载

- dataset/dataset.py
- dataset/dataset_mix.py
- dataset/dataset_subgraph.py
- dataset/dataset_test.py
- data.zip (论文微调库+候选库，解压至./data)

## 模型权重

- ckpt/pretrained_agile_60k/ (60k虚拟脂质库预训练权重随仓库分发)
- MolCLR基础权重需从外部 github.com/yuyangw/MolCLR 下载放入./ckpt
- models/agile_pretrain.py
- models/agile_finetune.py
- utils/nt_xent.py (对比学习损失)

## 评测基准

- AGILE_smiles_with_value_group.csv (组合脂质库: A/B/C组分SMILES + expt_Hela/expt_Raw双细胞系实验效力标签)
- data.zip (论文微调集与候选筛选库)
- finetune产出模型经infer_vis.py在数据集上回测

## 文档

- README.md (安装/预训练/微调/推理全流程说明)
- figures/ (平台架构图)

## 课题关联

- X06
- L3
- C003
- C005

## 与论文/课题的组合方式

- X06优化：'虚拟组合库预筛+实验闭环迭代'的主动式优化范式可直接迁移到肽优化课题的候选生成-评估-更新循环设计
- L3肽性质：其SMILES+分子描述符双通道回归管线(get_desc_cols+pred_additional_feat_dim)可复用为肽性质预测的特征融合基线结构
- C003多端点：同一分子在HeLa/Raw两细胞系的效力标签天然构成多端点数据结构，可作为多端点建模的跨域参照
- C005表型：细胞系依赖的递送效力本质是细胞表型读出，可用于讨论模型跨细胞系泛化与条件化建模
