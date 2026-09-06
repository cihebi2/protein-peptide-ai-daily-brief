# PatchProt: hydrophobic patch prediction using protein foundation models

- **论文 ID：** `EVIW-489DE22C3AA92EB0`
- **期刊 / 来源：** Bioinform Adv
- **发表时间：** 2024 Oct 14
- **DOI：** [10.1093/bioadv/vbae154](https://doi.org/10.1093/bioadv/vbae154)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者声称提出 PatchProt：一个基于 ESM-2、LoRA 和多任务学习的序列模型，能够同时做 residue-level 与 protein-level 的 (L)HP 预测，并在 secondary structure 等基础任务上超过既有方法；同时他们强调这是首个可在 residue level 预测 hydrophobic patch 的模型。

## 创新边界

`创新主要在 foundation model 微调与 local/global 多任务框架，不在新的 wet-lab 发现或新的 hydrophobic patch 定义；LHP 标签仍来自现有结构工具 MolPatch，基准也主要是既有 PDB/CASP/CB513/TS115 数据。`。这不是全球首创性检索或独立复现结论。

## 研究问题

从氨基酸序列直接预测蛋白表面的暴露疏水斑块非常困难，但这类斑块与蛋白-蛋白/蛋白-配体相互作用以及聚集相关疾病都密切相关。作者要解决的是在不依赖耗时 MSA 的前提下，同时预测局部与全局蛋白性质，尤其是 hydrophobic patch。

## 方法

- ESM-2 PEFT，残基层surface hydrophobicity与蛋白级solubility/expression等任务联合训练。

## 数据与基准

- 结构派生疏水patch标签和补充表达/全局性质数据。

## 比较基线

- 单任务ESM/传统表面计算与不同任务组合。

## 结果证据

- 论文报告多任务优于单任务并缓解稀疏数据；为计算表面性质预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 大PLM仍耗内存，多任务权重难平衡；标签依赖结构计算，不能替代实验聚集/溶解度。

## 仍未知

- LoRA 的具体 rank、优化超参数与训练细节在正文里不够完整，难以独立复现全部设置。
- 模型在非 PDB、非实验结构来源数据上的泛化能力仍不清楚。
- 局部 hydrophobic patch 预测是否能稳定迁移到真实设计流程，尤其是新蛋白序列，仍未被直接验证。

## Pi 结构化证据摘录

- **baseline：** SSE 对照包括 NetSurfP-2、NetSurfP-3、ESM-2 frozen head，以及同一框架下的 LoRA 版本，使用相同测试集和相近指标比较。
  - 证据：[doi:10.1093/bioadv/vbae154, p.6]
- **baseline：** LHP 对照包括作者先前的 TFM、31 特征 XGBoost 回归、基于 NetSurfP-2 预测值的 NBM 随机森林，以及相关的 global feature model。
  - 证据：[doi:10.1093/bioadv/vbae154, p.5]；[doi:10.1093/bioadv/vbae154, p.7]
- **baseline：** 作者还做了内部消融：仅 (L)HP、SSE+(L)HP、以及 SSE+(L)HP+SP+NX，借此比较辅助任务是否带来增益。
  - 证据：[doi:10.1093/bioadv/vbae154, p.7]
- **data：** 基础基准沿用 NetSurfP-2/3 的训练集与测试集，训练集为 10,848 条来自 PDB 的蛋白，测试集包括 CASP12、CB513 和 TS115。
  - 证据：[doi:10.1093/bioadv/vbae154, p.2]；[doi:10.1093/bioadv/vbae154, p.6]
- **data：** LHP 标注来自 MolPatch，扩展后共有 10,594 条 chain；用于全局 LHP 评估的独立单体蛋白测试集最终为 346 条。
  - 证据：[doi:10.1093/bioadv/vbae154, p.2]；[doi:10.1093/bioadv/vbae154, p.5]
- **data：** 作者还扩展了归一化表达与物种分类数据：expression 来自 Human Protein Atlas，得到 618 条链；species 则使用 10 个最常见物种标签。
  - 证据：[doi:10.1093/bioadv/vbae154, p.3]
- **declared_resources：** 论文明确给出公开代码与数据入口：https://github.com/Deagogishvili/chapter-multi-task 。
  - 证据：[doi:10.1093/bioadv/vbae154, p.9]
- **declared_resources：** 作者还致谢使用了 Vrije Universiteit Amsterdam 的 BAZIS HPC cluster 计算资源。
  - 证据：[doi:10.1093/bioadv/vbae154, p.8]
- **limitations：** global LHP 通过求和得到，作者自己指出这可能引入 sequence-length 依赖，因此建议未来尝试用均值替代求和。
  - 证据：[doi:10.1093/bioadv/vbae154, p.8]
- **limitations：** 辅助任务并非总是对 residue-level (L)HP 有利，文中也承认某些测试集上局部指标没有稳定提升。
  - 证据：[doi:10.1093/bioadv/vbae154, p.7]；[doi:10.1093/bioadv/vbae154, p.8]
- **limitations：** LHP 标签依赖实验结构和 MolPatch；作者还提醒，在 AlphaFold 预测结构上，disordered 或 coiled 区域可能导致 LHP 面积被高估。
  - 证据：[doi:10.1093/bioadv/vbae154, p.8]
- **limitations：** 大模型的显存开销仍是限制，作者把 pruning、distillation 与 quantization 视为后续缓解方向。
  - 证据：[doi:10.1093/bioadv/vbae154, p.8]
- **method：** 模型以 ESM-2 产生蛋白序列表征，并接入类似 NetSurfP-3 的 CNN + 双向 LSTM 解码头，同时输出 residue-level 与 protein-level 预测。
  - 证据：[doi:10.1093/bioadv/vbae154, p.3]；[doi:10.1093/bioadv/vbae154, p.5]
- **method：** 全局任务不是单独建模，而是把每个残基对该任务的输出求和，形成单个蛋白的 global prediction，并保留一定可解释性。
  - 证据：[doi:10.1093/bioadv/vbae154, p.4]
- **method：** 训练使用 uncertainty-based multitask loss，对回归与分类任务分别采用 MSE 或 cross-entropy，并对 batch 内缺失注释跳过对应损失。
  - 证据：[doi:10.1093/bioadv/vbae154, p.4]
- **method：** 作者用 LoRA 做参数高效微调，把低秩更新加到 transformer 的线性层、Q/K/V 投影和 feed-forward 层上；长序列则分段处理，并配合 gradient checkpointing 与 accumulation。
  - 证据：[doi:10.1093/bioadv/vbae154, p.5]
- **results：** 在 CASP12、CB513、TS115 上，PatchProt(All)+LoRA 在多数 secondary structure 指标上优于 NetSurfP-2、NetSurfP-3 以及冻结的 ESM-2 基线。
  - 证据：[doi:10.1093/bioadv/vbae154, p.6]
- **results：** 全局 LHP 预测明显优于既有回归基线，文中报告 global level 的 R2 约为 0.54，较此前仅用基础特征的 0.12 和加入 THSA/RHSA 后的 0.43 更好。
  - 证据：[doi:10.1093/bioadv/vbae154, p.5]；[doi:10.1093/bioadv/vbae154, p.7]
- **results：** 加入 SSE 相关任务后，(L)HP 的整体表现提升；再加入 species 与 expression 后，global LHP 继续改善，但 residue-level 的收益并不稳定。
  - 证据：[doi:10.1093/bioadv/vbae154, p.7]；[doi:10.1093/bioadv/vbae154, p.8]

## 页码证据

- [doi:10.1093/bioadv/vbae154, p.1]
- [doi:10.1093/bioadv/vbae154, p.2]
- [doi:10.1093/bioadv/vbae154, p.3]
- [doi:10.1093/bioadv/vbae154, p.8]
- [doi:10.1093/bioadv/vbae154, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
