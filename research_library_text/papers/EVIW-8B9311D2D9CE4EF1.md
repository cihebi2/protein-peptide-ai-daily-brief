# Molecular fingerprints are strong models for peptide function prediction

- **论文 ID：** `EVIW-8B9311D2D9CE4EF1`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2026 Apr 13
- **DOI：** [10.1093/bioinformatics/btag179](https://doi.org/10.1093/bioinformatics/btag179)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

论文声称提出并系统验证了一个很轻量但很强的 peptide 表征基线：把 count-based ECFP、Topological Torsion 和 RDKit fingerprints 与 LightGBM 结合，在 6 个 benchmark、132 个数据集上取得 SOTA，并通过 binary/count 消融、sequence shuffling 和人为长程任务对照，说明多数 peptide 任务主要依赖短程子图统计而非长程依赖。[doi:10.1093/bioinformatics/btag179, p.1][doi:10.1093/bioinformatics/btag179, p.2][doi:10.1093/bioinformatics/btag179, p.4][doi:10.1093/bioinformatics/btag179, p.5][doi:10.1093/bioinformatics/btag179, p.8][doi:10.1093/bioinformatics/btag179, p.9]

## 创新边界

`其新意边界主要在方法组合与系统性基准，而不是新的深度学习架构或新的湿实验；作者把已有的 hashed fingerprints 和 LightGBM 重新用于 peptide 任务，并用大规模对比去质疑 long-range dependency 的必要性。[doi:10.1093/bioinformatics/btag179, p.2][doi:10.1093/bioinformatics/btag179, p.3][doi:10.1093/bioinformatics/btag179, p.9]`。这不是全球首创性检索或独立复现结论。

## 研究问题

作者要回答的核心问题是：在 peptide function prediction 中，是否真的需要显式建模长程相互作用，还是像 count-based molecular fingerprints 这种只编码短程子图统计的简单方法就足够。[doi:10.1093/bioinformatics/btag179, p.1][doi:10.1093/bioinformatics/btag179, p.2][doi:10.1093/bioinformatics/btag179, p.3]

## 方法

- 从肽分子图计算count/binary ECFP、TT和RDKit指纹，训练LightGBM；与LRGB长程GNN和蛋白/肽BERT比较，并设计长程依赖反例任务。

## 数据与基准

- LRGB Peptides-func/struct和ADAPTABLE、APD、CAMP、dbAMP、DRAMP、YADAMP、XUAMP等共132个标准数据集。

## 比较基线

- GraphGPS、GINE、GatedGCN、GraphViT、GRIT、S2GCN、HDSE、AMP-BERT等。

## 结果证据

- Peptides-func ECFP AUPRC 74.60，高于S2GCN 73.11；六个AMP集TT平均F1 87.8；XUAMP ECFP AUROC 75.0/MCC 0.429。长程合成任务揭示指纹边界。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 指纹不建模构象和真正长程依赖；随机/同源拆分、类别不平衡会影响结论，适合作为基线而非普遍替代结构模型。

## 仍未知

- Supplementary Material 未读取。
- GitHub/Zenodo 代码与数据未独立核验。
- 外部 prior-art 未检索，global novelty 仅按冻结材料保守处理。

## Pi 结构化证据摘录

- **baseline：** 作者把结果与多类 graph model 对比，包括 Transformer、SAN、GraphGPS、GCN、GINE、GatedGCN、GraphViT、GRIT、HDSE 和 S2GCN，并据此强调 fingerprint 在 LRGB 上的优势。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.4]
- **baseline：** 在 AMP 任务上，他们与 AMP-BERT、BERT-Protein、cAMPs_pred、LM_pred 等 PLM 方法，以及 AMPscannerV2、ADAM-SVM、AMPEP、ampir、MACREL 等传统或混合方法比较。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.5]；[doi:10.1093/bioinformatics/btag179, p.6]
- **baseline：** 在 general benchmarks 上，他们把 ECFP 与 amino acid counts、ESM2，以及 48 种 sequence/structure encodings 对比；ECFP 多数时候优于 counts，并在 PeptideReactor、AutoPeptideML 等任务上非常有竞争力。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.7]；[doi:10.1093/bioinformatics/btag179, p.8]
- **baseline：** 论文还专门用 binary fingerprints 和 binary+length 作为消融基线，证明 count features 的增益不是简单的长度代理。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.5]
- **data：** 主评估覆盖 6 个 benchmark、132 个 datasets，跨越 LRGB、三组 AMP 基准、AutoPeptideML 和 PeptideReactor；摘要把它概括为“including LRGB and five additional peptide benchmarks”。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.1]；[doi:10.1093/bioinformatics/btag179, p.2]；[doi:10.1093/bioinformatics/btag179, p.5]；[doi:10.1093/bioinformatics/btag179, p.6]；[doi:10.1093/bioinformatics/btag179, p.7]
- **data：** LRGB 部分使用 Peptides-func 分类和 Peptides-struct 回归两个多任务数据集，并按照原 benchmark 的 metric 汇总到 task 平均值。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.4]
- **data：** AMP 部分包括 BERT-based models benchmark、XUAMP 和 AMPBenchmark；其中 XUAMP 由 9 个常用数据集经 CD-HIT 去冗余构建，AMPBenchmark 则把同一正类与 11 种负采样策略组合成 55 个数据集。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.5]；[doi:10.1093/bioinformatics/btag179, p.6]
- **data：** AutoPeptideML 包含 18 个数据集，采用同源聚类形成 out-of-distribution test split；PeptideReactor 包含 50 个数据集和 48 种 encodings，且作者把它当作 encoding benchmark 来做对照。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.7]
- **data：** 在 BERT benchmark 中，作者采用 leave-one-dataset-out 的训练方式，并对 ADAPTABLE 等数据集使用 CD-HIT-2D 去除与测试集过于相似的 peptides，以模拟更严格的泛化评估。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.5]
- **declared_resources：** 论文声明代码与数据公开在 GitHub 和 Zenodo；第 10 页的 Data availability 也重复给出同一公开地址。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.1]；[doi:10.1093/bioinformatics/btag179, p.10]
- **declared_resources：** 作者感谢 BIT Student Scientific Group 提供计算资源，并声明 AGH University of Krakow 的一般经费与 IDUB 项目支持本工作。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.9]；[doi:10.1093/bioinformatics/btag179, p.10]
- **limitations：** 作者明确承认 fingerprint 只能表达短程、局部子图，无法解决真正需要顺序和长程依赖的任务；他们自己设计的 KKK / RRR motif 任务对 fingerprints 很难，但对 ESM2 很容易。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.8]
- **limitations：** 性能并非对所有数据集都均匀，尤其是最短 peptides 上 fingerprint 和 ESM2 都会掉点，说明数据长度和结构信息量仍然重要。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.8]
- **limitations：** 最优 fingerprint 类型依赖任务与数据集；作者在 PeptideReactor 中把 fingerprint type 当超参后才得到最佳结果，说明没有单一最优配置。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.7]；[doi:10.1093/bioinformatics/btag179, p.8]
- **limitations：** 作者把 larger proteins 和 chemically modified / cyclic peptides 列为 future work，暗示当前结论主要覆盖常规 peptide benchmark，而不是更广泛的蛋白设计场景。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.9]
- **method：** 作者采用 atom-level molecular graph，将 peptide 转成定长 hashed fingerprints；重点比较的是 count-based ECFP、Topological Torsion 和 RDKit fingerprint，这些表示只编码短程子图统计，不依赖 3D 构象信息。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.2]；[doi:10.1093/bioinformatics/btag179, p.3]
- **method：** 分类器统一使用 LightGBM；正文给出的默认设置是 500 trees，并按正类频率倒数做 class weighting，除个别 benchmark 外基本不做超参调优。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.3]
- **method：** 在 LRGB 的多任务设置中，作者为每个任务单独训练一个模型，因为 LightGBM 不支持多输出；这使得 fingerprint 与图模型的对比更接近任务级评测。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.4]
- **method：** 在 PeptideReactor 上，作者用 5-fold cross-validation 只微调 fingerprint 的 radius 或 path length，并把 fingerprint type 本身当作超参来比较 FP encoding。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.7]
- **method：** 作者还做了 sequence shuffling：随机打乱训练序列中不同比例的氨基酸，以逐步破坏顺序和长程信息，再观察 fingerprint 性能是否仍然稳定。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.8]
- **results：** 在 LRGB 上，ECFP 取得 74.60 AUPRC 和 0.2432 MAE，优于 S2GCN 的 73.11 AUPRC 和 0.2447 MAE；TT 和 RDKit 也都达到或接近同类最好水平。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.4]
- **results：** count 版显著优于 binary 版及 binary+length：例如 Peptides-func 上 ECFP 从 70.57 升至 74.60，Peptides-struct 上 MAE 从 0.3049 降到 0.2432，说明提升不只是把序列长度当代理变量。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.5]
- **results：** 在 BERT-based models benchmark 上，TT 和 ECFP 的平均 F1 分别为 87.8 和 87.6，明显高于 AMP-BERT 的 75.3。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.5]
- **results：** 在 XUAMP 上，ECFP 达到 75.0 AUROC 和 0.429 MCC，超过 AMPfun 的 73.5 AUROC 和 0.414 MCC。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.6]
- **results：** 在 AMPBenchmark 上，ECFP 的 AUROC 为 97.37 ± 1.74，优于 ampir 的 96.71 ± 2.08，而且波动更小。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.6]
- **results：** 在 AutoPeptideML 上，ECFP 达到 78.1 AUROC 和 0.437 MCC，接近或超过多个 ESM2 / Prot-T5 变体；在 PeptideReactor 上，FP encoding 的 average F1 为 82.9，是表中最佳。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.7]；[doi:10.1093/bioinformatics/btag179, p.8]
- **results：** sequence shuffling 下，fingerprint 模型性能下降不超过约 4%，在 XUAMP 上几乎不变，说明它对顺序破坏相当稳健。
  - 证据：[doi:10.1093/bioinformatics/btag179, p.8]

## 页码证据

- [doi:10.1093/bioinformatics/btag179, p.10]
- [doi:10.1093/bioinformatics/btag179, p.1]
- [doi:10.1093/bioinformatics/btag179, p.2]
- [doi:10.1093/bioinformatics/btag179, p.4]
- [doi:10.1093/bioinformatics/btag179, p.5]
- [doi:10.1093/bioinformatics/btag179, p.6]
- [doi:10.1093/bioinformatics/btag179, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
