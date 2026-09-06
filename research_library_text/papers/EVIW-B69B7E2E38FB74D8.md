# A Machine Learning Model for the Proteome-Wide Prediction of Lipid-Interacting Proteins

- **论文 ID：** `EVIW-B69B7E2E38FB74D8`
- **期刊 / 来源：** J Chem Inf Model
- **发表时间：** 2025 Sep 4
- **DOI：** [10.1021/acs.jcim.5c01076](https://doi.org/10.1021/acs.jcim.5c01076)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 SLiPP：先用 fpocket 从结构中提取口袋，再用 Random Forest 依据口袋物化特征区分 lipid-binding pockets 与其他口袋，并将其扩展到 E. coli、S. cerevisiae 和 H. sapiens 的蛋白组预测；同时以 ADCK5 做了实验验证。[doi:10.1021/acs.jcim.5c01076, p.1][doi:10.1021/acs.jcim.5c01076, p.3][doi:10.1021/acs.jcim.5c01076, p.4]

## 创新边界

`创新主要在结构口袋级别的机器学习筛选与蛋白组应用，不是全新脂质化学机制或全球新颖性已被独立核验的方案。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在蛋白结构和蛋白组尺度上，快速识别可与脂质相互作用的蛋白及其结合口袋，以弥补序列同源、粗粒度注释和低通量实验在脂质互作发现中的局限。

## 方法

- protein descriptors/PLM与classifier。

## 数据与基准

- known lipid-binding/nonbinding proteins。

## 比较基线

- homology/features。

## 结果证据

- 论文报告候选；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 负样本/annotation缺失，候选需实验。

## 仍未知

- SLiPP 在依赖寡聚化形成口袋的脂质结合蛋白上表现如何仍未直接验证。
- 对类固醇和 heme 相关误报的真实规模，在其他蛋白组中尚不清楚。
- ADCK5 具体结合的脂质分子种类仍未完全确定。

## Pi 结构化证据摘录

- **baseline：** 与 LIBP-Pred、MBPpred、DisoLipPred 相比，SLiPP 的核心差异是先定位 discrete pocket，再用结构物化特征分类，而不是仅靠序列、粗分段或无序区概率。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.2]
- **baseline：** 在算法比较中，Random Forest 优于 SVM、logistic regression、kNN、naive bayes 和 decision tree；作者报告其 F1 为 0.775、AUROC 为 0.980、accuracy 为 99.1%。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.5]
- **baseline：** 作者还指出 AlphaFold 3 虽可做蛋白-配体结构预测，但可用脂质类型有限且 de novo 复杂预测成本高，不适合高通量 proteome mining。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.2]
- **data：** 训练数据由 1006 个 nonlipid-bound PDB、780 个 lipid-bound PDB、240 个 heme-bound PDB 以及 2026 个 PDB 结构产生的 90,232 个 pseudo pockets 组成，对应提取到 3333 个 nLBPs、1981 个 LBPs 和 429 个 heme pockets。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.12]
- **data：** 独立测试集包含 8380 个 pockets，其中 198 个 LBPs、333 个 nLBPs、7849 个 PPs；另有 131 个 apo PDB 结构和 177 个 AlphaFold 模型用于外部验证。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.6]；[doi:10.1021/acs.jcim.5c01076, p.12]
- **data：** 蛋白组预测覆盖 E. coli、S. cerevisiae 和 H. sapiens；其中 human proteome 有 20406 个蛋白，7346 个因长度或 pLDDT 被过滤。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.7]；[doi:10.1021/acs.jcim.5c01076, p.8]；[doi:10.1021/acs.jcim.5c01076, p.13]
- **data：** ADCK5 的实验构建体为 residues 68–580，结合的脂质来源是 brain total lipid extract (BTL)。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.9]；[doi:10.1021/acs.jcim.5c01076, p.13]；[doi:10.1021/acs.jcim.5c01076, p.14]
- **declared_resources：** 论文声明代码与使用说明托管于 GitHub: https://github.com/dassamalab/SLiPP_2024，并提供 Supporting Files 1–3 作为训练与验证数据。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.14]
- **declared_resources：** 实现依赖 fpocket/biobb_vs、scikit-learn、SignalP 6.0、AlphaFold database、UniProt、ShinyGO、PDB 等公开资源。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.12]；[doi:10.1021/acs.jcim.5c01076, p.13]；[doi:10.1021/acs.jcim.5c01076, p.14]
- **limitations：** fpocket 的 α-sphere pocket detection 可能把连续大口袋切碎，导致 apo/AlphaFold 集上的 sensitivity 下降。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.7]；[doi:10.1021/acs.jcim.5c01076, p.11]
- **limitations：** 模型主要在单体 AlphaFold 结构上运行，因而难以覆盖依赖寡聚化或表面结合形成的脂质互作位点。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.11]
- **limitations：** 模型可能把 steroid-binding proteins 或 heme-binding pockets 误判为 LBP，因为这些口袋在 hydrophobicity 特征上与 lipid pockets 重叠。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.11]；[doi:10.1021/acs.jcim.5c01076, p.12]
- **limitations：** ADCK5 的具体结合脂质仍未被完全鉴定，作者仅确认其与 BTL 中的某些 species 相关。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.10]
- **method：** 从 PDB 中整理 lipid、nonlipid 和 heme 结合结构，并用 dpocket/fpocket 提取 17 个口袋描述符，另将 fpocket 产生的未配体口袋定义为 pseudo pockets 参与建模。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.5]；[doi:10.1021/acs.jcim.5c01076, p.12]
- **method：** 比较了 SVM、logistic regression、kNN、naive bayes、decision tree 与 Random Forest，最后以 Random Forest 作为主分类器，并保持 sklearn 默认超参数。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.5]；[doi:10.1021/acs.jcim.5c01076, p.6]；[doi:10.1021/acs.jcim.5c01076, p.12]
- **method：** 在 proteome 预测时，作者先移除 signal peptide，再过滤掉少于 100 aa 和整体 pLDDT 低于 70 的 AlphaFold 模型，然后把 fpocket 口袋送入分类器，取最高口袋分数作为蛋白分数。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.7]；[doi:10.1021/acs.jcim.5c01076, p.13]
- **method：** 对 ADCK5 进行了表达纯化、protein lipid overlay、nanoDSF、MST、ATPase assay、lipid pulldown 和 untargeted lipidomics 等实验验证。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.8]；[doi:10.1021/acs.jcim.5c01076, p.9]；[doi:10.1021/acs.jcim.5c01076, p.10]；[doi:10.1021/acs.jcim.5c01076, p.13]；[doi:10.1021/acs.jcim.5c01076, p.14]
- **results：** 在独立测试集中，SLiPP 达到 AUROC 0.970、accuracy 96.8%、F1 0.869、sensitivity 81.8% 和 precision 92.6%。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.6]
- **results：** 在 apo PDB 与 AlphaFold 验证集中，AUROC 分别为 0.828 和 0.851，F1 分别为 0.726 和 0.643，主要问题是 sensitivity 明显下降。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.6]；[doi:10.1021/acs.jcim.5c01076, p.7]
- **results：** 蛋白组预测得到 E. coli 159、yeast 273、human 935 个候选，且 GO 富集主要集中在 lipid transport、lipid metabolism 和 biosynthesis。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.7]；[doi:10.1021/acs.jcim.5c01076, p.8]
- **results：** ADCK5 被实验证明可结合 BTL，且 BTL 使其 basal ATPase 活性约提高 1.7-fold；pulldown lipidomics 还富集到 diglycerides 和 phosphatidyl serine 相关特征。
  - 证据：[doi:10.1021/acs.jcim.5c01076, p.9]；[doi:10.1021/acs.jcim.5c01076, p.10]

## 页码证据

- [doi:10.1021/acs.jcim.5c01076, p.1]
- [doi:10.1021/acs.jcim.5c01076, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
