# DLTKcat: deep learning-based prediction of temperature-dependent enzyme turnover rates

- **论文 ID：** `EVIW-22CD6AE48DCDB16D`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2024 Jan 6
- **DOI：** [10.1093/bib/bbad506](https://doi.org/10.1093/bib/bbad506)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 DLTKcat：一个把 SMILES、蛋白 3-mer 序列、温度与 1/T 联合输入的 bidirectional attention CPI 模型，声称能更准确预测 temperature-dependent kcat，并可用于突变效应和代谢建模案例。

## 创新边界

`这是用于性质预测与表征分析的方法，不是直接生成或优化候选酶序列；其案例主要是推断性应用，而且作者自己也承认代谢建模的定量精度仍有限。`。这不是全球首创性检索或独立复现结论。

## 研究问题

高质量、带温度条件的 enzyme kcat 数据稀缺，作者希望用深度学习同时建模底物-蛋白相互作用与温度效应，以预测温度依赖的 kcat。

## 方法

- 编码底物SMILES、酶序列和温度，训练compound-protein interaction网络回归kcat。

## 数据与基准

- 数据库kcat记录及相应底物、序列、实验温度；用于proteome-constrained FBA案例。

## 比较基线

- DLKcat及不含温度的CPI模型。

## 结果证据

- 论文称能描述温度依赖，但准确度尚不足以完整预测细胞代谢；FBA能预测25–42°C生长上升，却未预测42–49°C下降。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- pH、离子强度等实验条件仍未建模，数据库标签稀缺且异质。

## 仍未知

- 代码仓库是否可直接复现未核验。
- 模型在更广泛物种与酶类别上的泛化性能未由冻结证据独立证明。
- 过采样与数据清洗对潜在偏差的影响未充分量化。

## Pi 结构化证据摘录

- **baseline：** 作者将 DLTKcat 与 EF-UniKP、Revised UniKP、UniKP 进行比较，并指出这些先前模型在 temperature-dependent kcat 上的 R2 普遍低于 0.5。
  - 证据：[doi:10.1093/bib/bbad506, p.2]；[doi:10.1093/bib/bbad506, p.5]
- **baseline：** temperature-related feature 的 unshuffled vs shuffled 对照构成了内部 baseline，用来验证 temperature 与 1/T 的增益。
  - 证据：[doi:10.1093/bib/bbad506, p.6]
- **data：** 最终训练数据包含 10556 条 WT 记录和 5693 条 mutant 记录，作者只保留同一 SMILES、序列、温度与 kcat 的非冗余条目，并对低温和高温区做了过采样。
  - 证据：[doi:10.1093/bib/bbad506, p.2]
- **data：** LL 与 ST 的 genome-scale metabolic model 分别来自 Flahaut et al. 与 Pastink et al.，实验生长率来自 Chen et al. 与 Vaningelgem et al.，用于温度依赖代谢建模案例。
  - 证据：[doi:10.1093/bib/bbad506, p.4]
- **data：** Pyrococcus furiosus ornithine carbamoyltransferase 的 WT 和突变体温度敏感 kcat 数据来自 Roovers et al.，用于独立的突变效应案例。
  - 证据：[doi:10.1093/bib/bbad506, p.6]
- **declared_resources：** 作者声明使用了 University of Oxford Advanced Research Computing (ARC) facility。
  - 证据：[doi:10.1093/bib/bbad506, p.9]
- **declared_resources：** 论文声明 code 和 data 开放在 https://github.com/SizheQiu/DLTKcat，并依赖 BRENDA、SABIO-RK、PubChem、UniProt 与 COBRApy 等外部资源。
  - 证据：[doi:10.1093/bib/bbad506, p.2]；[doi:10.1093/bib/bbad506, p.3]；[doi:10.1093/bib/bbad506, p.9]
- **limitations：** 作者明确承认，log10-scale RMSE 虽然小于 1，但仍不足以支撑 temperature-sensitive proteome constrained flux balance analysis 做出高精度代谢预测。
  - 证据：[doi:10.1093/bib/bbad506, p.7]
- **limitations：** 在 ST 的 49°C 场景中，模型预测的 kcat 增长与实验上接近生存上限的现象不一致，说明极端温度外推仍不稳。
  - 证据：[doi:10.1093/bib/bbad506, p.7]
- **limitations：** 作者建议加入 pH、金属离子或 enzyme optimal temperature，但也指出这些信息数据稀缺，且 optimal temperature 预测本身的 RMSE 约为 2。
  - 证据：[doi:10.1093/bib/bbad506, p.9]
- **method：** 作者从 SABIO-RK 和 BRENDA 抽取 EC、底物、物种、UniProt ID、温度与 kcat，并用 PubChem 和 UniProt 补全 SMILES 与蛋白序列；去重后保留 4383 条 SABIO-RK 记录和 11866 条 BRENDA 记录。
  - 证据：[doi:10.1093/bib/bbad506, p.2]
- **method：** DLTKcat 用 GAT 编码底物分子图、CNN 编码蛋白 3-mer 序列，再用 bidirectional attention 融合原子与残基表示，并把温度与逆温度拼接后送入全连接层回归 log10(kcat)。
  - 证据：[doi:10.1093/bib/bbad506, p.2]；[doi:10.1093/bib/bbad506, p.3]
- **method：** 模型训练使用 batch size 32、Adam 优化、MSE loss，初始学习率为 0.001，且每 10 个 epoch 学习率衰减 50%。
  - 证据：[doi:10.1093/bib/bbad506, p.3]
- **method：** 代谢案例中，作者把预测 kcat 嵌入 COBRApy 的 proteome constrained flux balance analysis，并结合 LL 与 ST 的 GSMM 和实验生长率数据评估温度敏感代谢响应。
  - 证据：[doi:10.1093/bib/bbad506, p.3]；[doi:10.1093/bib/bbad506, p.4]
- **results：** 在随机测试集上，DLTKcat 将 log10(kcat) 的 RMSE 降到 0.88、R2 提到 0.66，并被作者描述为优于 EF-UniKP、Revised UniKP 和 UniKP。
  - 证据：[doi:10.1093/bib/bbad506, p.1]；[doi:10.1093/bib/bbad506, p.5]
- **results：** 对 3 组多突变酶-底物对，预测误差大约仍在一个数量级内（RMSE 1.0017、MAE 0.7504），且高 attention 位点与部分突变位点有重叠。
  - 证据：[doi:10.1093/bib/bbad506, p.5]
- **results：** 把 temperature 相关特征打乱后，RMSE 和 MAE 上升、R2 下降，说明 temperature 与 1/T 对模型贡献显著。
  - 证据：[doi:10.1093/bib/bbad506, p.6]
- **results：** 在 P. furiosus 案例中，模型达到 RMSE 0.5006、MAE 0.4338，并较好复现高温下更高 kcat 及部分突变增益趋势；但在 LL/ST 代谢案例中只能定性抓住趋势，定量 growth rate 仍偏差较大。
  - 证据：[doi:10.1093/bib/bbad506, p.6]；[doi:10.1093/bib/bbad506, p.7]

## 页码证据

- [doi:10.1093/bib/bbad506, p.1]
- [doi:10.1093/bib/bbad506, p.2]
- [doi:10.1093/bib/bbad506, p.6]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
