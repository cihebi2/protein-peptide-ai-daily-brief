# AttABseq: an attention-based deep learning prediction method for antigen–antibody binding affinity changes based on protein sequences

- **论文 ID：** `EVIW-8AA96DCC4EAD6598`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2024 Jul 3
- **DOI：** [10.1093/bib/bbae304](https://doi.org/10.1093/bib/bbae304)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 AttABseq，一个端到端的 sequence-based attention 深度学习模型，融合 wild-type/mutant 抗原-抗体复合物序列、OHM+PSSM 特征、自注意力与互注意力，来回归并排序突变导致的亲和力变化，并给出残基级可解释性。

## 创新边界

`其贡献边界是亲和力变化预测与候选突变排序，不是新抗体序列生成，也不是 wet-lab 设计流程。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在缺乏可靠抗原-抗体复合物结构、只给定蛋白序列时，如何预测点突变引起的结合亲和力变化（ΔΔG），以支持抗体优化、筛选和排序。

## 方法

- 对野生型和突变复合物序列构建理化/序列特征，经embedding、多头mutual-attention和全连接回归预测delta-delta-G，以MSE训练并用PCC和R2评估。

## 数据与基准

- 三个基准为AB645（29类抗体、645突变）、AB1101（32类、1101突变）和S1131/Skempi 2.0（112类、1131突变），另有SARS-CoV-2与Ebola外部集。

## 比较基线

- 与多个序列式和结构式delta-delta-G预测方法比较，并使用AB-Bind/Skempi作为传统评测基础。

## 结果证据

- 摘要称相对其他序列模型PCC准确度提升120%，并在三基准上总体优于序列基线、与结构方法竞争；Ebola外部集报告R2=0.43。相对百分比不能替代各拆分的绝对PCC/R2。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 数据量小、复合物类型和样本数不均、序列长度不一；在抗原序列特别长时性能会下降；缺少大规模实验验证。

## 仍未知

- GitHub 仓库中是否完整公开了训练代码、参数和许可证，PDF 本身未核验。
- 外部 SARS-CoV-2 与 Ebola 数据的具体构建细节和统计检验强度，需看代码或附录才能完全确认。
- 论文报告的改进幅度主要来自作者自报结果，缺少独立复现与外部 prior-art 验证。

## Pi 结构化证据摘录

- **baseline：** K-fold 对比中的 sequence-based baselines 包括 PIPR、TransPPI、DeepFE-PPI 和 LSTM-PHV，作者称这些方法都只依赖蛋白序列输入。
  - 证据：[doi:10.1093/bib/bbae304, p.3]
- **baseline：** 结构-based baselines 主要是 FoldX、BeAtMuSiC，以及外部 SARS-CoV-2 对照中的 mCSM-AB2；论文把它们作为抗体亲和力变化预测的经典对照。
  - 证据：[doi:10.1093/bib/bbae304, p.4]；[doi:10.1093/bib/bbae304, p.6]
- **data：** AB-Bind 中抽取出 AB645：29 个抗原-抗体复合物上的 645 个 single mutations；同源的 AB1101 包含 32 个复合物上的 1101 个突变，其中 645 个为单点、456 个为多点突变。
  - 证据：[doi:10.1093/bib/bbae304, p.8]；[doi:10.1093/bib/bbae304, p.9]
- **data：** Skempi 2.0 中构建了 S1131 数据集，覆盖 112 个抗原-抗体复合物与 1131 个突变，作者将其作为另一核心 benchmark。
  - 证据：[doi:10.1093/bib/bbae304, p.8]；[doi:10.1093/bib/bbae304, p.9]
- **data：** 外部案例部分整理了 SARS-CoV-2 与 Ebola 的抗体优化数据，作者声称这些标签均来自公开文献并经实验验证；SARS-CoV-2 示例以 6WAQ 复合物为基础，Ebola 数据来自已发表实验。
  - 证据：[doi:10.1093/bib/bbae304, p.5]；[doi:10.1093/bib/bbae304, p.6]
- **declared_resources：** 资金支持来自 National Key Research and Development Program of China (2021YFE0206400)、NSFC (22220102001, 92370130) 以及 Fundamental Research Funds for the Central Universities (226-2022-00220)。
  - 证据：[doi:10.1093/bib/bbae304, p.13]
- **declared_resources：** Data availability 声明给出了 GitHub 仓库链接 https://github.com/ruofanjin/AttABseq；文中也提到 Ebola 外部结果的附加页面路径。
  - 证据：[doi:10.1093/bib/bbae304, p.6]；[doi:10.1093/bib/bbae304, p.13]
- **declared_resources：** PSSM 的生成依赖 PSI-BLAST 和 UniProtKB/Swiss-Prot，作者将其作为序列特征构建的重要外部资源。
  - 证据：[doi:10.1093/bib/bbae304, p.9]
- **limitations：** 作者明确指出，AB-Bind 和 Skempi 数据规模有限、不同数据集分布不均，而且不同抗体类型的序列长度并不统一，这些都会限制模型泛化。
  - 证据：[doi:10.1093/bib/bbae304, p.7]
- **limitations：** 论文还承认，当抗原具有特别长的氨基酸序列时，AttABseq 的预测有时会失准，说明其鲁棒性仍需改进。
  - 证据：[doi:10.1093/bib/bbae304, p.7]
- **limitations：** Ebola 外部验证缺少公开晶体结构，因此无法与结构-based 工具做同台比较，说明部分场景下的可比性受数据可得性限制。
  - 证据：[doi:10.1093/bib/bbae304, p.6]
- **method：** AttABseq 以 wild-type 与 mutant 抗原-抗体复合物的四类序列输入为基础，先将 OHM 与 PSSM 拼接为 (n,40) 特征，再经 Conv1D、gated linear units、self-attention 和 mutual-attention 提取表示，最终用全连接层回归 ΔΔG。
  - 证据：[doi:10.1093/bib/bbae304, p.9]；[doi:10.1093/bib/bbae304, p.10]
- **method：** 训练与评估使用 MSELoss 进行回归学习，并以 PCC 与 R2 作为主要指标；实验设计中，AB1101 采用 5-fold，AB645 与 S1131 采用 10-fold，同时还做了 label-ascending ordered split。
  - 证据：[doi:10.1093/bib/bbae304, p.10]；[doi:10.1093/bib/bbae304, p.11]
- **method：** 为解释 attention 权重，作者对 wild-type 与 mutant 的权重矩阵做归一化后相减，构造 residue-level 的差异热图，用于解释突变对亲和力变化的影响。
  - 证据：[doi:10.1093/bib/bbae304, p.11]；[doi:10.1093/bib/bbae304, p.12]
- **results：** 在 K-fold cross-validation 中，AttABseq 在 AB645 上取得 PCC=0.440、R2=0.174；在 S1131 上取得 PCC=0.663、R2=0.368；在 AB1101 上取得 PCC=0.587，均优于文中列出的 sequence-based 对照。
  - 证据：[doi:10.1093/bib/bbae304, p.3]
- **results：** 作者在 AB645、AB1101、S1131 的 label-ascending split 上分别报告 PCC=0.528、0.519、0.470，说明模型在更接近真实分布的划分下仍保持较稳健的泛化。
  - 证据：[doi:10.1093/bib/bbae304, p.3]；[doi:10.1093/bib/bbae304, p.4]
- **results：** 与结构方法相比，AttABseq 在表1中的 AB645、S1131、AB1101 结果均显著高于 FoldX 与 BeAtMuSiC，说明序列模型在该任务上可与结构法竞争。
  - 证据：[doi:10.1093/bib/bbae304, p.4]
- **results：** 在 SARS-CoV-2 VHH 优化外部实验中，AttABseq 的 R2=0.76，高于 FoldX 0.69、BeAtMuSiC 0.16、mCSM-AB2 0.13；在 Ebola 外部数据上，作者报告 R2=0.43。
  - 证据：[doi:10.1093/bib/bbae304, p.6]
- **results：** 消融实验显示 attention block 会明显提升性能，而可视化分析表明模型能够把权重集中到突变残基及其邻域。
  - 证据：[doi:10.1093/bib/bbae304, p.6]；[doi:10.1093/bib/bbae304, p.7]

## 页码证据

- [doi:10.1093/bib/bbae304, p.1]
- [doi:10.1093/bib/bbae304, p.3]
- [doi:10.1093/bib/bbae304, p.7]
- [doi:10.1093/bib/bbae304, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
