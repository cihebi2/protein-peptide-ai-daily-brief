# Seq2Phase: language model-based accurate prediction of client proteins in liquid-liquid phase separation

- **论文 ID：** `EVIW-EFC798AC8E4439DA`
- **期刊 / 来源：** Bioinform Adv
- **发表时间：** 2023 Dec 22
- **DOI：** [10.1093/bioadv/vbad189](https://doi.org/10.1093/bioadv/vbad189)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 Seq2Phase：结合 ProtTrans/ESM 序列表征与 SVM、RF、HGBC、NN 的 stacking 集成模型，作为首个 LLPS client 预测器，并声称能发现大量未注释 client。

## 创新边界

`创新边界主要在序列驱动的 client/scaffold/non-LLPS 判别与跨物种推断；不涉及 wet-lab 验证，也不直接生成或优化新候选分子。`。这不是全球首创性检索或独立复现结论。

## 研究问题

从氨基酸序列中准确识别液-液相分离（LLPS）中的 client 蛋白，并在缺乏明确手工特征规则的情况下实现跨物种泛化。

## 方法

- 蛋白PLM嵌入降维后输入传统/深度分类器，随机/Tomek下采样处理不平衡。

## 数据与基准

- 人、小鼠、酵母、植物LLPS client/non-LLPS数据，限制<1000 aa。

## 比较基线

- 传统序列特征与不同PLM/分类器。

## 结果证据

- 论文报告跨物种高准确率并识别与教科书IDR偏见不同的特征；为预测/统计关联。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 标签和负样本不完整，长度截断；跨物种并不证明新client相分离。

## 仍未知

- 新增的 2097 个 human 候选及跨物种新增 client 是否逐项经湿实验确认，页内未见。
- non-LLPS 负例中实际混入多少未注释 client，页内没有量化。

## Pi 结构化证据摘录

- **baseline：** 作者将 Seq2Phase 与 425 维 naive baseline 比较，后者包含 hydrophobicity、length、amino-acid ratios、dimers、IDR、low-complexity 与 charged amino acids 等特征。
  - 证据：[doi:10.1093/bioadv/vbad189, p.5]
- **baseline：** 作者还与 PScore 及 PhaSePred 的 SaPS/PdPS scaffold predictors 比较，结果显示 Seq2Phase 对 client prediction 最强。
  - 证据：[doi:10.1093/bioadv/vbad189, p.5]
- **baseline：** 在 scaffold vs non-LLPS 与 scaffold vs client 任务上，Seq2Phase 与既有 scaffold predictors 的表现互有强弱，部分设置下达到相当或更优水平。
  - 证据：[doi:10.1093/bioadv/vbad189, p.5]
- **data：** 训练数据来自 Swiss-Prot 与 DrLLPS：H.sapiens 代表序列包含 75 个 scaffold、2700 个 client 和 12562 个 non-LLPS；S.cerevisiae 代表序列包含 15 个 scaffold、573 个 client 和 5247 个 non-LLPS。
  - 证据：[doi:10.1093/bioadv/vbad189, p.3]
- **data：** 跨物种评估使用 Mus musculus 与 Arabidopsis thaliana 的 Swiss-Prot proteome，并在去除与 human 相似序列后分别保留 124、17、255 个 client 序列用于验证。
  - 证据：[doi:10.1093/bioadv/vbad189, p.7]
- **data：** GO 富集、UMAP 可视化和结构分析依赖 GOA tools、go-basic.obo、goa_human.gaf、UMAP 与 AlphaFold DB 等外部资源。
  - 证据：[doi:10.1093/bioadv/vbad189, p.2]；[doi:10.1093/bioadv/vbad189, p.7]；[doi:10.1093/bioadv/vbad189, p.10]
- **declared_resources：** 作者在论文中声明 Python 软件代码已公开于 GitHub 仓库 Seq2Phase。
  - 证据：[doi:10.1093/bioadv/vbad189, p.1]
- **declared_resources：** 论文显式依赖 Swiss-Prot、DrLLPS v1.0、ProtTrans、ESM2、GOA tools、DIAMOND、UMAP 与 AlphaFold DB 等外部资源/工具。
  - 证据：[doi:10.1093/bioadv/vbad189, p.2]；[doi:10.1093/bioadv/vbad189, p.3]；[doi:10.1093/bioadv/vbad189, p.7]；[doi:10.1093/bioadv/vbad189, p.10]
- **limitations：** 作者明确指出 DrLLPS 标注并不完整，因此所谓 non-LLPS 里可能混入尚未实验确认的真实 client，预测中的“假阳性”不能直接视为错误。
  - 证据：[doi:10.1093/bioadv/vbad189, p.5]
- **limitations：** 跨物种评估必须先用 DIAMOND 去除与 human 相似的序列，说明近缘同源会抬高评估结果；因此泛化结论仍依赖去同源处理。
  - 证据：[doi:10.1093/bioadv/vbad189, p.7]
- **method：** 作者从 Swiss-Prot 下载 human 和 yeast proteome，并用 DrLLPS 提取 scaffold、client 与 regulator 标签；随后以 CD-HIT 在 50% 序列同一性阈值下聚类、选取代表序列降冗余，且含 regulator 的簇会被排除。
  - 证据：[doi:10.1093/bioadv/vbad189, p.2]；[doi:10.1093/bioadv/vbad189, p.3]
- **method：** 序列表示使用 ProtTransT5XLU50 与 ESM2-3B 的 per-residue embedding，再对整条蛋白取平均；分类阶段比较了 SVM、RF、HGBC、NN，并用 stacking + logistic regression 形成集成模型。
  - 证据：[doi:10.1093/bioadv/vbad189, p.2]；[doi:10.1093/bioadv/vbad189, p.3]
- **method：** 跨物种预测时，作者用 human 训练的模型评估 mouse、yeast 与 Arabidopsis，并先用 DIAMOND 去除与 human 相似的序列；区域级预测则用 100 aa sliding window 生成 client-like regions。
  - 证据：[doi:10.1093/bioadv/vbad189, p.2]；[doi:10.1093/bioadv/vbad189, p.7]
- **results：** 在 human client vs non-LLPS 任务上，PT-T5XLU50 + stacked ensemble 达到 ROC AUC 0.859、PR AUC 0.630；作者同时报告 PT-T5XLU50 整体优于 ESM2-3B，且 stacking 略优于单独 SVM。
  - 证据：[doi:10.1093/bioadv/vbad189, p.5]
- **results：** Seq2Phase 在 12,562 个 human non-LLPS 中预测出 2097 个 client 候选，这些候选在 membraneless organelle 相关 GO-CC 术语上的富集模式与已知 client 相近。
  - 证据：[doi:10.1093/bioadv/vbad189, p.5]；[doi:10.1093/bioadv/vbad189, p.6]
- **results：** human 训练模型迁移到非同源跨物种集时，ROC AUC 分别为 0.818（yeast）、0.846（mouse）和 0.845（Arabidopsis），显示较好的泛化。
  - 证据：[doi:10.1093/bioadv/vbad189, p.8]
- **results：** 作者进一步预测出 1121、4440 和 2944 个额外 client（分别对应 yeast、mouse、Arabidopsis），并报告 LLPS regulator 的 client score 显著高于 non-LLPS。
  - 证据：[doi:10.1093/bioadv/vbad189, p.8]；[doi:10.1093/bioadv/vbad189, p.10]
- **results：** 区域级分析显示，高 client score 往往落在结构化片段；作者据此认为许多 LLPS 相关蛋白并不只由大规模无序区定义。
  - 证据：[doi:10.1093/bioadv/vbad189, p.10]

## 页码证据

- [doi:10.1093/bioadv/vbad189, p.1]
- [doi:10.1093/bioadv/vbad189, p.2]
- [doi:10.1093/bioadv/vbad189, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
