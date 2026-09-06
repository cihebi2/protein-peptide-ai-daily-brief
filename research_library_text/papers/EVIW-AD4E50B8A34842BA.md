# xBitterT5: an explainable transformer-based framework with multimodal inputs for identifying bitter-taste peptides

- **论文 ID：** `EVIW-AD4E50B8A34842BA`
- **期刊 / 来源：** Journal of Cheminformatics（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1186/s13321-025-01078-1](https://doi.org/10.1186/s13321-025-01078-1)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 xBitterT5：一个基于 pretrained BioT5+ 的多模态可解释框架，把 peptide 序列与 SELFIES 分子表示联合建模，用于 BP 分类，并配套提供 web server、源码与预训练权重。

## 创新边界

`本工作的新意主要在 BioT5+ + peptide/SELFIES 的多模态组合及解释流程；它是作者声称的首个此类 BP 识别框架，但冻结证据无法独立验证全球首创性。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何在短肽场景下，把 peptide sequence 与分子字符串信息结合起来，更准确地识别 bitter-taste peptides (BPs)，同时给出可解释的分子片段依据。

## 方法

- sequence+SELFIES输入BioT5+，分类并用attribution解释。

## 数据与基准

- 两个既有苦味肽benchmark。

## 比较基线

- iBitter-Fuse及序列/PLM模型。

## 结果证据

- xBitterT5-640 sensitivity/specificity均0.953；为计算分类。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 数据集小、苦味assay/阈值异质，attribution非感官机制。

## 仍未知

- 是否已有未被本稿覆盖的先前多模态 BP 识别方法，尚未外部核实。
- GitHub 代码、Hugging Face 权重与 web server 当前是否在线可用，尚未实际访问验证。
- 论文未提供新的湿实验验证，模型的生物学机制解释仍属计算层面的推断。

## Pi 结构化证据摘录

- **baseline：** 在 BTP640 上，xBitterT5-640 相比 iBitter-DRLF 在训练与独立测试中都取得了更高的 MCC 和 ACC，作者报告的增益分别可达 1.70%–9.40% 和 0.60%–10.90%。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.9]
- **baseline：** 在 BTP720 上，xBitterT5-720 相比 CPM-BP 在训练集提升了 MCC 11.60%、ACC 5.40%、F1 4.70%、AUC 4.70%，在独立测试集提升了 MCC 6.30%、ACC 3.50%、F1 4.10%、AUC 7.50%。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.9]；[doi:10.1186/s13321-025-01078-1, p.10]
- **data：** BTP640 是一个平衡数据集，包含 320 个 BP 和 320 个 non-BP，并按 80:20 划分为 BTP-CV 与 BTP-TS。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.3]；[doi:10.1186/s13321-025-01078-1, p.4]
- **data：** BTP720 在 BTP640 基础上扩展而来，作者仅保留唯一 bitter taste 的序列并剔除多味标签样本；做独立评估时还移除了与 BTP640 训练集重叠的序列。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.4]；[doi:10.1186/s13321-025-01078-1, p.8]
- **data：** 两个数据集中的肽大多很短，通常不超过 15 个氨基酸，这也是作者引入 molecular representation 的主要动机之一。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.4]
- **declared_resources：** 论文提供了可直接提交 FASTA 的 xBitterT5 web server，并支持结果以 CSV 下载。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.12]；[doi:10.1186/s13321-025-01078-1, p.14]
- **declared_resources：** 作者公开了 GitHub 源码与 Hugging Face 上的 xBitterT5-640 / xBitterT5-720 预训练权重。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.12]；[doi:10.1186/s13321-025-01078-1, p.14]；[doi:10.1186/s13321-025-01078-1, p.15]
- **declared_resources：** 致谢与数据可得性部分还提到 K-BDS 和 KAIT 提供计算资源，训练与独立数据集也随项目页面公开。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.14]
- **limitations：** 作者明确承认当前框架只针对 bitter peptides；若要推广到 sweet、sour、salty、umami 等多味觉任务，需要更大且标注更精确的数据集。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.13]
- **limitations：** 作者建议进一步探索 InChI、DeepSMILES、Group SELFIES 等替代分子表示，说明当前 SELFIES 路线仍有扩展空间。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.13]
- **limitations：** 解释分析中作者也承认 peptide 模态因序列太短而难以提取稳定理化特征，所以只对 SELFIES 做归因，可见短肽信息量仍有限。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.10]
- **method：** 作者将 peptide sequence 先转成 SMILES，再转成 SELFIES，并为 BioT5+ 输入添加 <bop>/<eop> 与 <bom>/<eom> 等特殊 token；还支持把 sequence 与 SELFIES 以 [SEQUENCE][SELFIES] 形式拼接输入。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.4]；[doi:10.1186/s13321-025-01078-1, p.5]
- **method：** 模型主干采用 pretrained T5 extractor，对比 ProtT5-Uniref50、ProtT5-BFD、MolT5、BioT5/BioT5+；最终冻结 encoder、仅训练部分 decoder block，并在 mean pooling 后接分类头。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.5]；[doi:10.1186/s13321-025-01078-1, p.6]
- **method：** 训练阶段使用 stratified 10-fold cross-validation 与 grid search，以 MCC 作为主要调参指标；模型解释则基于 transformers-interpret 的 Integrated Gradients，并结合 RDKit 做可视化。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.6]
- **results：** 在 BTP640 上，最佳的 multimodal BioT5+ 模型在训练集达到 MCC 0.794、ACC 0.895、F1 0.892、AUC 0.912，在独立测试集达到 MCC 0.906、ACC 0.953、F1 0.953、AUC 0.968。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.8]
- **results：** 在 BTP720 上，最佳的 multimodal BioT5+ 模型在训练集达到 MCC 0.814、ACC 0.903、F1 0.895、AUC 0.915，在独立测试集达到 MCC 0.879、ACC 0.938、F1 0.934、AUC 0.980。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.8]；[doi:10.1186/s13321-025-01078-1, p.9]
- **results：** 案例分析中，xBitterT5-720 对 Group A 的已报道 BP 全部判对，并在 Group B 的 10 条已知 BP 中判对 8 条。
  - 证据：[doi:10.1186/s13321-025-01078-1, p.12]

## 页码证据

- [doi:10.1186/s13321-025-01078-1, p.1]
- [doi:10.1186/s13321-025-01078-1, p.3]
- [doi:10.1186/s13321-025-01078-1, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
