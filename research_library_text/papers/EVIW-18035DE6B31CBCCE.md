# Nature’s defense against emerging neurodegenerative threats: Dynamic simulation, PCA, DCCM identified potential plant-based antiviral lead targeting borna disease virus nucleoprotein

- **论文 ID：** `EVIW-18035DE6B31CBCCE`
- **期刊 / 来源：** PLoS One
- **发表时间：** 2024 Dec 30
- **DOI：** [10.1371/journal.pone.0310802](https://doi.org/10.1371/journal.pone.0310802)
- **范围标签：** `Pi 已解析` / `背景资料` / `论文声明资源` / `扩散/生成`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称通过整合 molecular docking、MM-GBSA、SwissADME、ProTox-II、100 ns MD、PCA 与 DCCM，从 IMPPAT 的 1940 个 unique phytochemicals 中识别出来自 Mangifera indica 的 CID 20871246 (3,4-Dihydroxy-5-oxocyclohex-3-ene-1-carboxylic acid) 作为最有前景、最稳定的 BDV nucleoprotein 先导，并认为它可能抑制 BDV replication 的初始阶段。

## 创新边界

`新意主要在针对 BDV nucleoprotein 的候选排序与多指标一致性验证；方法本身是常规 CADD 管线，没有看到新算法、新模型或湿实验证据。`。这不是全球首创性检索或独立复现结论。

## 研究问题

该文要解决的是：面对缺乏有效治疗的 Borna disease virus (BDV) nucleoprotein 靶点，能否从印度药用植物来源的 phytochemicals 中筛出可作为抗病毒先导的候选分子，并用分子对接、动力学与药代毒性预测给出优先级。

## 方法

- 对PDB 1N93虚拟筛选phytochemical并模拟稳定性/相关运动。

## 数据与基准

- 植物化合物库和BDV nucleoprotein结构。

## 比较基线

- 参考配体与不同植物候选。

## 结果证据

- 论文提出若干计算候选；作者明确要求进一步实验证实compound-protein interaction。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 全部关键效力为in silico，资源约束限制采样；标准应用不形成新模型。

## 仍未知

- 缺少 in vitro / in vivo 结果，真实抗病毒活性未被验证。
- 主要 lead CID 20871246 的脑部可达性未解决，BBB 预测为 No。
- 不同评分体系对候选排序不一致，最终优先级依赖综合判断。
- 文中未提供可直接复用的代码仓库或脚本链接。

## Pi 结构化证据摘录

- **baseline：** Favipiravir (CID 492405) 是全文唯一明确设定的 control ligand，作者用它来比较 docking、MM-GBSA、MD 与药代毒性指标。
  - 证据：[doi:10.1371/journal.pone.0310802, p.5]；[doi:10.1371/journal.pone.0310802, p.7]；[doi:10.1371/journal.pone.0310802, p.9]
- **baseline：** 在 MD 分析中，apoprotein 1N93 也被作为额外参照，作者用其对比候选复合物的 PCA 与 DCCM 行为。
  - 证据：[doi:10.1371/journal.pone.0310802, p.12]；[doi:10.1371/journal.pone.0310802, p.13]；[doi:10.1371/journal.pone.0310802, p.14]
- **baseline：** 相对 Favipiravir，多个候选在 docking 和部分 MD 指标上更优，但不同指标的排序不完全一致，因此作者采用了综合判读而非单一分数定论。
  - 证据：[doi:10.1371/journal.pone.0310802, p.6]；[doi:10.1371/journal.pone.0310802, p.7]；[doi:10.1371/journal.pone.0310802, p.9]；[doi:10.1371/journal.pone.0310802, p.13]；[doi:10.1371/journal.pone.0310802, p.18]
- **data：** 靶标结构是 BDV nucleoprotein 1N93，单链 A、375 aa，分辨率 1.76 Å。
  - 证据：[doi:10.1371/journal.pone.0310802, p.4]
- **data：** 化合物数据来自 IMPPAT 的 36 种植物和 8617 个原始化合物，研究中保留了 1940 个去重后的候选分子。
  - 证据：[doi:10.1371/journal.pone.0310802, p.4]；[doi:10.1371/journal.pone.0310802, p.5]
- **data：** 对照分子是 PubChem CID 492405 的 Favipiravir，作者还在补充材料中提供了 docking、MM-GBSA、RMSD、RMSF 与 ligand property 等表格。
  - 证据：[doi:10.1371/journal.pone.0310802, p.5]；[doi:10.1371/journal.pone.0310802, p.19]
- **declared_resources：** 作者声明数据与支持信息主要来自 RCSB PDB 的 1N93、PubChem 的 Favipiravir 以及 IMPPAT 的植物化合物库。
  - 证据：[doi:10.1371/journal.pone.0310802, p.4]；[doi:10.1371/journal.pone.0310802, p.5]；[doi:10.1371/journal.pone.0310802, p.19]
- **declared_resources：** 计算资源与软件栈包括 Schrödinger 2020-3、Glide、Maestro、Prime MMGBSA、Desmond、OPLS3e force field，以及 Bio3D。
  - 证据：[doi:10.1371/journal.pone.0310802, p.4]；[doi:10.1371/journal.pone.0310802, p.5]；[doi:10.1371/journal.pone.0310802, p.6]；[doi:10.1371/journal.pone.0310802, p.12]；[doi:10.1371/journal.pone.0310802, p.13]
- **declared_resources：** 药代与毒性评估使用了 SwissADME、ProTox-II，补充分析还提到 PASS online 用于结构活性关系预测。
  - 证据：[doi:10.1371/journal.pone.0310802, p.5]；[doi:10.1371/journal.pone.0310802, p.8]；[doi:10.1371/journal.pone.0310802, p.18]；[doi:10.1371/journal.pone.0310802, p.19]
- **declared_resources：** 文中明确写出所有相关数据都在正文或 Supporting information 中，且补充文件 S1-S6 覆盖 compound list、docking、MM-GBSA、RMSD、RMSF 和 ligand properties。
  - 证据：[doi:10.1371/journal.pone.0310802, p.1]；[doi:10.1371/journal.pone.0310802, p.19]
- **limitations：** 这是一篇纯 in silico 研究，作者自己也明确指出仍需要 in vitro 和 in vivo 实验来验证复合物-蛋白相互作用与真实抗病毒效力。
  - 证据：[doi:10.1371/journal.pone.0310802, p.17]；[doi:10.1371/journal.pone.0310802, p.19]
- **limitations：** 对于 BDV 这种中枢神经系统相关靶点，主要 lead CID 20871246 的 BBB permeant 预测为 No，脑部递送仍是不确定性。
  - 证据：[doi:10.1371/journal.pone.0310802, p.8]；[doi:10.1371/journal.pone.0310802, p.17]
- **limitations：** 多个评分体系给出的排序并不一致：CID 163114683 在 MM-GBSA 更强，但 CID 20871246 在 MD/PCA/DCCM 更稳，因此最终 lead 判定依赖作者的综合解释，而非单一实验读数。
  - 证据：[doi:10.1371/journal.pone.0310802, p.7]；[doi:10.1371/journal.pone.0310802, p.9]；[doi:10.1371/journal.pone.0310802, p.12]；[doi:10.1371/journal.pone.0310802, p.13]
- **method：** 作者先从 RCSB PDB 获取 BDV nucleoprotein 1N93，并用 Protein Preparation Wizard 去除水分子、异源配体并补全氢原子与侧链。
  - 证据：[doi:10.1371/journal.pone.0310802, p.4]
- **method：** 配体库来自 IMPPAT 的 36 种药用植物，共 8617 个化合物，去重后得到 1940 个 unique phytochemicals；Favipiravir (CID 492405) 被设为 control ligand。
  - 证据：[doi:10.1371/journal.pone.0310802, p.4]；[doi:10.1371/journal.pone.0310802, p.5]
- **method：** 对 1940 个化合物使用 Schrödinger Glide v8.8 进行 standard precision docking，并基于共晶配体活性位点建立 grid；随后用 Prime MMGBSA 计算 post-docking binding free energy。
  - 证据：[doi:10.1371/journal.pone.0310802, p.5]；[doi:10.1371/journal.pone.0310802, p.6]
- **method：** 作者对入选化合物继续做 SwissADME 与 ProTox-II 预测，检查药代性质、Lipinski 规则与毒性端点。
  - 证据：[doi:10.1371/journal.pone.0310802, p.5]；[doi:10.1371/journal.pone.0310802, p.8]；[doi:10.1371/journal.pone.0310802, p.17]
- **method：** 对复合物进行了 100 ns Desmond MD simulation，使用 OPLS3e、SPC water、0.15 M ions、300 K 与 1 atm 的 NPT 条件，并基于轨迹计算 RMSD、RMSF、rGyr、SASA、protein-ligand contact、PCA 和 DCCM。
  - 证据：[doi:10.1371/journal.pone.0310802, p.6]；[doi:10.1371/journal.pone.0310802, p.9]；[doi:10.1371/journal.pone.0310802, p.12]；[doi:10.1371/journal.pone.0310802, p.13]
- **results：** Docking 选出的前三个分子分别是 CID 163114683、CID 20871246 和 CID 243，得分为 -6.244、-6.116 和 -6.07 kcal/mol，均优于 control 的 -5.373 kcal/mol，并与 GLN 161、ARG 165、ILE 145、ILE 162、ILE 149、VAL 229 等残基形成相似结合模式。
  - 证据：[doi:10.1371/journal.pone.0310802, p.6]；[doi:10.1371/journal.pone.0310802, p.7]
- **results：** MM-GBSA 显示四个分子的净结合自由能分别为 -51.21、-13.94、-22.95 和 -18.57 kcal/mol；其中 CID 163114683 的 MM-GBSA 最负，但与后续 MD 稳定性排序并不完全一致。
  - 证据：[doi:10.1371/journal.pone.0310802, p.7]；[doi:10.1371/journal.pone.0310802, p.18]
- **results：** ADME/T 结果表明三条 lead 与 control 都满足 Lipinski；CID 20871246 和 CID 243 的 GI absorption 为 High，而 BBB permeant 只有 CID 243 为 Yes；毒性预测总体偏好，但 CID 243 预测为 active hepatotoxicity，control 预测为 active carcinogenicity。
  - 证据：[doi:10.1371/journal.pone.0310802, p.8]；[doi:10.1371/journal.pone.0310802, p.9]；[doi:10.1371/journal.pone.0310802, p.17]
- **results：** MD、PCA 与 DCCM 综合起来更支持 CID 20871246：其平均 RMSD 约 6.89 Å、rGyr 2.30 Å、SASA 75.25 Å²、ligand RMSD 0.23 Å，PC3 为 5.97%，作者因此将其判定为最稳定、最有前景的复合物。
  - 证据：[doi:10.1371/journal.pone.0310802, p.9]；[doi:10.1371/journal.pone.0310802, p.10]；[doi:10.1371/journal.pone.0310802, p.11]；[doi:10.1371/journal.pone.0310802, p.12]；[doi:10.1371/journal.pone.0310802, p.13]；[doi:10.1371/journal.pone.0310802, p.14]
- **results：** 作者在结论中把 3,4-Dihydroxy-5-oxocyclohex-3-ene-1-carboxylic acid (CID 20871246) 作为最终推荐的 BDV 先导，并声称其可能抑制 viral replication 和 transcription。
  - 证据：[doi:10.1371/journal.pone.0310802, p.18]；[doi:10.1371/journal.pone.0310802, p.19]

## 页码证据

- [doi:10.1371/journal.pone.0310802, p.19]
- [doi:10.1371/journal.pone.0310802, p.1]
- [doi:10.1371/journal.pone.0310802, p.4]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
