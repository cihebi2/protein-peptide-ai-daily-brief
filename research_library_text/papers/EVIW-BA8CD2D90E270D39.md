# MuToN Quantifies Binding Affinity Changes upon Protein Mutations by Geometric Deep Learning

- **论文 ID：** `EVIW-BA8CD2D90E270D39`
- **期刊 / 来源：** Adv Sci (Weinh)
- **发表时间：** 2024 Jul 12
- **DOI：** [10.1002/advs.202402918](https://doi.org/10.1002/advs.202402918)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `图与几何学习`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 MuToN，一个 geometric deep learning 框架，用结构编码、界面编码和界面差分解码三段式地预测突变前后复合物的结合亲和力变化，并在 SKEMPI v2.0 与 SARS-CoV-2 RBD/ACE2 场景中展示性能。

## 创新边界

`它的创新主要在 mutation-induced interface change 的几何建模与信息传播，不是直接生成或优化新的蛋白候选，因此更接近可用于设计的性质预测工作。`。这不是全球首创性检索或独立复现结论。

## 研究问题

预测蛋白质点突变，尤其是单点与多点突变，如何改变 protein-protein binding affinity（ΔΔG），并尽量捕捉远离界面位点引起的 allosteric 影响。

## 方法

- 从野生型复合物和计算突变结构构建几何图，通过几何注意力提取局部界面及全局变构特征，回归ΔΔG。

## 数据与基准

- 以SKEMPI v2.0为主要训练/评估集，并用S4169、S1131、M1707等子集比较。

## 比较基线

- 进化保守性方法、传统特征回归、结构/几何深度学习ΔΔG模型。

## 结果证据

- 论文报告多数据集上超过SOTA并可快速做大规模突变扫描；这些是计算ΔΔG预测。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 模型假设突变仅导致中等结构变化，剧烈多突变及远离界面的扰动会降低准确性。

## 仍未知

- 补充信息中的 Algorithm S1/S2、Tables S7-S9 和 Note S2 未在当前冻结页中完整展开。
- 论文声明代码开源，但未提供可直接核验的仓库链接。
- 多位点突变场景下 mutant structure 的生成与筛选误差对性能的真实影响仍不完全清楚。

## Pi 结构化证据摘录

- **baseline：** 作者将 mCSM-PPI2、MutaBind2、SAAMBE-SEQ、TopNetTree、GeoPPI 等既有突变亲和力预测方法作为主要对比对象。
  - 证据：[doi:10.1002/advs.202402918, p.1]；[doi:10.1002/advs.202402918, p.5]
- **baseline：** 在细粒度消融中，作者还比较了仅 amino acid type、仅 PLM feature，以及 graph CNN、graph attention 与 geometric attention。
  - 证据：[doi:10.1002/advs.202402918, p.3]；[doi:10.1002/advs.202402918, p.4]
- **baseline：** 在多突变比较里，作者将 GeoPPI、Discovery Studio 与 FoldX 作为对照。
  - 证据：[doi:10.1002/advs.202402918, p.5]；[doi:10.1002/advs.202402918, p.10]
- **baseline：** 在 SARS-CoV-2 单突变景观上，作者把 MuToN-SE 与 AlphaMissense、EVE、Tranception、GEMME、MSA Transformer、ESM1v 等序列模型作比较。
  - 证据：[doi:10.1002/advs.202402918, p.6]；[doi:10.1002/advs.202402918, p.8]
- **data：** 主数据集为 SKEMPI v2.0；作者报告其含 7,086 条记录，排除不同蛋白中多重突变后，剩余 5,091 条记录用于训练与评估。
  - 证据：[doi:10.1002/advs.202402918, p.8]
- **data：** 外部对比基准包括 S4169、S1131 与 M1707，这些子集来自既有研究并用于与 SOTA 方法比较。
  - 证据：[doi:10.1002/advs.202402918, p.4]；[doi:10.1002/advs.202402918, p.10]
- **data：** SARS-CoV-2 RBD/ACE2 的 ΔΔG 实验值来自 Barton et al. 的 SPR 测量，另有 DMS 结果用于验证全局突变景观。
  - 证据：[doi:10.1002/advs.202402918, p.8]；[doi:10.1002/advs.202402918, p.6]；[doi:10.1002/advs.202402918, p.10]
- **declared_resources：** 作者声明数据和代码已开源；数据可在 Zenodo 的 10.5281/zenodo.10445252 获取，但冻结页未给出可核验的代码仓库 URL。
  - 证据：[doi:10.1002/advs.202402918, p.8]；[doi:10.1002/advs.202402918, p.10]
- **declared_resources：** 突变结构生成/比较使用了 Modeller、FoldX 与 ESMFold，wild-type 结构来自 PDB。
  - 证据：[doi:10.1002/advs.202402918, p.8]；[doi:10.1002/advs.202402918, p.9]
- **limitations：** 作者明确指出，过多或过于剧烈的多位点突变会挑战预测精度，因为模型默认结构变化相对温和。
  - 证据：[doi:10.1002/advs.202402918, p.3]
- **limitations：** MuToN 依赖精确的 mutant structure；而多位点突变时结构计算与候选结构选择都比较困难。
  - 证据：[doi:10.1002/advs.202402918, p.7]；[doi:10.1002/advs.202402918, p.9]
- **limitations：** 作者也承认 DMS 的 binding affinity 读数存在 biophysical ambiguity，因此相关性可能受 stability 等因素混杂。
  - 证据：[doi:10.1002/advs.202402918, p.6]
- **method：** MuToN-SE 将 wild-type receptor、mutant receptor 和 ligand 表示为 residue-level graph，并结合 amino acid type 与 PLM embedding 进行几何 transformer 消息传递。
  - 证据：[doi:10.1002/advs.202402918, p.3]；[doi:10.1002/advs.202402918, p.9]
- **method：** MuToN-IE 以 geometric attention 从 receptor 聚合到 ligand，分别编码 wild-type 与 mutant complex 的 interface，再通过 global pooling 得到 interface descriptor。
  - 证据：[doi:10.1002/advs.202402918, p.2]；[doi:10.1002/advs.202402918, p.3]；[doi:10.1002/advs.202402918, p.9]
- **method：** MuToN-IDD 通过无 bias、无非线性激活的全连接层，将 Iw 与 Im 的差分映射为 ΔΔG，并显式保持 antisymmetry。
  - 证据：[doi:10.1002/advs.202402918, p.2]；[doi:10.1002/advs.202402918, p.9]
- **method：** 训练与评估采用 mutation-level 与 complex-level 两种切分，并使用 tenfold cross-validation 来检验泛化。
  - 证据：[doi:10.1002/advs.202402918, p.4]；[doi:10.1002/advs.202402918, p.9]
- **results：** 在 SKEMPI v2.0 的 mutation-level 切分上，MuToN 达到 RMSE 1.03、PCC 0.86；对未见 reverse mutations 的 PCC 也达到 0.89。
  - 证据：[doi:10.1002/advs.202402918, p.3]
- **results：** 在二分类任务中，MuToN 对直接突变的 PCC 为 0.83，加入 reverse mutations 后提升到 0.88。
  - 证据：[doi:10.1002/advs.202402918, p.3]
- **results：** 在 S4169 上，MuToN 的 mutation-level PCC 比次优方法高约 1.3%，complex-level PCC 则高约 13.4%。
  - 证据：[doi:10.1002/advs.202402918, p.5]
- **results：** 在 S1131 上，MuToN 的 complex-level PCC 为 0.7，较 GeoPPI 约高 29%。
  - 证据：[doi:10.1002/advs.202402918, p.5]
- **results：** 在 M1707 上，MuToN 相比最佳既有方法的 PCC 约高 4.2%。
  - 证据：[doi:10.1002/advs.202402918, p.5]
- **results：** 在 SARS-CoV-2 RBD 与 ACE2 的 10 个变体案例中，MuToN 的趋势预测 PCC 达到 0.991。
  - 证据：[doi:10.1002/advs.202402918, p.5]；[doi:10.1002/advs.202402918, p.7]
- **results：** MuToN-SE 对 DMS 约束景观的 Spearman correlation 达到 0.62；而以 SKEMPI 预训练的 MuToN 对 DMS 的相关性仅为 0.18。
  - 证据：[doi:10.1002/advs.202402918, p.6]；[doi:10.1002/advs.202402918, p.8]
- **results：** 分区分析显示 core region 的 PCC 最高可到 0.879，而更远离界面的区域 PCC 下降到约 0.397–0.797。
  - 证据：[doi:10.1002/advs.202402918, p.5]

## 页码证据

- [doi:10.1002/advs.202402918, p.1]
- [doi:10.1002/advs.202402918, p.3]
- [doi:10.1002/advs.202402918, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
