# TransBind allows precise detection of DNA-binding proteins and residues using language models and deep learning

- **论文 ID：** `EVIW-457E2FBD9F52B0DD`
- **期刊 / 来源：** Communications Biology（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1038/s42003-025-07534-w](https://doi.org/10.1038/s42003-025-07534-w)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 TransBind：先用 ProtT5-XL-UniRef50 生成残基级语言模型嵌入，再借助 self-attention 建模全局上下文，随后用 stacked Inception V2 做局部特征提取，并用加权损失缓解类别不平衡，从而提升 DNA-binding proteins 与 residues 的预测性能。

## 创新边界

`新意主要在这个 sequence-only 架构的组合设计、残基分离策略和加权训练；冻结页只支持方法层面的增量改进，未提供独立 prior-art 证据来验证全球新颖性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在仅给定蛋白质一级序列的条件下，同时准确预测 DNA-binding proteins 与 DNA-binding residues，并尽量摆脱对 MSA、PSSM/HMM 和结构信息的依赖；作者还要处理残基层面极端的正负样本不平衡。

## 方法

- PLM编码序列，第一级protein classification，第二级残基预测并用不平衡策略训练。

## 数据与基准

- 多个实验DNA-binding protein/residue数据和case studies。

## 比较基线

- ProteDNA、PSSM/HMM和其他sequence/site predictor。

## 结果证据

- 论文报告准确度与效率优于SOTA；属于计算分类。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- binding residue标签稀疏，二级误差受一级筛选传播；无实验结合验证。

## 仍未知

- 真实前瞻性外部数据上的泛化能力仍未知
- 代码仓库的具体 commit 与可复现实验环境未在冻结页中给出
- 是否能稳定迁移到 RNA binding 或其他 ligand class 仍需进一步验证

## Pi 结构化证据摘录

- **baseline：** 与依赖 PSSM、HMM 和 MSA 的传统方法相比，TransBind 直接绕开了多序列比对流程，作者也强调这显著降低了特征生成开销。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.1]；[doi:10.1038/s42003-025-07534-w, p.2]；[doi:10.1038/s42003-025-07534-w, p.9]
- **baseline：** 在 PDNA-41 上，iProDNA 和 ProteDNA 都表现出明显缺陷：前者 false positive 较多，后者 specificity 虽高但 sensitivity 只有 4.77%。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.4]；[doi:10.1038/s42003-025-07534-w, p.5]
- **baseline：** 在 DNA-129 / RNA-117 上，作者把 TransBind 与 GraphBind、NABind、NucBind、DNAPred、TargetDNA、CLAPE-DB 等结构或语言模型混合基线进行比较。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.4]；[doi:10.1038/s42003-025-07534-w, p.5]；[doi:10.1038/s42003-025-07534-w, p.6]
- **data：** 残基级训练/验证主要使用 PDNA-224、PDNA-316、PDNA-543、DNA-573 和 RNA-495；蛋白级训练/验证使用 PDB-1075。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.11]；[doi:10.1038/s42003-025-07534-w, p.12]
- **data：** 独立测试集包括 PDNA-41、DNA-129、RNA-117 和 PDB-186；作者还把 PDNA-41 中 4 条与训练集相似度大于 30% 的序列剔除，得到 37 条非冗余序列版本。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.12]
- **data：** 作者说明数据来自 PDB、BioLiP 等公开来源，并用 CD-HIT 以 30% 序列同一性阈值去冗余。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.11]；[doi:10.1038/s42003-025-07534-w, p.12]
- **declared_resources：** 作者声明数据集可在 Zenodo 获取，代码也以 open source project 形式发布，并提供了 web server。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.12]；[doi:10.1038/s42003-025-07534-w, p.14]
- **declared_resources：** 运行时间实验在 13th Generation Intel Core i7-13700HX、64GB RAM 和 NVIDIA GeForce RTX 4070 Laptop GPU 上完成。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.9]
- **declared_resources：** 作者还给出了用于复现实验的公开数据源与补充材料入口。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.12]；[doi:10.1038/s42003-025-07534-w, p.14]
- **limitations：** 冻结页没有新的 wet-lab 实验；全部结论都来自公开 benchmark、case study 和离线统计评估。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.8]；[doi:10.1038/s42003-025-07534-w, p.12]；[doi:10.1038/s42003-025-07534-w, p.14]
- **limitations：** 作者明确指出，针对 orphan proteins 和 fast-evolving proteins 的专门基准不足，因此无法对这类场景做全面比较。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.6]；[doi:10.1038/s42003-025-07534-w, p.9]
- **limitations：** 在部分基准上它并非处处最优，例如 PDB-1075 验证集和 DNA-129 / RNA-117 的某些指标仍有其他方法更强。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.8]；[doi:10.1038/s42003-025-07534-w, p.4]；[doi:10.1038/s42003-025-07534-w, p.5]；[doi:10.1038/s42003-025-07534-w, p.6]
- **limitations：** 方法依赖 ProtT5-XL-UniRef50 这类较大的预训练模型；作者也把继续探索更新、更大的 protein language models 视为后续方向。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.6]；[doi:10.1038/s42003-025-07534-w, p.9]
- **method：** TransBind 以 ProtT5-XL-UniRef50 为每个氨基酸残基生成 1024 维 embedding，并通过 self-attention 聚合全局上下文信息。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.9]；[doi:10.1038/s42003-025-07534-w, p.10]
- **method：** 模型不把整条序列直接送入分类器，而是把每个残基的 context vector 单独送入 stacked Inception V2 作为局部特征提取器。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.10]
- **method：** 训练时使用 inverse-frequency 的 weighted cross-entropy 处理正负样本不平衡，蛋白级任务则用加权 pooling 汇总残基层预测。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.10]；[doi:10.1038/s42003-025-07534-w, p.11]
- **results：** 在 PDNA-224 上，TransBind 报告 MCC 0.82、Accuracy 97.68、Sensitivity 86.1、Specificity 98.75、AUC 0.90，表中整体优于此前方法。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.2]；[doi:10.1038/s42003-025-07534-w, p.4]
- **results：** 在 PDNA-316 和 PDNA-543 上，TransBind 分别达到 MCC 0.827 / AUC 0.970 和 MCC 0.643 / AUC 0.917，整体处于最强或接近最强水平。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.4]；[doi:10.1038/s42003-025-07534-w, p.5]
- **results：** 在独立测试 PDNA-41 的 37 条非冗余序列上，TransBind 达到 MCC 0.427、AUC 0.848；在 PDB-186 上达到 Accuracy 90.86、MCC 0.82。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.5]；[doi:10.1038/s42003-025-07534-w, p.8]
- **results：** 作者还报告，PDB-1075 验证集上 TransBind 并非所有指标都最优，但在 DNA-129 / RNA-117 上它对 sequence-only 方法具有很强竞争力。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.8]；[doi:10.1038/s42003-025-07534-w, p.4]；[doi:10.1038/s42003-025-07534-w, p.5]；[doi:10.1038/s42003-025-07534-w, p.6]
- **results：** 消融实验显示，3 个 inception block 表现最好，去掉 weighted loss 后 MCC 明显下降；运行时间上，ProtTrans 特征生成少于 5 分钟，而 PSSM 特征生成约 37 小时。
  - 证据：[doi:10.1038/s42003-025-07534-w, p.6]；[doi:10.1038/s42003-025-07534-w, p.9]

## 页码证据

- [doi:10.1038/s42003-025-07534-w, p.1]
- [doi:10.1038/s42003-025-07534-w, p.4]
- [doi:10.1038/s42003-025-07534-w, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
