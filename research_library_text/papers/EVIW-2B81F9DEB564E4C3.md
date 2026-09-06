# ZeroGEN: leveraging language models for zero-shot ligand design from protein sequences

- **论文 ID：** `EVIW-2B81F9DEB564E4C3`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2025 Oct 15
- **DOI：** [10.1093/bioinformatics/btaf572](https://doi.org/10.1093/bioinformatics/btaf572)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出 ZeroGEN：一个面向蛋白序列的零样本配体设计框架，把蛋白-配体对比学习、交叉注意力交互预测、蛋白引导的自回归解码，以及基于自蒸馏的伪数据增强整合到同一管线中，以提升未知靶点的配体生成质量。

## 创新边界

`主要新意在于把序列级生成、对比学习、交叉注意力和自蒸馏式伪标签增强组合成统一零样本流程；证据支持的是算法整合与 in silico 改进，不支持全球首创或湿实验验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在缺少已知配体、甚至缺乏结构信息的零样本场景下，仅凭蛋白序列生成可结合且具备药物样式的候选配体。

## 方法

- 编码蛋白序列并与分子语言模型交叉注意；先生成并筛选伪配体数据，再对目标生成模块微调。

## 数据与基准

- 在按靶点划分的配体数据上模拟未见蛋白，并以AutoDock Vina、药物样性和生成质量指标评价。

## 比较基线

- 序列条件生成模型、结构/口袋条件生成方法及不同对比/伪标签组件。

## 结果证据

- 论文声称未见靶点上生成配体具有较好对接分数和药物样性；无合成、结合或活性实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 生物特异性仍不足，作者提出未来加入口袋mask和结构预训练；伪数据可能强化评分器偏差。

## 仍未知

- 仓库代码、许可证和运行结果未在本次纸面审查中核验。
- 训练集完整规模、去重策略与负样本构造细节未在正文中完整展开。
- 生成分子的实际体外/体内活性尚未被实验确认。

## Pi 结构化证据摘录

- **baseline：** Prot2Drug 被用作把蛋白序列映射到分子序列的 translation baseline。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.5]
- **baseline：** DeepTarget 被用作基于 conditional GAN 的序列配体生成 baseline。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.5]
- **baseline：** Randomization 作为随机分子下限对照，用于判断模型是否优于无条件采样。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.5]
- **baseline：** ZeroGEN-Vanilla w/o ss 是去除相似蛋白序列的消融，用来检验 sequence similarity 在训练中的作用。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.6]；[doi:10.1093/bioinformatics/btaf572, p.7]
- **data：** 零样本评估选择了 DRD2、AKT1、GSK3b、ROCK1 四个靶点，并从训练集中移除了这些靶点相关 ligands，序列来自 PDB 结构 6cm4、3o96、3l1s、4yve。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.5]
- **data：** 阈值构建时，每个靶点随机采样 10000 个 ChEMBL inactive molecules，并与 known active molecules 的 PLCL similarity 分布对比。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.7]
- **data：** Docking 评估对每个靶点取 100 个有效且唯一的 generated molecules，用 AutoDock Vina 计算 binding score；相似性与新颖性评估则基于 10000 个有效生成分子。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.5]；[doi:10.1093/bioinformatics/btaf572, p.7]
- **data：** 作者还用 ADMETLab 2.0 对 1000 个生成分子检查 ADMET 特性，以验证 drug-like profile。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.9]
- **declared_resources：** 论文公开声明 source code 和 data 可在 GitHub 的 ZeroGEN 仓库获取。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.10]
- **declared_resources：** Docking 评估资源明确使用 AutoDock Vina。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.5]
- **declared_resources：** ADMET 评估资源明确使用 ADMETLab 2.0。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.9]
- **declared_resources：** 零样本靶点来自 PDB 结构 6cm4、3o96、3l1s、4yve，背景分子与新颖性检查依赖 ChEMBL。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.5]；[doi:10.1093/bioinformatics/btaf572, p.7]
- **limitations：** 论文的验证主要停留在 docking、fingerprint similarity、feature similarity 和 ADMET 预测层面，没有给出湿实验或真实结合实验来确认生物活性。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.5]；[doi:10.1093/bioinformatics/btaf572, p.7]；[doi:10.1093/bioinformatics/btaf572, p.9]
- **limitations：** 作者明确表示 pseudo-ligands 只是模型内部的 confidence proxy，并不主张其具备真实生物活性，说明自蒸馏标签仍有噪声风险。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.7]
- **limitations：** 结论部分也承认生物特异性与效率仍有提升空间，建议未来加入 pocket-aware masking、residue-weighted contrastive learning 和 structure-informed pre-training。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.9]
- **method：** 模型采用分离的 protein encoder 与 ligand encoder，并在 protein-based ligand decoder 中用 cross-attention 条件生成配体序列。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.2]；[doi:10.1093/bioinformatics/btaf572, p.3]
- **method：** PLCL 通过 momentum queue、可学习温度和对比损失，把蛋白与配体投到共享 latent space，拉近正对并拉远负对。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.4]
- **method：** PLIP 将蛋白-grounded molecule encoder 输出送入二分类头，以预测蛋白-配体是否存在相互作用。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.4]
- **method：** PBLD 以自回归方式生成 ligand tokens，并用 cross-entropy 优化给定蛋白条件下的分子序列概率。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.3]；[doi:10.1093/bioinformatics/btaf572, p.4]
- **method：** 自蒸馏增强先用 PLCL similarity 和 PLIP 结果筛选生成分子，再以 inactive 分布的 95th percentile 作为阈值，从每个靶点保留 1000 个 pseudo pairs 继续微调。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.4]；[doi:10.1093/bioinformatics/btaf572, p.7]
- **results：** ZeroGEN-Vanilla 相比 Randomization、Prot2Drug、DeepTarget 在四个靶点上给出更好的 docking 分布，整体平均分向更负方向移动。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.5]
- **results：** 移除相似序列后（ZeroGEN-Vanilla w/o ss）docking 变差，说明模型会从训练集中的相似蛋白序列中借力学习。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.6]；[doi:10.1093/bioinformatics/btaf572, p.7]
- **results：** 在 AKT1 case 中，ZeroGEN-Vanilla 生成了 5 个与已知 inhibitor 的 Tanimoto > 0.5 分子，且有 8 个分子呈现相似 scaffold。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.7]
- **results：** Table 1 显示自蒸馏后高相似分子覆盖面扩大，例如 AKT1 的 GenMol >0.5 Sim 从 188 提升到 613，GSK3B 从 301 提升到 663，ROCK1 则从 1 持平到 1，但 ActMol identified 进一步增加到 2。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.8]
- **results：** 注意力热图把高分残基定位到已知 binding pocket 附近，例如 AKT1 的 SER-205/LYS-268/TRP-80、GSK3b 的 ASP-200/VAL-135/ASP-133、ROCK1 的 MET-156/LYS-105/PHE-85、DRD2 的 ASP-114/TRP-386/PHE-390。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.8]；[doi:10.1093/bioinformatics/btaf572, p.9]
- **results：** 作者报告 1000 个生成分子在 ADMETLab 2.0 下满足 drug-like benchmarks。
  - 证据：[doi:10.1093/bioinformatics/btaf572, p.9]

## 页码证据

- [doi:10.1093/bioinformatics/btaf572, p.1]
- [doi:10.1093/bioinformatics/btaf572, p.2]
- [doi:10.1093/bioinformatics/btaf572, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
