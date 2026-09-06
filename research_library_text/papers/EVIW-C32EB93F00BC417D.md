# A Comparative Study of Deep Learning and Classical Modeling Approaches for Protein–Ligand Binding Pose and Affinity Prediction in Coronavirus Main Proteases

- **论文 ID：** `EVIW-C32EB93F00BC417D`
- **期刊 / 来源：** J Chem Inf Model
- **发表时间：** 2025 Dec 22
- **DOI：** [10.1021/acs.jcim.5c02481](https://doi.org/10.1021/acs.jcim.5c02481)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `结构预测`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称对 ASAP Antiviral Challenge 2025 的 pose prediction 与 potency prediction 进行回顾性系统比较，横向评估 docking、ligand superposition 和 deep learning-based modeling，并用 LRIP-SF 与 GSA 解释 pose 质量、预测精度和关键残基贡献。

## 创新边界

`创新边界主要是 benchmark 与 workflow integration，而不是新药物生成或新 wet-lab 结果。`。这不是全球首创性检索或独立复现结论。

## 研究问题

比较 SARS-CoV-2 与 MERS-CoV main protease 的蛋白-配体结合姿势预测与亲和力预测方法，并评估不同 pose 生成策略对下游 affinity 预测质量的影响。

## 方法

- 用Glide/Vina、FlexS、AlphaFold3、Boltz-2、DiffDock和Gnina生成pose；基于pose计算MM-GBSA残基相互作用特征并训练LRIP-SF。

## 数据与基准

- 使用ASAP Antiviral Challenge 2025的SARS-CoV-2与MERS-CoV Mpro结构、pose和实验抑制效力数据。

## 比较基线

- Glide、AutoDock Vina、FlexS、AlphaFold3、Boltz-2、DiffDock、Gnina及不同效力评分。

## 结果证据

- 论文报告AlphaFold3 pose成功率88.1%、平均LRMSD 1.12 Å；其pose配合LRIP-SF时，MERS和SARS-CoV-2的pIC50 MAE分别0.606和0.724。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- AlphaFold3计算成本高；部分方法无法生成有效pose或产生化学无效pose，且部分测试配体缺实验效力。

## 仍未知

- 未见独立前瞻性外部验证集。
- 仅见 Zenodo DOI，未见可直接克隆的独立代码仓库。
- 部分测试样本因无效姿势、缺失 potency 标注或对映异构体冲突被剔除，可能影响可比性。

## Pi 结构化证据摘录

- **baseline：** pose 基线主要是传统 docking 与 template-based 方法：Glide、AutoDock Vina、FlexS、DiffDock、Boltz-2 和 Gnina；Gnina 还比较了 rigid/flexible receptor 与 minimization 组合。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.2]；[doi:10.1021/acs.jcim.5c02481, p.3]；[doi:10.1021/acs.jcim.5c02481, p.4]；[doi:10.1021/acs.jcim.5c02481, p.5]
- **baseline：** 在 LRIP-SF 内部，作者用 7 种 ML 算法做基线比较，最终选择 GBDT 作为测试集预测器。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.4]；[doi:10.1021/acs.jcim.5c02481, p.6]
- **baseline：** 作者在讨论中还把本工作与挑战赛中其他高分提交进行了对照，例如 MolE、MolGPS 和 ensemble ML 方案，用来说明自己的 MAE 大致仍接近当次比赛的前沿水平。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.10]；[doi:10.1021/acs.jcim.5c02481, p.11]
- **data：** pose 数据集来自 ASAP Antiviral Ligand Pose Prediction Challenge 2025，共 965 个 protein-ligand complexes，其中训练集 770 个为 SARS-CoV-2 Mpro，测试集为 98 个 SARS-CoV-2 Mpro 与 97 个 MERS-CoV Mpro。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.2]
- **data：** potency 数据集来自 ASAP Antiviral Potency Prediction Challenge 2025，每个靶点包含 1031 个训练分子与 297 个测试分子；作者又过滤掉 pIC50 < 4 的样本，最终训练集中保留 837 个 MERS-CoV 与 842 个 SARS-CoV-2 配体。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.4]
- **data：** 测试集配体最初以 CXSMILES 提供，作者用 Open Babel 生成 3D 构象并在建模前做了化学有效性检查。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.2]；[doi:10.1021/acs.jcim.5c02481, p.4]
- **declared_resources：** 数据声明为 ASAP Discovery Consortium 提供的公开数据集，作者给出 Polaris 组织页面作为获取入口。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.11]
- **declared_resources：** 作者声明 LRIP-SF 源码已存放到 Zenodo DOI 10.5281/zenodo.16761312，并使用 AMBER 24 和 Python3 完成最小化、分解、分析与建模。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.11]
- **limitations：** AlphaFold3 与 Boltz-2 的计算成本较高，作者明确指出这会限制其在大规模 virtual screening 中的实用性。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.10]
- **limitations：** FlexS 依赖模板质量且不显式考虑 receptor 环境；当只用 reference ligand 作模板时，success rate 下降到 22.5%，平均 RMSD 为 3.395 Å。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.10]
- **limitations：** 作者也承认 AlphaFold3 的 internal ranking score 与实验 potency 相关性很弱，且若干测试样本因无效 pose、缺失标签或对映异构体冲突被剔除。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.10]；[doi:10.1021/acs.jcim.5c02481, p.6]
- **method：** 在 pose prediction 中，作者比较了 Glide、AutoDock Vina、FlexS、AlphaFold3、Boltz-2、DiffDock 和 Gnina，并用同一挑战数据和参考复合物进行统一评估。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.2]；[doi:10.1021/acs.jcim.5c02481, p.3]；[doi:10.1021/acs.jcim.5c02481, p.4]
- **method：** 在 potency prediction 中，作者构建了 LRIP-SF：先做 pose generation，再做 GBSA 隐式溶剂最小化与 ligand-residue free energy decomposition，最后用多种 ML 算法训练回归模型。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.4]
- **method：** 作者对 Lasso、Bayesian regression、SVR、RF、Adaboost、GBDT 和 MLP 做 bootstrap 比较，并以 RMSE、MAE、Pearson R、R2、p-value、TAU 和 PI 选出最佳模型。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.4]
- **method：** 为解释预测结果，作者还做了 global sensitivity analysis，并将 Pearson 相关系数大于 0.85 的残基合并为特征组。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.4]
- **results：** 在 pose prediction 中，AlphaFold3 表现最佳，success rate 为 88.1% 且平均 LRMSD 为 1.122 Å；Boltz-2 紧随其后，分别为 84.2% 和 1.251 Å。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.5]；[doi:10.1021/acs.jcim.5c02481, p.6]
- **results：** 在 LRIP-SF 下游亲和力预测中，AlphaFold3 生成的 pose 在两个靶点上都给出了最好的误差：MERS-CoV Mpro 的 MAE/RMSE 为 0.606/0.813，SARS-CoV-2 Mpro 为 0.724/0.894。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.6]；[doi:10.1021/acs.jcim.5c02481, p.7]；[doi:10.1021/acs.jcim.5c02481, p.8]
- **results：** GSA 给出的关键残基/残基组包括 SARS-CoV-2 Mpro 的 H41、T135、Q19−N119、A191、I43−C44−T45−D48−M49−H164，以及 MERS-CoV Mpro 的 C148、P39−G177、F143、Q19、P52。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.9]
- **results：** 在分类区分能力上，多数方法的 ROC-AUC 都高于 0.8；作者报告 MERS-CoV 上 Boltz-2-Internal AUC 最高为 0.883，SARS-CoV-2 上 Boltz-2-Internal 最高为 0.955。
  - 证据：[doi:10.1021/acs.jcim.5c02481, p.8]

## 页码证据

- [doi:10.1021/acs.jcim.5c02481, p.10]
- [doi:10.1021/acs.jcim.5c02481, p.1]
- [doi:10.1021/acs.jcim.5c02481, p.6]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
