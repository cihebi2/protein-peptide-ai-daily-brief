# LncPNdeep: A long non-coding RNA classifier based on large language model with peptide and nucleotide embedding

- **论文 ID：** `EVIW-02F2CAC014E9FB65`
- **期刊 / 来源：** Noncoding RNA Res
- **发表时间：** 2026 Aug 13
- **DOI：** [10.1016/j.ncrna.2026.06.004](https://doi.org/10.1016/j.ncrna.2026.06.004)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `肽与抗菌肽` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 LncPNdeep，一个把 peptide embedding 与 nucleotide embedding 融合到同一深度学习管线中的 lncRNA 分类器，声称可在 human 与跨物种数据上取得优于现有方法的表现。

## 创新边界

`新意主要是多模态嵌入融合与长序列建模，不是新生物学发现或候选分子生成。`。这不是全球首创性检索或独立复现结论。

## 研究问题

区分 lncRNA 与 coding RNA，并在跨物种场景下提升转录本分类的准确性与泛化能力。

## 方法

- 从RNA提取最长ORF肽或固定阅读框伪肽，分别生成核苷酸与肽语言模型表示，拼接后输入神经分类器；长序列分段采样以适配模型窗口。

## 数据与基准

- GENCODE Release 43人类数据：48,876条lncRNA和99,187条编码RNA训练，5,415/11,037测试；另有多种动物、真菌跨物种集合。

## 比较基线

- CNCI、CPAT、CPC2、PLEK、LncAdeep、LncRNA-Mdeep，以及RF/LR/SVM结合不同嵌入。

## 结果证据

- 人体测试准确率97.1%、特异性96.7%、敏感性98.0；多数跨物种F1超过90%，但个别物种CPAT/CPC2准确率更高。均为计算分类。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 长RNA需分段，可能丢失全局关系；伪肽生物意义有限，类别嵌入仍有显著重叠；跨物种数据分布和注释质量不同。

## 仍未知

- nucleotide transformer 是否冻结或微调在方法与计算资源描述间略有不一致。
- fake peptide 的生物学含义仍缺乏湿实验验证。
- 跨物种外推在 fungi 上明显弱于 vertebrates，边界尚不清楚。
- 未见独立外部数据集的复现结果。

## Pi 结构化证据摘录

- **baseline：** 与之对比的专用工具包括 CNCI、CPC2、CPAT、PLEK、LncAdeep 和 LncRNA Mdeep；其中 CPAT 与 PLEK 可重训，作者使用相同训练集重训。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.3]
- **baseline：** 传统 baseline 还包括 SVM、LR、RF，均在单一 embedding 上训练/测试。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.3]
- **data：** 人类数据集共 54,291 条 lncRNA 与 110,224 条 coding RNA，训练/测试分别为 48,876/99,187 与 5,415/11,037。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.2]
- **data：** 跨物种验证数据来自 Ensembl 与 Ensembl Fungi，覆盖 6 个 vertebrates 和 6 个 fungi 物种。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.2]
- **declared_resources：** 论文给出 GitHub 仓库 https://github.com/yatoka233/LncPNdeep，且宣称 pretrained weights 已上传至 Hugging Face。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.3]
- **declared_resources：** 资源消耗方面，pretraining-stage 在单张 NVIDIA V100 16 GB 上约需 5 天并配合约 50 GB CPU memory；下游在 RTX 4080 Super 上即可运行，单条 transcript embedding 提取约 1.5 s。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.6]
- **limitations：** 作者明确指出 fake peptide embedding 只是输入一致性的计算技巧，不能视为已证实的生物翻译或功能证据。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.7]
- **limitations：** 训练标签依赖 curated annotation，可能把 ORF 特征泄漏进 coding/non-coding 区分，且 pseudogene 与边界转录本仍较难。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.7]；[doi:10.1016/j.ncrna.2026.06.004, p.8]
- **limitations：** fungi 上性能下降可能来自 codon usage、ORF 长度分布、转录本 compactness 与注释不一致；作者也承认仍需独立数据集验证。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.4]；[doi:10.1016/j.ncrna.2026.06.004, p.7]
- **limitations：** 未来工作包括整合 Ribo-seq 和 experimentally validated ORFs，以增强 peptide-level 预测的生物学可信度。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.7]；[doi:10.1016/j.ncrna.2026.06.004, p.8]
- **method：** 作者以 GENCODE Release 43 的人类 coding/lncRNA 转录本构建主体数据集，并对训练集中的 lncRNA 进行 bootstrapping 以平衡类别。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.2]
- **method：** 肽特征通过 ORF 扫描与标准遗传密码翻译生成 Fake、Max、Average 三种 peptide，再送入 ProtTrans 产生 embedding；无 ORF 时使用固定读框的 pseudo-peptide 填充。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.2]
- **method：** 核苷酸特征采用 MLM 思路，结合 BigBird 与 Longformer 处理长序列，并通过 subsequence sampling 与 [CLS] 平均获得 Longformer256、BigBird256、BigBird768 表示。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.3]
- **method：** 六类 embedding 先经各自 CNN，再串接后输入 BiLSTM 与 DNN 完成二分类；文中还说明 BigBird、Longformer、ProtTrans 在下游阶段仅用于 embedding extraction。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.3]；[doi:10.1016/j.ncrna.2026.06.004, p.6]
- **results：** 在人类测试集上，LncPNdeep 报告 97.1% accuracy、96.7% specificity、98.0% sensitivity，并优于 CNCI、CPC2、CPAT、PLEK、LncAdeep、LncRNA_Mdeep。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.3]
- **results：** 传统 ML baseline 中，SVM + BigBird256 的 accuracy 最好，为 0.93，显示长序列核苷酸 embedding 具有较强判别力。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.3]
- **results：** 跨物种测试里，模型在大多数物种保持较高 accuracy/F1，panda、cow、zebrafish 等表现突出，但在部分 fungi 上有下降。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.4]
- **results：** 置换实验显示 Average Peptide Embedding 被随机化时性能下降最大；而把全部 embedding 联合后，t-SNE 的类间分离更清晰。
  - 证据：[doi:10.1016/j.ncrna.2026.06.004, p.4]；[doi:10.1016/j.ncrna.2026.06.004, p.5]；[doi:10.1016/j.ncrna.2026.06.004, p.6]

## 页码证据

- [doi:10.1016/j.ncrna.2026.06.004, p.1]
- [doi:10.1016/j.ncrna.2026.06.004, p.2]
- [doi:10.1016/j.ncrna.2026.06.004, p.3]
- [doi:10.1016/j.ncrna.2026.06.004, p.4]
- [doi:10.1016/j.ncrna.2026.06.004, p.7]
- [doi:10.1016/j.ncrna.2026.06.004, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
