# MOFormer: navigating the antimicrobial peptide design space with Pareto-based multi-objective transformer

- **论文 ID：** `EVIW-DDA5A6DE373DB097`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2025 Nov 5
- **DOI：** [10.1093/bib/bbaf376](https://doi.org/10.1093/bib/bbaf376)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 MOFormer，一个基于 conditional Transformer 的多目标 AMP 生成框架，结合 multi-fusion descriptors、正则化潜空间与 Pareto 反馈筛选，用于同时优化 MIC、HEMO 和 TOXI。

## 创新边界

`可确认的是论文内的组合式方法与筛选流程；无法仅凭冻结页证明其相对全局 prior art 的唯一新颖性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在多目标约束下设计抗菌肽，使其同时提升抗菌活性、降低溶血/毒性，并尽量保持序列多样性与可筛选性。

## 方法

- sequence transformer生成，多个property predictors构成Pareto front。

## 数据与基准

- AMP/非AMP及多property datasets。

## 比较基线

- 单目标/加权多目标AMP generators。

## 结果证据

- 论文报告更优多目标trade-off和novelty；为计算生成。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- Pareto依赖predictor calibration，无实验/体内。

## 仍未知

- 补充材料中的完整超参数与实现细节在冻结页中未完全展开。
- 生成候选是否经过真实湿实验验证，冻结页未提供实测结果。
- 相对更广泛 prior art 的全球新颖性无法仅凭冻结页独立确认。

## Pi 结构化证据摘录

- **baseline：** 文中对比了 LSTM、AMP-GAN、PepGAN、WAE、AMPEMO 与 HMAMP，并分别说明这些方法在多目标控制、搜索方式或训练稳定性上的差异。
  - 证据：[doi:10.1093/bib/bbaf376, p.5]
- **baseline：** 作者还设置了 MOFormer (w/o D) 与 MOFormer (w/o F) 两个消融版本，用于分别移除 descriptors 和反馈环。
  - 证据：[doi:10.1093/bib/bbaf376, p.5]
- **data：** 核心训练数据为 4096 条 AMP 序列，来源于多个已知数据集，并被筛选为对 E. coli 具有低 MIC 且 HEMO 概率低于 0.7。
  - 证据：[doi:10.1093/bib/bbaf376, p.2]
- **data：** 作者还使用了 4547 条 AMP 活性样本、1006 条 HEMO/非 HEMO 平衡样本，以及 201 条 TOXI 样本和等量对照。
  - 证据：[doi:10.1093/bib/bbaf376, p.2]
- **data：** 为复现条件表示，59 维 descriptors、PCA loadings 与最终 3 维控制向量被声明放在 Supplementary Materials 和 GitHub 中。
  - 证据：[doi:10.1093/bib/bbaf376, p.4]；[doi:10.1093/bib/bbaf376, p.11]
- **declared_resources：** 作者声明 59 维 multi-fusion descriptors、PCA loadings 和 3 维 control vector 已随 Supplementary Materials 提供，并可在 GitHub 获取。
  - 证据：[doi:10.1093/bib/bbaf376, p.4]；[doi:10.1093/bib/bbaf376, p.11]
- **declared_resources：** 论文末尾给出 source code 与 processed datasets 的仓库地址：https://github.com/wl-wl/MOFormer/tree/master。
  - 证据：[doi:10.1093/bib/bbaf376, p.11]
- **limitations：** 作者明确指出 TOXI 数据稀缺且难以获取，这会限制验证过程和模型表现。
  - 证据：[doi:10.1093/bib/bbaf376, p.10]
- **limitations：** 在 MIC<0 与极低 HEMO 区域，生成密度仍然稀疏，说明多目标权衡会压缩可达多样性。
  - 证据：[doi:10.1093/bib/bbaf376, p.6]；[doi:10.1093/bib/bbaf376, p.7]
- **limitations：** 论文把 peptide synthesis、purification、in vitro assays 和 MD simulations 放到 future work，说明当前冻结证据中没有湿实验验证。
  - 证据：[doi:10.1093/bib/bbaf376, p.10]
- **method：** 研究把 AMP 设计表述为多目标条件生成问题，并用 MIC 与 HEMO/TOXI 的权衡来驱动候选序列生成与排序。
  - 证据：[doi:10.1093/bib/bbaf376, p.1]；[doi:10.1093/bib/bbaf376, p.2]
- **method：** 训练集来自 Witten、Szymczak 和 Hasan 等来源，序列长度上限为 60 aa；经多序列比对与 0.35 去冗余后，得到 4096 条实验验证 AMP。
  - 证据：[doi:10.1093/bib/bbaf376, p.2]
- **method：** 条件输入由 AAC 与 CTDC 组成的 59 维 multi-fusion descriptors 构成，并通过 PCA 压缩为 3 维控制向量以注入条件信息。
  - 证据：[doi:10.1093/bib/bbaf376, p.2]；[doi:10.1093/bib/bbaf376, p.4]
- **method：** MOFormer 采用 conditional Transformer 的 p(x|c) 形式，并用 reconstruction loss、KL annealing、Gaussian dropout 及针对低 MIC/低 HEMO 的辅助正则项稳定训练。
  - 证据：[doi:10.1093/bib/bbaf376, p.3]；[doi:10.1093/bib/bbaf376, p.4]
- **method：** MIC 回归器与 HEMO/TOXI 分类器都基于 Prot-BERT-BFD 微调，再用于生成后筛选和 multi-objective 评估。
  - 证据：[doi:10.1093/bib/bbaf376, p.4]；[doi:10.1093/bib/bbaf376, p.5]
- **method：** 生成阶段使用 non-dominated sorting 与 Pareto-based feedback，把 top PF1-PF10 的候选重新编码并回灌训练集。
  - 证据：[doi:10.1093/bib/bbaf376, p.5]
- **results：** 在 MIC+HEMO 任务上，MOFormer 的 HV 为 0.976，优于文中比较的其他方法。
  - 证据：[doi:10.1093/bib/bbaf376, p.7]
- **results：** 在 MIC+TOXI 任务上，MOFormer 的 HV 为 1.291，同样高于 HMAMP、PepGAN 等基线。
  - 证据：[doi:10.1093/bib/bbaf376, p.10]
- **results：** 模型生成序列的 diversity score 为 32.691；当 Levenshtein 阈值 T=3 时，novelty score 为 0.289，平均最小编辑距离为 3.672。
  - 证据：[doi:10.1093/bib/bbaf376, p.5]；[doi:10.1093/bib/bbaf376, p.6]
- **results：** Top 5 PF 共得到 67 个候选，之后用传统 AMP classifier/SVM 筛到 56 个；其中若干候选显示 coil 或 alpha-helix 结构，PIDDT 约在 70% 到 90% 之间。
  - 证据：[doi:10.1093/bib/bbaf376, p.8]；[doi:10.1093/bib/bbaf376, p.9]

## 页码证据

- [doi:10.1093/bib/bbaf376, p.1]
- [doi:10.1093/bib/bbaf376, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
