# Protein-ligand binding affinity prediction using multi-instance learning with docking structures

- **论文 ID：** `EVIW-5C0DA702F696CD1D`
- **期刊 / 来源：** Front Pharmacol
- **发表时间：** 2025 Jan 3
- **DOI：** [10.3389/fphar.2024.1518875](https://doi.org/10.3389/fphar.2024.1518875)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出一个基于 multi-instance learning (MIL) 的结构推断框架，把每个复合体的多个 docking poses 作为一个 bag，用 attention pooling 聚合来自 SGCNN 或 EGNN 的 pose 表征，从而在不依赖 co-crystal structures 时预测 binding affinity。

## 创新边界

`主要新意在多 pose 的 MIL 聚合与 pose-wise attention，而不是新的 docking 生成流程或 wet-lab 设计。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在 co-crystal structures 稀缺且 docking poses 含噪的情况下，如何仅依靠多个 docking poses 稳健预测 protein-ligand binding affinity。

## 方法

- 每个pose编码为3D原子图，多pose经共享编码和注意力池化汇总，再回归复合物亲和力。

## 数据与基准

- 使用PDBbind及SARS-CoV-2主蛋白酶化合物数据，并以多套对接pose而非共晶单结构训练/测试。

## 比较基线

- 共晶结构模型、最佳对接pose模型、单实例3D图网络和对接评分。

## 结果证据

- 论文报告多实例聚合在多个数据集改善亲和力预测，并降低错误单pose影响；结果仍依赖计算对接结构。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 论文未公开独立代码/数据包，数据可用性仅指正文和补充；多pose质量仍受对接程序和口袋定义限制。

## 仍未知

- 正文未提供公开代码仓库或权重下载链接。
- 外部复现时 docking 参数与 pose 质量可能显著影响结果。

## Pi 结构化证据摘录

- **baseline：** 对照方法包括 HACNET、SGCNN、EGNN 和 Fusion，并同时比较 Top 与 Avg 两种 pose 聚合方式；其中 HACNET 用 PDBbind 2016 训练，其余晶体基线主要用 PDBbind 2020 训练。[doi:10.3389/fphar.2024.1518875, p.6]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.6]；[doi:10.3389/fphar.2024.1518875, p.7]
- **baseline：** 作者还比较了 crystal-only、crystal+docking 和 docking-only 设置，用来验证 docking pose 训练是否能弥补晶体结构稀缺。[doi:10.3389/fphar.2024.1518875, p.6]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.6]；[doi:10.3389/fphar.2024.1518875, p.7]
- **data：** PDBbind 2020 general/refined 用于训练，CASF-2016 core set 用于评估；每个 ligand 最多生成 10 个 docking poses，并用 ODDT 计算 pose 与 crystal ligand 的 RMSD。[doi:10.3389/fphar.2024.1518875, p.4]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.4]；[doi:10.3389/fphar.2024.1518875, p.5]
- **data：** Mpro 数据集来自 POSTERA 和 GOSTAR，receptor 为 6LU7，没有 complex crystal structures；作者采用 random split 与 scaffold split，训练/测试规模为 2,135/1,281。[doi:10.3389/fphar.2024.1518875, p.4]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.4]；[doi:10.3389/fphar.2024.1518875, p.5]
- **declared_resources：** 实现使用 PyTorch 和 PyTorch Geometric，在 4 张 NVIDIA Titan Xp GPU 上训练；pose 生成与处理依赖 AutoDock VINA、ConveyorLC、Open Babel、tfbio 和 ODDT，训练时还使用 RMSprop 与 multi-step learning-rate scheduler。[doi:10.3389/fphar.2024.1518875, p.3]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.3]；[doi:10.3389/fphar.2024.1518875, p.6]；[doi:10.3389/fphar.2024.1518875, p.11]
- **limitations：** 作者明确指出 Mpro 数据集表现较弱，可能因为 docking poses 更不准确；在没有 co-crystal structures 时，pose 质量本身也更难直接评估。[doi:10.3389/fphar.2024.1518875, p.8]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.8]；[doi:10.3389/fphar.2024.1518875, p.9]
- **limitations：** bag size K 的选择存在权衡，过大可能增加复杂度与过拟合风险，且最佳范围依赖 compound type、pose 数量和模型结构。[doi:10.3389/fphar.2024.1518875, p.10]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.10]
- **limitations：** multi-head attention 没有稳定优于单头全局 attention，说明该架构替换并未带来一致性能增益。[doi:10.3389/fphar.2024.1518875, p.11]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.11]
- **method：** 将每个 protein-ligand 复合体的多条 docking poses 视为一个 bag，并把 binding affinity 回归成 bag-level 的单个连续标签；核心是对 pose 顺序不敏感的 MIL 设定。[doi:10.3389/fphar.2024.1518875, p.2]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.2]；[doi:10.3389/fphar.2024.1518875, p.3]
- **method：** 每个 pose 先经由 SGCNN 或 EGNN 编码为低维 embedding，再送入 attention network 做加权池化；输入特征采用 Pafnucy 风格原子特征，包含 3D 坐标与 19 维原子描述。[doi:10.3389/fphar.2024.1518875, p.3]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.3]；[doi:10.3389/fphar.2024.1518875, p.4]
- **method：** 作者还说明 attention 层后接全连接层，并试验了 multi-head attention，但未观察到明显改进。[doi:10.3389/fphar.2024.1518875, p.4]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.4]；[doi:10.3389/fphar.2024.1518875, p.11]
- **results：** 在 PDBbind CASF-2016 上，EGNN-MIL 达到 RMSE 0.955、MAE 0.736、r2 0.808、Pearson 0.904、Spearman 0.899，优于 top/avg 聚合基线。[doi:10.3389/fphar.2024.1518875, p.7]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.7]
- **results：** 在仅用 docking poses 训练的 PDBbind 实验中，EGNN-MIL 仍优于 SGCNN-MIL 与 top/avg，RMSE 为 0.967、MAE 为 0.748。[doi:10.3389/fphar.2024.1518875, p.7]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.7]
- **results：** 在 SARS-CoV-2 Mpro 上，random split 下 EGNN-MIL 的 RMSE 为 0.763；scaffold split 下 EGNN-MIL 的 RMSE 为 0.846、r2 为 0.366，均优于对应基线。[doi:10.3389/fphar.2024.1518875, p.8]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.8]
- **results：** 消融结果显示，增加每个 bag 中的 pose 数通常会提升性能，5–10 个 pose 更有效；multi-head attention 对 EGNN 并未带来稳定收益。[doi:10.3389/fphar.2024.1518875, p.10]
  - 证据：[doi:10.3389/fphar.2024.1518875, p.10]；[doi:10.3389/fphar.2024.1518875, p.11]

## 页码证据

- [doi:10.3389/fphar.2024.1518875, p.11]
- [doi:10.3389/fphar.2024.1518875, p.1]
- [doi:10.3389/fphar.2024.1518875, p.3]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
