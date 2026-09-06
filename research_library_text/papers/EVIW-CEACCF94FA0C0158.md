# Optimization of drug-target affinity prediction methods through feature processing schemes

- **论文 ID：** `EVIW-CEACCF94FA0C0158`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2023 Oct 9
- **DOI：** [10.1093/bioinformatics/btad615](https://doi.org/10.1093/bioinformatics/btad615)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称先构造 SAFs 和 AAFs，再用多种特征选择/降维方法与 SHAP、IFS 进行优化，最终结合 MART learning to rank 建立一个更高性能、可解释的 DTA 预测流程。

## 创新边界

`新意主要在既有特征处理方法的组合、筛选与系统比较，不在新的 DTA 基础算法或候选生成机制。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在 drug-target affinity (DTA) 预测中，如何通过特征工程压缩冗余、抑制噪声，并同时提升预测精度、鲁棒性和可解释性。

## 方法

- 构造self-associated/adjacent-associated特征，比较树模型选择、XGBoost/LightGBM重要度与降维，再训练DTA ranking。

## 数据与基准

- Davis/KIBA类两个常用DTA数据集及多排列重复实验。

## 比较基线

- 无特征优化、PCA/降维、多种filter/wrapper/tree选择和DTA学习器。

## 结果证据

- 论文报告regression-tree feature selection最有利于性能与稳健性；为计算方法比较。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 结论依赖手工特征和两个数据集；随机拆分/feature leakage和新target泛化未充分验证。

## 仍未知

- 冻结证据未核验仓库许可与可复现性。
- 论文未展示独立外部测试集之外的更广泛泛化验证。
- SAF/AAF 构造阈值在更多数据集上的稳定性仍不明确。

## Pi 结构化证据摘录

- **baseline：** 外部对比基线是 Gen 与 Graph，分别代表手工分子描述符/序列特征和 GraphDTA 风格特征。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.5]
- **baseline：** 内部基线还包括 all、VT、PCA、Lasso、ivis，以及 XGB/Light/Cat 的 SFM 与 SHAP 两套选特征结果。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.5]；[doi:10.1093/bioinformatics/btad615, p.6]
- **data：** 实验使用 Davis 与 KIBA 两个常用基准集；Davis 含 442 个蛋白和 68 个药物，KIBA 含 229 个蛋白和 2111 个药物。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.4]
- **data：** 作者在 S1（known targets/new drugs）与 S2（known drugs/new targets）两种查询设定下评估，指标是 CI、MSE 和 r2m。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.4]
- **data：** 比较输入包括 Gen、Graph，以及 all、VT、PCA、Lasso 和 ivis 等特征方案。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.5]
- **declared_resources：** 论文在 Availability and implementation 中明确给出 GitHub 仓库 FS_DTA。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.1]
- **declared_resources：** Funding 声明列出 NSFC 62101094、62131004、62250028 和 Quzhou 2022D040。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.9]
- **limitations：** 作者自己也指出，初始 SAF/AAF 会因重叠邻居和阈值筛选而带入重复、冗余甚至无效信息，部分 SAF 几乎不贡献性能。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.7]
- **limitations：** ivis 路线表现明显较差，尤其在 KIBA 上 CI 约 0.75，r2m 低于 0.5，说明该降维策略不够稳。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.5]
- **limitations：** 结论把扩展 protein-protein interaction、drug-disease association 和更高级的特征融合列为未来工作，显示当前方案仍受特征覆盖面限制。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.9]
- **method：** 先依据 drug-drug similarity、drug-drug sharing、protein-protein similarity、protein-protein sharing 以及 DTA matrix 构造 SAFs 和 AAFs。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.2]
- **method：** 再对初始特征做 VT、PCA、Lasso、XGBoost、LightGBM、CatBoost 和 ivis 处理，并通过 grid search 设定参数。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.3]；[doi:10.1093/bioinformatics/btad615, p.5]
- **method：** 用 SHAP 计算特征重要性，并结合 IFS 在不同维度上寻找稳定的高质量子集。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.2]；[doi:10.1093/bioinformatics/btad615, p.6]
- **method：** 把优化后的特征输入 MART 这种 learning to rank 模型，在 S1 与 S2 两种 DTA 设定下训练和评估。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.1]；[doi:10.1093/bioinformatics/btad615, p.4]
- **results：** 在 Davis 与 KIBA 上，作者方法整体优于 Gen 和 Graph 基线，说明 SAF/AAF 比简单描述符、序列或图特征更有效。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.5]；[doi:10.1093/bioinformatics/btad615, p.6]
- **results：** XGBoost、LightGBM、CatBoost 这三类树模型在低维子集上最稳，且它们的内建重要性与 SHAP 排名几乎一致。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.6]
- **results：** 按 SHAP+IFS 选出的 top 150 features 基本接近全特征性能，而 top 20 features 对性能变化最敏感。
  - 证据：[doi:10.1093/bioinformatics/btad615, p.1]；[doi:10.1093/bioinformatics/btad615, p.6]；[doi:10.1093/bioinformatics/btad615, p.8]

## 页码证据

- [doi:10.1093/bioinformatics/btad615, p.1]
- [doi:10.1093/bioinformatics/btad615, p.4]
- [doi:10.1093/bioinformatics/btad615, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
