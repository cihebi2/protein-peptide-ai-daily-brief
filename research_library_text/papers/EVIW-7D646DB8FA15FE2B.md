# Machine learning predictor PSPire screens for phase-separating proteins lacking intrinsically disordered regions

- **论文 ID：** `EVIW-7D646DB8FA15FE2B`
- **期刊 / 来源：** Nat Commun
- **发表时间：** 2024 Mar 8
- **DOI：** [10.1038/s41467-024-46445-y](https://doi.org/10.1038/s41467-024-46445-y)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `结构预测`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

论文提出 PSPire：把 AlphaFold 结构导出的 SSUP 与 sticker 特征、IDR 相关特征和 Phos frequency 结合进 XGBoost 分类器，以更准确预测并筛选 ID-PSPs 和 noID-PSPs，同时用 HeLa 细胞与体外实验验证若干候选蛋白的相分离能力。

## 创新边界

`新意主要在把结构层面的 SSUP/sticker 特征与序列层面的 IDR 特征联合用于 PSP 筛选；AlphaFold、DSSP、PSAIA、XGBoost、SHAP 等都属于现有工具组合，不是全新模型范式。`。这不是全球首创性检索或独立复现结论。

## 研究问题

现有 phase-separation protein 预测器对缺乏 intrinsically disordered regions (IDRs) 的 PSPs 识别明显偏弱，导致难以在全蛋白组中可靠筛选候选 phase-separating proteins。

## 方法

- 从序列、AlphaFold结构和表面/相互作用特征训练PSP classifier，重点noIDR子集。

## 数据与基准

- 多套phase-separating/non-PSP数据。

## 比较基线

- IDR-centric和其他PSP predictor。

## 结果证据

- 论文报告noIDR-PSP识别显著优于现有预测器；为计算screening。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- IDR由AlphaFold pLDDT近似，phase separation强依赖浓度/环境，标签异质。

## 仍未知

- 未见独立外部 prior-art 证据，global novelty 不能确认。
- 未见完整独立复现或更大规模外部队列的结果。
- HeLa 与少数候选蛋白的验证支持力有限，泛化到所有 PSPs 仍未知。

## Pi 结构化证据摘录

- **baseline：** 与 PhaSePred、PSPredictor、PSAP、FuzDrop、PSPer、PScore、catGRANULE、PLAAC 相比，PSPire 主要提升了 noID-PSPs 的识别能力。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.2]；[doi:10.1038/s41467-024-46445-y, p.6]
- **baseline：** 作者报告当前方法在 noID-PSPs 上的最佳基线仅 AUROC 0.68、AUPRC 0.08，而 PSPire 达到 0.84/0.24。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.2]；[doi:10.1038/s41467-024-46445-y, p.6]
- **data：** 正样本来自 PhaSePred 开发数据集及 LLPSDB、PhaSePro、PhaSepDB、DrLLPS 中经实验或 MLO 证据支持的 PSPs；过滤后正训练集 259、正测试集 258，负训练集 8323、负测试集 1961。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.9]
- **data：** 作者另外收集了 5 个 human MLO datasets：G3BP1 proximity labeling、DACT1-particulate proteome、RNAgranuleDB Tier1、PhaSepDB low/high throughput MLO、DrLLPS MLO。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.9]
- **data：** 候选验证使用 HeLa cells、GFP-tagged constructs，以及纯化的 RAB31、S100A7、SERPINB4、PGM1 蛋白与其荧光标记版本。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.10]；[doi:10.1038/s41467-024-46445-y, p.11]
- **declared_resources：** Human proteome AlphaFold PDB files (UP000005640) 与公共 phase-separation 数据库（LLPSDB、PhaSePro、PhaSepDB、DrLLPS）被明确作为数据来源。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.9]；[doi:10.1038/s41467-024-46445-y, p.11]
- **declared_resources：** PSPire 源码公开在 https://github.com/TongjiZhanglab/PSPire，且作者声明已发布预计算的 PS scores、SSUP 与 sticker positions。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.11]
- **limitations：** 模型依赖 AlphaFold 预测结构；如果预测结构与 native structure 有偏差，SSUP 和 sticker 特征会随之受影响。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.9]
- **limitations：** ID-PSP/noID-PSP 的标签依赖是否存在 IDRs，但像 JAK1 这类更依赖 modular domains 的蛋白会被默认特征低估；作者只提供了将 IDR-related features 置空的选项。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.9]
- **limitations：** 模型不用于区分 driver/passenger，也不能仅凭分数判断单组分或多组分 droplet。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.9]
- **method：** 作者先用 AlphaFold 预测结构、pLDDT 和 DSSP 划分 IDRs，再把非 IDR 中 RSA>25% 的残基定义为 structured superficial regions (SSUP)。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.9]
- **method：** charged sticker 的定义来自 SSUP 内残基的 net charge index，并通过 hierarchical clustering 聚类；距离阈值在 10–20 Å 中筛到 14 Å。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.3]；[doi:10.1038/s41467-024-46445-y, p.9]
- **method：** 作者把 PSAP/PhaSePred 的 residue-level 特征分别在 IDR 和 SSUP 上重算，并加入 Phos frequency，最终用 XGBoost 训练 PSPire；human 版本保留 Phos，其它物种版本不含 Phos。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.4]；[doi:10.1038/s41467-024-46445-y, p.10]
- **method：** 训练过程使用 5-fold cross-validation、Optuna 调参、inverse-frequency sample weights，以及 10 轮负样本子采样平均分数来缓解类别不平衡。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.10]
- **results：** 在独立测试集上，PSPire 对 ID-PSPs 的 AUROC/AUPRC 为 0.86/0.51，对 noID-PSPs 为 0.84/0.24。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.6]
- **results：** 在 5 个 human MLO datasets 上，PSPire 对 ID-PSPs 的表现与最优现有工具相当，但对 noID-PSPs 明显更好。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.6]
- **results：** 作者筛出 74 个高置信 ID-PSP 候选、100 个高置信 noID-PSP 候选、580 个中等置信 ID-PSP 候选和 395 个中等置信 noID-PSP 候选；其中 9/11 选中候选在细胞内形成 condensates，PGM1、SERPINB4、RAB31、S100A7 还能在体外 phase separate，FRAP 与高盐实验支持其凝聚特性。
  - 证据：[doi:10.1038/s41467-024-46445-y, p.7]；[doi:10.1038/s41467-024-46445-y, p.8]

## 页码证据

- [doi:10.1038/s41467-024-46445-y, p.1]
- [doi:10.1038/s41467-024-46445-y, p.2]
- [doi:10.1038/s41467-024-46445-y, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
