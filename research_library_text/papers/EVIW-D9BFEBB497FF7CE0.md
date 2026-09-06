# Screening of multi deep learning-based de novo molecular generation models and their application for specific target molecular generation

- **论文 ID：** `EVIW-D9BFEBB497FF7CE0`
- **期刊 / 来源：** Scientific Reports（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1038/s41598-025-86840-z](https://doi.org/10.1038/s41598-025-86840-z)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称提出了三种 GPT 改造版（GPT-RoPE、GPT-Deep、GPT-GEGLU）、一个基于完整 encoder-decoder 的条件生成模型 T5MolGe，以及对 Mamba 的系统比较；随后结合 transfer learning，在 EGFR TKI 目标上筛出并虚拟筛选候选分子。

## 创新边界

`创新主要体现在模型结构改造、条件生成框架与目标导向应用，不是新的 wet-lab chemistry 或新的生物学靶点发现。`。这不是全球首创性检索或独立复现结论。

## 研究问题

比较并改造多种基于 transformer 与 selective state space 的 de novo molecular generation 模型，评估它们在无条件生成、scaffold 条件生成与 transfer learning 场景下的表现，并将最合适的模型用于面向 L858R/T790M/C797S-mutant EGFR 的 TKI 候选分子生成。

## 方法

- 多生成器统一metrics、target scoring与筛选。

## 数据与基准

- 公开分子库/target cases。

## 比较基线

- 多个受测generators。

## 结果证据

- 论文报告模型差异/target candidates；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- metrics/reward/无实验。

## 仍未知

- GitHub 仓库是否包含可运行代码、完整数据与许可未在冻结证据中核验。
- pKd、dock 和筛选结果均为计算预测，缺少实验亲和力与生物活性验证。
- 候选分子的合成可行性、毒性与药代性质尚未被系统证明。

## Pi 结构化证据摘录

- **baseline：** 实验基线主要是 GPT、GPT-RoPE、GPT-Deep、GPT-GEGLU、Mamba 和 T5MolGe；条件任务中这些模型在同一设置下比较。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.7]；[doi:10.1038/s41598-025-86840-z, p.8]
- **baseline：** 引言还把 MolGPT、CharRNN、VAE、JT-VAE、AAE 和 LatentGAN 作为既有工作背景，但它们不是本研究复现实验的直接对照。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.1]
- **data：** 无条件和条件预训练使用 GuacaMol，它是 ChEMBL 24 的子集，约含 1.6 million molecules。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.5]
- **data：** 针对 EGFR TKI 目标，作者从 2,431,025 个 ChEMBL compounds 中筛出 171 个 '-tinib' 分子，并用 SMILES randomization 扩增到 1710 条序列。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.5]
- **data：** 最终筛得 7059 条 standard and nonrepeated SMILES，并对 EGFR L858R/T790M/C797S mutant（PDB 6LUD）做 DeepPurpose 亲和力预测与 Schrödinger Maestro docking。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.10]；[doi:10.1038/s41598-025-86840-z, p.5]
- **declared_resources：** 作者声明使用 PyTorch、Hugging Face、RDKit、DeepPurpose 和 Schrödinger Maestro 12.8；实验环境为 Linux ubuntu20.04、AMD EPYC 7642、80 GB memory 与 24 GB GPU。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.5]；[doi:10.1038/s41598-025-86840-z, p.10]
- **declared_resources：** 数据与代码声明已上传 GitHub，并附有 Supplementary Information。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.14]
- **limitations：** 作者明确承认仍需进一步做 efficacy、toxicity、pharmacodynamics 等实验，当前结果主要停留在计算筛选与虚拟对接层面。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.13]；[doi:10.1038/s41598-025-86840-z, p.10]；[doi:10.1038/s41598-025-86840-z, p.11]
- **limitations：** 目标特异数据集很小，只有 171 个 '-tinib' 分子，经 randomization 才扩到 1710 条 SMILES，数据稀缺仍是主要瓶颈。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.5]；[doi:10.1038/s41598-025-86840-z, p.10]
- **limitations：** 部分条件基线在某些 scaffold 上出现 similarity ratio = 0，说明 scaffold 约束并非对所有条件都稳健。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.8]
- **method：** 作者对 GPT 做了三处结构改造：RoPE、DeepNorm 和 GEGLU，并同时引入 Mamba 与基于 T5 的条件生成模型 T5MolGe 进行对比。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.2]；[doi:10.1038/s41598-025-86840-z, p.3]；[doi:10.1038/s41598-025-86840-z, p.4]
- **method：** T5MolGe 以 ChEMBL 提取的 molecular scaffold 作为条件输入，经 encoder 编码后由 masked self-attention decoder 逐步生成 SMILES，并以 maximum likelihood 作为输出目标。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.4]
- **method：** 训练与微调使用 PyTorch / Hugging Face，优化上采用 Adam、cross-entropy、10 epochs、lr warm-up/decay 与自动 gradient scaling。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.5]
- **results：** 无条件生成里，GPT-RoPE 的 validity 最高（0.980），而 Mamba 在 FCD 和 KL divergence 上最好，说明其生成分布更接近目标集。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.5]；[doi:10.1038/s41598-025-86840-z, p.7]
- **results：** 条件 scaffold 生成里，T5MolGe 在 validity（0.989）和 similarity ratio（0.975）上最强，且比 GPT-RoPE 更能保持 scaffold 一致性。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.8]
- **results：** 迁移学习的无条件阶段中，GPT-RoPE 的 validity 为 0.794 最好；条件迁移学习阶段中，T5MolGe 的 validity 0.884、similarity ratio 0.963 均优于 GPT-RoPE。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.10]；[doi:10.1038/s41598-025-86840-z, p.11]
- **results：** 作者还报告条件生成的分子在局部 pKd 分布上优于无条件生成，表明 scaffold 条件有助于提高对 EGFR mutant 的预测亲和力。
  - 证据：[doi:10.1038/s41598-025-86840-z, p.10]；[doi:10.1038/s41598-025-86840-z, p.11]

## 页码证据

- [doi:10.1038/s41598-025-86840-z, p.1]
- [doi:10.1038/s41598-025-86840-z, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
