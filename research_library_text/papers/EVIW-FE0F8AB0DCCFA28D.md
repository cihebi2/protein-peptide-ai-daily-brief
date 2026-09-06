# PHIStruct: improving phage-host interaction prediction at low sequence similarity settings using structure-aware protein embeddings

- **论文 ID：** `EVIW-FE0F8AB0DCCFA28D`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2025 Jan 13
- **DOI：** [10.1093/bioinformatics/btaf016](https://doi.org/10.1093/bioinformatics/btaf016)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称提出PHIStruct：先用ColabFold预测RBP结构，再用SaProt生成structure-aware embeddings，最后用两层MLP预测ESKAPEE宿主属，并在低相似度场景优于多种sequence-only与BLAST基线。[doi:10.1093/bioinformatics/btaf016, p.1][doi:10.1093/bioinformatics/btaf016, p.2][doi:10.1093/bioinformatics/btaf016, p.6]

## 创新边界

`创新边界主要是任务级方法整合，而非已证明的全球首创；本次冻结证据不足以验证独立prior-art。[doi:10.1093/bioinformatics/btaf016, p.1][doi:10.1093/bioinformatics/btaf016, p.11]`。这不是全球首创性检索或独立复现结论。

## 研究问题

在低序列相似性条件下，如何把RBP的结构信息纳入phage-host interaction预测，以提升对ESKAPEE宿主属的判别能力。[doi:10.1093/bioinformatics/btaf016, p.1][doi:10.1093/bioinformatics/btaf016, p.2]

## 方法

- 对7627个受体结合蛋白预测结构，生成SaProt结构感知token/嵌入，使用SMOTE-Tomek平衡和MLP多分类，并按40%至100%序列相似性构建拆分。

## 数据与基准

- 3350个噬菌体的7627个受体结合蛋白，宿主为ESKAPEE属；40%拆分训练4,465、测试3,203。

## 比较基线

- Boeckaerts工具、PHIEmbed、Badam-Rao方法、BLASTp、PSI-BLAST、不同结构感知/序列嵌入和分类器。

## 结果证据

- 低于40%相似性且置信度阈值大于50%时，宏F1比非结构ML工具高7至9个百分点、比BLASTp高5至6个百分点；这些是计算宿主分类结果。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 只能到宿主属且只覆盖ESKAPEE；依赖ColabFold结构质量；可解释性不足，其他感染蛋白与低分类层级标志尚未纳入。

## 仍未知

- 补充材料中的逐图逐表数值未在本次审读中逐项核验。
- GitHub仓库是否完整可运行、许可证是否满足复用条件，冻结文本无法确认。
- 论文未提供湿实验验证，因此结果仅代表计算评估。

## Pi 结构化证据摘录

- **baseline：** ML基线包括Boeckaerts et al. 2021的随机森林手工特征模型、PHIEmbed的ProtT5嵌入随机森林模型，以及Badam and Rao 2024的ESM-1b嵌入MLP；作者对它们都在同一数据集上重训。[doi:10.1093/bioinformatics/btaf016, p.6]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.6]
- **baseline：** 序列比对基线包括BLASTp（E-value=0.05，BLOSUM62）与PSI-BLAST（最多5轮迭代，E-value=0.05，profile inclusion threshold=0.002），并以top hit的属标签作为预测结果。[doi:10.1093/bioinformatics/btaf016, p.6]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.6]
- **baseline：** 表示学习对照还包括同架构MLP使用ProtT5、ESM-1b、ESM-2，以及结构-aware的ProstT5和PST嵌入；这些比较用于隔离表示差异的影响。[doi:10.1093/bioinformatics/btaf016, p.8][doi:10.1093/bioinformatics/btaf016, p.9]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.8]；[doi:10.1093/bioinformatics/btaf016, p.9]
- **baseline：** 下游分类器对照包括SVM与random forest，它们与PHIStruct共享同一SaProt输入，用来检验MLP是否是更优下游选择。[doi:10.1093/bioinformatics/btaf016, p.10]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.10]
- **data：** 用于ESKAPEE任务的核心数据集包含7,627个非冗余RBP，来自3,350个噬菌体；作者还扩展到19,081个RBP、8,525个噬菌体和238个宿主属。[doi:10.1093/bioinformatics/btaf016, p.4]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.4]
- **data：** ESKAPEE各属的ColabFold结构置信度整体较高，均值都在77%以上、中位数都在80%以上；扩展数据集的总体平均pLDDT为78.45%，中位数为81.69%。[doi:10.1093/bioinformatics/btaf016, p.4]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.4]
- **data：** 训练/测试规模随最大训练-测试相似度s变化而变化，例如s=40%时训练集在SMOTE-Tomek前后为4,465/11,662，测试集为3,203；s=100%时则为5,338/16,942与2,340。[doi:10.1093/bioinformatics/btaf016, p.5]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.5]
- **declared_resources：** 论文声明数据与源码托管在GitHub仓库 https://github.com/bioinfodlsu/PHIStruct ；冻结文本未核验仓库内容、许可证或可运行性。[doi:10.1093/bioinformatics/btaf016, p.1][doi:10.1093/bioinformatics/btaf016, p.11]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.1]；[doi:10.1093/bioinformatics/btaf016, p.11]
- **declared_resources：** 作者声明使用了Google TPU Research Cloud的Cloud TPUs，以及Monash University、University of Queensland和Queensland Cyber Infrastructure Foundation提供的MLeRP算力。[doi:10.1093/bioinformatics/btaf016, p.11]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.11]
- **declared_resources：** 资金来源包括DOST-PCHRD的ATTACK-AMR项目，另致谢了方法建议；这些属于论文自报资源支持。[doi:10.1093/bioinformatics/btaf016, p.11]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.11]
- **limitations：** 作者指出在低相似性场景下，模型容易把Enterobacter和Klebsiella误判为Escherichia，反映出属间细粒度区分仍不足。[doi:10.1093/bioinformatics/btaf016, p.10]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.10]
- **limitations：** 方法高度依赖RBP识别质量；对未注释蛋白的in silico筛选结果质量会直接影响数据集与后续分类表现。[doi:10.1093/bioinformatics/btaf016, p.11]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.11]
- **limitations：** 作者明确提到模型可解释性仍是挑战，结构-aware token与embedding的attention分析需要后续研究。[doi:10.1093/bioinformatics/btaf016, p.11]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.11]
- **method：** 作者先从GenBank与INPHARED收集噬菌体序列，剔除非细菌宿主，并对缺少注释的序列用Prokka/Prodigal/PHROG补注释。[doi:10.1093/bioinformatics/btaf016, p.2]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.2]
- **method：** RBP识别结合了作者先前定义的正则规则、排除列表，以及对hypothetical proteins的ProtBert+PhageRBPdetect判别，随后去除长度离群值并用CD-HIT去冗余。[doi:10.1093/bioinformatics/btaf016, p.2][doi:10.1093/bioinformatics/btaf016, p.4]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.2]；[doi:10.1093/bioinformatics/btaf016, p.4]
- **method：** 作者用ColabFold预测RBP结构，再将序列与结构token一起输入SaProt，取最后一层hidden states均值作为1280维structure-aware embedding。[doi:10.1093/bioinformatics/btaf016, p.4]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.4]
- **method：** 分类器采用两层MLP（160与80个神经元），并按CD-HIT相似度阈值s构造70/30训练测试集，辅以SMOTE-Tomek平衡类别，再在不同置信阈值k下评估macro与weighted指标。[doi:10.1093/bioinformatics/btaf016, p.5]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.5]
- **results：** 在s=40%时，PHIStruct达到最高macro-F1 57.67%，macro-recall 63.09%，macro-precision 69.43%，并在高置信度区间对其他ML基线保持更稳的F1。[doi:10.1093/bioinformatics/btaf016, p.6]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.6]
- **results：** 在s=60%、80%与100%时，PHIStruct仍保持有竞争力的macro性能；其中s=100%时macro-recall为81.69%、macro-precision为87.40%、macro-F1为81.12%。[doi:10.1093/bioinformatics/btaf016, p.6]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.6]
- **results：** 加权指标与macro趋势一致：例如s=40%时weighted recall为64.23%、weighted precision为74.50%、weighted F1为63.41%，并在较高相似度阈值下继续保持领先或接近领先。[doi:10.1093/bioinformatics/btaf016, p.7]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.7]
- **results：** UMAP与embedding距离分析显示，SaProt表示在属级别形成局部簇，同属与异属RBP对的cosine distance分布差异显著，支持结构感知表示具有判别力。[doi:10.1093/bioinformatics/btaf016, p.7][doi:10.1093/bioinformatics/btaf016, p.8]
  - 证据：[doi:10.1093/bioinformatics/btaf016, p.7]；[doi:10.1093/bioinformatics/btaf016, p.8]

## 页码证据

- [doi:10.1093/bioinformatics/btaf016, p.10]
- [doi:10.1093/bioinformatics/btaf016, p.11]
- [doi:10.1093/bioinformatics/btaf016, p.1]
- [doi:10.1093/bioinformatics/btaf016, p.4]
- [doi:10.1093/bioinformatics/btaf016, p.5]
- [doi:10.1093/bioinformatics/btaf016, p.6]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
