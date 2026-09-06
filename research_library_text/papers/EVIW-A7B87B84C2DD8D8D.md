# A genotype-to-drug diffusion model for generation of tailored anti-cancer small molecules

- **论文 ID：** `EVIW-A7B87B84C2DD8D8D`
- **期刊 / 来源：** Nature Communications（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1038/s41467-025-60763-9](https://doi.org/10.1038/s41467-025-60763-9)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `扩散/生成`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 G2D-Diff，一个以 genotype 和离散 response class 为条件的 latent diffusion 生成框架，通过 chemical VAE、condition encoder 与 classifier-free guidance，直接学习 hit-like 抗癌分子的分布，并尝试同时给出相关基因/通路解释。

## 创新边界

`本稿的边界创新在于把临床相关基因改变与药物响应等级联合条件化到分子生成扩散模型中；但仅凭冻结证据无法验证其相对全部 prior art 的全球首创性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在癌症异质性高、最佳靶点常不明确的场景下，如何仅凭临床相关基因型与期望药物响应，直接生成可用于 hit identification 的抗癌小分子候选，是本文要解决的核心问题。

## 方法

- VAE在约150万化合物上学习潜空间，contrastive预训练genotype encoder，再以drug response条件扩散生成分子。

## 数据与基准

- GDSC、CTRP、NCI60等药物反应与基因组数据及GuacaMol化学数据。

## 比较基线

- target-based生成、phenotype-based生成及无contrastive/不同条件编码模型。

## 结果证据

- 论文报告多样性、可行性和condition fitness优于比较方法；主要是回顾性药物反应代理评价。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- SMILES随机生成有效率较低，condition fitness依赖细胞系药物反应代理；无候选合成/体内验证。

## 仍未知

- TNBC-S1 与 TNBC-S2 是否在独立体外或体内实验中得到验证，冻结证据中未见。
- 论文对全球 prior art 的相对首创性无法仅凭本地证据完全确认。
- 这些候选分子在真实临床环境中的疗效、毒性与可制造性仍未知。

## Pi 结构化证据摘录

- **baseline：** 论文将 PaccMannRL 作为唯一可直接比较的生成 baseline，并在相同数据上重训其 predictor / generator；表 1 显示其在 diversity、FCD 和 OTD 上弱于 G2D-Diff。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.5]；[doi:10.1038/s41467-025-60763-9, p.12]
- **baseline：** 为条件一致性评估，作者额外重训了 HiDRA 作为独立 drug-response predictor，用于交叉验证生成分子的 condition fitness，而不是作为生成器 baseline。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.5]
- **data：** 化学结构数据来自 GuacaMol/ChEMBL，经清洗、规范化和去重后得到 1,583,442 个 unique SMILES，并按 9:1 划分为训练集与验证集。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.9]
- **data：** 药物响应数据整合了 GDSC、CTRP 和 NCI60，形成 cell line-centric 与 drug-centric 两套数据；前者包含 1244 个 cell lines、803 个 compounds 和 432,293 个 pair，后者包含 62 个 cell lines、38,502 个 compounds 和 811,585 个 pair。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.9]；[doi:10.1038/s41467-025-60763-9, p.10]
- **data：** 作者构建了三组评估集，每组 5 个 cell lines：evaluation set 1 为训练充分的已见条件，evaluation set 2 为条件已知但生成器未见化合物，evaluation set 3 为完全未见的 zero-shot 条件。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.10]
- **data：** TNBC 临床案例从 AACR Project GENIE / cBioPortal 的 metastatic breast cancer cohort 中筛出 4 名 lethal TNBC 患者，并合并其变异与拷贝数事件形成代表性临床基因型；后续 docking 使用的蛋白结构来自 PDB。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.12]；[doi:10.1038/s41467-025-60763-9, p.13]
- **declared_resources：** processed datasets 与 source data 已公开到 GitHub repository，raw datasets 也均为公共资源，包括 GuacaMol、ChEMBL、GDSC、CTRP、NCI60、DepMap、Project GENIE、PDB 与 Enamine catalog。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.13]
- **declared_resources：** 代码与 trained model parameters 公开在 GitHub repository，论文注明其采用 PolyForm Noncommercial License 1.0.0，且部分代码改编自 lucidrains/denoising-diffusion-pytorch。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.13]
- **declared_resources：** 训练在四块 NVIDIA A100 GPU 上完成；retrosynthesis 使用 AiZynthFinder v4.3.1，并结合 ZINC、Enamine building blocks 与 USPTO reaction templates。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.11]；[doi:10.1038/s41467-025-60763-9, p.13]
- **limitations：** 作者明确指出，若未来结合 in vivo 与 clinical drug response data，模型性能还有提升空间；当前做法仍主要依赖临床相关基因型与手工离散化的五档 in vitro 响应。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.9]；[doi:10.1038/s41467-025-60763-9, p.10]
- **limitations：** 作者也承认，基于 SMILES 的 chemical VAE 会产生 ill-defined latent regions，从而带来无效化学结构；他们建议未来采用 graph-based VAE 或 3D 信息框架改进。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.9]
- **method：** 整体方法由三个串联部分组成：先用 chemical VAE 学习分子 latent space，再用 condition encoder 表达基因型与响应条件，最后用条件化 latent diffusion 生成分子 latent vector 并解码为 SMILES。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.2]；[doi:10.1038/s41467-025-60763-9, p.10]；[doi:10.1038/s41467-025-60763-9, p.11]
- **method：** chemical VAE 采用三层 LSTM 的 SMILES VAE 结构，并在约 1.58M 个去重后的 SMILES 上预训练，训练时结合 beta-VAE 与 cyclical annealing 来平衡重建和 KLD。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.9]；[doi:10.1038/s41467-025-60763-9, p.11]
- **method：** condition encoder 将 718 个临床相关基因的 mutation、copy number amplification 和 deletion 作为二值输入，并与五档 response class 一起进入带 NeST 层级 mask 的三层 transformer；作者再用对比学习预训练该编码器。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.9]；[doi:10.1038/s41467-025-60763-9, p.10]；[doi:10.1038/s41467-025-60763-9, p.11]
- **method：** 扩散生成器基于 DDPM 噪声预测器，采用六层 denoising network 和 condition injection module 注入条件向量，并使用 classifier-free guidance 控制生成分子的条件强度。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.11]；[doi:10.1038/s41467-025-60763-9, p.7]
- **results：** chemical VAE 在重建任务中达到 1.00 validity、1.00 uniqueness 和 0.99 reconstruction success；随机生成任务则报告 0.86 validity、1.00 uniqueness、1.00 novelty 和 0.89 diversity。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.2]
- **results：** condition encoder 的 PCA 显示其能按 response class 与 genotype 分离条件；基于 top-5 / top-10 相似度的 odds ratio 在敏感条件下尤其高，说明编码器学到了可区分的条件表示。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.3]
- **results：** 与 PaccMannRL 相比，G2D-Diff 在 diversity、FCD 和 OTD 上更优，而 validity 与 novelty 大体相近；Table 1 给出了三个 evaluation set 的一致趋势。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.5]
- **results：** 生成分子的 predicted AUC 随条件从 very sensitive 到 very resistant 呈单调分层，并且在 evaluation set 2 与 3 中仍保持条件一致性，作者报告两尾 Mann–Whitney U 检验 p < 1e-4。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.4]；[doi:10.1038/s41467-025-60763-9, p.5]
- **results：** 生成分子表现出接近 one-per-molecule 的 scaffold 多样性，同时保留 pharmacophore 相似性，并在 QED、SAS 与 ADMETlab 毒性预测上显示出更好的可药性特征。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.5]；[doi:10.1038/s41467-025-60763-9, p.6]
- **results：** TNBC zero-shot 案例中，TNBC-S1 与 Fimepinostat、TNBC-S2 与 Dinaciclib 在低 Tanimoto、docking 位点、PLIP 交互与 MoA similarity 上都呈现机制一致性；attention 还富集到 PI3K/AKT/PTEN、histone deacetylation 与 CDK 相关通路。
  - 证据：[doi:10.1038/s41467-025-60763-9, p.7]；[doi:10.1038/s41467-025-60763-9, p.8]

## 页码证据

- [doi:10.1038/s41467-025-60763-9, p.1]
- [doi:10.1038/s41467-025-60763-9, p.2]
- [doi:10.1038/s41467-025-60763-9, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
