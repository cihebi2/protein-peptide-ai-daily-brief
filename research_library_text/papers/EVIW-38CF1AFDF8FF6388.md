# Machine learning-aided design and screening of an emergent protein function in synthetic cells

- **论文 ID：** `EVIW-38CF1AFDF8FF6388`
- **期刊 / 来源：** Nat Commun
- **发表时间：** 2024 Mar 5
- **DOI：** [10.1038/s41467-024-46203-0](https://doi.org/10.1038/s41467-024-46203-0)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出一个面向 emergent protein function 的 i3 流程：用 MSA-VAE 生成 MinE 变体，再以结构基础的 divide-and-conquer 评分、PURE 无细胞表达和脂滴 synthetic cells 体外筛选，最终在 ΔminDE E. coli 中找到可完全补偿 wild-type MinE 的 synMinEv25。

## 创新边界

`创新边界主要在 MinE/MinDE 这一具体系统的筛选与验证框架，而不是通用 de novo 生成模型本身。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何把机器学习生成的 MinE 变体，经过可解释的计算筛选与体外/体内筛选，找到能够在细胞内重建 MinDE 空间振荡并替代天然基因的人工同源蛋白。

## 方法

- sequence/design model提出候选，droplet/synthetic-cell高通量功能测量反馈模型。

## 数据与基准

- 设计蛋白库与synthetic cell时空表型实验。

## 比较基线

- 随机/未引导设计和初始模型。

## 结果证据

- 论文报告实验命中和迭代改善；仅按其明确无细胞实验记录。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- synthetic cell不等同活细胞，功能与规模有限。

## 仍未知

- 跨其他 emergent function 的泛化效果尚未证明。
- 体外/体内筛选结果主要基于单一 MinE 体系，缺少独立外部队列复现。
- 全局 novelty 未被独立 prior-art 证据验证。

## Pi 结构化证据摘录

- **baseline：** 作者将自己的评分与 sequence identity/closest homolog 和 HMM profile-based scoring 做比较，并报告改进后的评分优于这两类传统序列基线。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.6]
- **baseline：** 实验上，作者把传统的蛋白纯化流程作为对照，指出 PURE cell-free expression 比标准纯化更适合高通量预筛。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.4]；[doi:10.1038/s41467-024-46203-0, p.6]；[doi:10.1038/s41467-024-46203-0, p.11]
- **baseline：** 体内对照包括 -MinDE、-MinE 和 wt 条件，用于区分 minicell、filamentous 与 normal phenotype。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.6]；[doi:10.1038/s41467-024-46203-0, p.11]
- **data：** 训练数据来自含 IPR005527 的序列集合，初始 8,496 条去重后得到 5,958 条、186 列的 MSA，且没有单独保留 test split。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.8]
- **data：** 模型一次生成 4,000 条候选序列，经 60% identity 过滤后剩下 167 条，再选出 48 条进入体外筛选。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.2]；[doi:10.1038/s41467-024-46203-0, p.3]；[doi:10.1038/s41467-024-46203-0, p.9]；[doi:10.1038/s41467-024-46203-0, p.10]
- **data：** 在 PURE 体系里，48 个变体中超过 80%（40 个）达到可检测表达，而脂滴重构中有 14 个出现典型 Min wave。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.5]
- **data：** 14 个体外阳性里，10 个来自高 in silico 分组、4 个来自低分组；进入体内后，7/10 高分变体产生振荡，而低分组只有 1 个产生振荡。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.6]
- **data：** synMinEv25 的序列与 wtMinE 的 identity/similarity 低于 50%/70%，但仍保持同源蛋白属性，并与最近自然同源物接近。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.7]
- **declared_resources：** 生成与评分工具包括 MSA-VAE、AlphaFold2 Multimer、ProteinSol Patches、ProteinSol、cd-hit、Clustal Omega 和 PyTorch。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.8]；[doi:10.1038/s41467-024-46203-0, p.9]；[doi:10.1038/s41467-024-46203-0, p.10]；[doi:10.1038/s41467-024-46203-0, p.12]
- **declared_resources：** 实验资源包括 E. coli PUREfrex 2.0 cell-free system、POPC/POPG lipid droplets、HL1 ΔminDE strain 以及 mGreenLantern-MinD 构建体。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.5]；[doi:10.1038/s41467-024-46203-0, p.10]；[doi:10.1038/s41467-024-46203-0, p.11]；[doi:10.1038/s41467-024-46203-0, p.12]
- **declared_resources：** 作者声明所有图表源数据已随文提供，>10 GB 的原始图像数据可向通讯作者索取，代码则公开在 GitHub。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.12]
- **limitations：** 作者明确说明该 divide-and-conquer pipeline 是为 MinE 的已知三项子功能定制的，若不重新定义子功能，难以直接泛化到其他 emergent functions。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.8]
- **limitations：** 事后分析显示 solubility 和 dimerization 这两个子分数并不能显著区分阳性与阴性，且单项 in silico 与 in vitro 特征之间的相关性总体并不强。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.6]；[doi:10.1038/s41467-024-46203-0, p.7]
- **limitations：** 成功样本数仍然有限：48 个候选中只有 14 个体外阳性、10 个高分体内候选中只有 7 个真正振荡，因此统计和泛化都仍受样本规模约束。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.5]；[doi:10.1038/s41467-024-46203-0, p.6]
- **limitations：** 方法实现还经历过 VAE loss 设定不当和 mode collapse 风险，这提示生成环节本身仍需要较强的人工调参。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.9]
- **method：** 作者先用 InterPro/Pfam 相关序列构建 MinE 的 MSA，并训练一个 16 维 latent 的 MSA-VAE 来生成 4000 个候选序列。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.8]；[doi:10.1038/s41467-024-46203-0, p.9]
- **method：** 对去冗余后的 167 个候选，作者用 AlphaFold2 Multimer 预测结构，再基于 PAE、N-terminal hydrophobicity 和 ProteinSol 估计 MinD 相互作用、二聚化、膜结合与可溶性，并汇总成 Function Score。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.3]；[doi:10.1038/s41467-024-46203-0, p.9]；[doi:10.1038/s41467-024-46203-0, p.10]
- **method：** 作者把高分和低分各 24 个候选送入 PURE 体系表达，并在 POPC/POPG 脂滴中与 MinD/ATP 共封装，以观察是否出现 Min waves。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.4]；[doi:10.1038/s41467-024-46203-0, p.5]；[doi:10.1038/s41467-024-46203-0, p.10]
- **method：** 体外阳性的 14 个变体随后被引入 ΔminDE HL1 E. coli，通过 GFP-tagged MinD 观察振荡和细胞形态，并进一步做蛋白纯化、SEC、ATPase assay 和 QCMD。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.5]；[doi:10.1038/s41467-024-46203-0, p.6]；[doi:10.1038/s41467-024-46203-0, p.11]；[doi:10.1038/s41467-024-46203-0, p.12]
- **method：** 作者在方法里承认最初的 VAE loss 设计不理想，KL 与 reconstruction 的权重失衡曾导致 mode collapse 风险，后来用 0.01 缩放 KL 进行修正。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.9]
- **results：** 初始 Function Score 能区分体外阳性与阴性（p=0.03, AUC=0.68），而改进后的 MinD interaction + N-terminal hydrophobicity 评分几乎完全区分两类样本（p=2e-7, AUC=0.92），并优于 sequence similarity 与 HMM scoring。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.6]
- **results：** synMinEv25 在体内恢复了接近 wt 级的生长、细胞尺寸分布和 Min 振荡，且在体外三项功能指标上最接近 wtMinE。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.6]；[doi:10.1038/s41467-024-46203-0, p.7]
- **results：** 作者声称 synMinEv25 是首个由 generative model 生成、并在活细胞中功能性替代天然基因的人工同源蛋白。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.6]
- **results：** 作者还观察到，体外筛选在 2 天内完成全部变体的快速预筛，而纯化流程仅能获得 60% 的高分候选，说明 cell-free 方案显著加速了筛选。
  - 证据：[doi:10.1038/s41467-024-46203-0, p.6]；[doi:10.1038/s41467-024-46203-0, p.10]；[doi:10.1038/s41467-024-46203-0, p.11]

## 页码证据

- [doi:10.1038/s41467-024-46203-0, p.1]
- [doi:10.1038/s41467-024-46203-0, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
