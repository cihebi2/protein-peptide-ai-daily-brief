# Transformers enable accurate prediction of acute and chronic chemical toxicity in aquatic organisms

- **论文 ID：** `EVIW-A744CE81A2103EEC`
- **期刊 / 来源：** Sci Adv
- **发表时间：** 2024 Mar 6
- **DOI：** [10.1126/sciadv.adk6669](https://doi.org/10.1126/sciadv.adk6669)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出基于预训练ChemBERTa transformer + DNN 的毒性预测框架，利用SMILES、暴露时长与效应/终点信息直接预测鱼、无脊椎动物和藻类的EC50/EC10，并声称在精度与适用域上优于常用QSAR方法。

## 创新边界

`边界在于这是面向毒性性质预测的迁移学习与多任务回归，不涉及分子生成、候选优化、对接或新的湿实验；创新主要体现在模型组合与毒性预测应用。`。这不是全球首创性检索或独立复现结论。

## 研究问题

现有面向水生生物的QSAR和机器学习毒性预测，普遍受限于准确率、适用域和可覆盖化合物范围，难以替代实验毒性测试并满足监管需求。

## 方法

- SMILES/chemical transformer与multi-task toxicity heads。

## 数据与基准

- aquatic toxicity assays/species。

## 比较基线

- QSAR/ML。

## 结果证据

- 论文报告预测性能；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- species/assay域、环境到人体外推不可。

## 仍未知

- 对其它水生/陆生物种、不同 assay 设计或新型 endpoint 的泛化能力未在冻结证据中直接验证。
- 公开代码与模型链接虽被声明，但本次分析未做联网核验，外部可复现性仍需独立检查。
- 模型在真实监管流程中的校准、阈值选择与不确定性传播效果仍未知。

## Pi 结构化证据摘录

- **baseline：** 主要基线是 ECOSAR v2.2、VEGA v1.1.5 和 T.E.S.T. v5.1.1.0；比较时同时评估 AD 内可预测比例与共同 AD 下的误差，并用相同或可比的 endpoint 设置做对照。
  - 证据：[doi:10.1126/sciadv.adk6669, p.4]；[doi:10.1126/sciadv.adk6669, p.5]；[doi:10.1126/sciadv.adk6669, p.9]
- **baseline：** 对照设计还包括一个最近的 fish toxicity ensemble QSAR（random forest、gradient boosted trees、SVR）；由于其未公开，作者是在论文复现的数据集上进行离线比较。
  - 证据：[doi:10.1126/sciadv.adk6669, p.6]；[doi:10.1126/sciadv.adk6669, p.9]
- **data：** 数据来自 REACH dossiers、ECOTOX 和 EFSA openTox，合并后包含 147,864 条实验 effect concentrations，覆盖约 6,473–6,474 个 unique chemical structures，涉及 fish、aquatic invertebrates 和 algae。
  - 证据：[doi:10.1126/sciadv.adk6669, p.2]；[doi:10.1126/sciadv.adk6669, p.8]
- **data：** 表1给出各数据集的样本量、唯一化学结构数、暴露时长与浓度分布；训练前统一做了 species 名称校验、SMILES canonicalization，并剔除 limit tests 和 >500 mg/L 的值。
  - 证据：[doi:10.1126/sciadv.adk6669, p.3]；[doi:10.1126/sciadv.adk6669, p.8]
- **data：** 终点覆盖并不完全一致：algae 主要是 population toxicity，aquatic invertebrates 与 fish 还包含 mortality、intoxication、development、reproduction、morphology、growth 等多个 endpoint。
  - 证据：[doi:10.1126/sciadv.adk6669, p.3]；[doi:10.1126/sciadv.adk6669, p.8]
- **declared_resources：** 计算资源来自 NAISS 和 SNIC 的高性能算力，训练在 NVIDIA A100-SXM4-40GB GPUs 上完成。
  - 证据：[doi:10.1126/sciadv.adk6669, p.9]；[doi:10.1126/sciadv.adk6669, p.10]
- **declared_resources：** 论文声明 code、data 和 trained models 可在 GitHub/TRIDENT 与 Zenodo 获取；实现基于 PyTorch 1.10.2、ChemBERTa（Huggingface transformers 4.21.1）与 RDKit 等工具。
  - 证据：[doi:10.1126/sciadv.adk6669, p.2]；[doi:10.1126/sciadv.adk6669, p.8]；[doi:10.1126/sciadv.adk6669, p.10]
- **limitations：** 作者明确承认方法高度依赖大规模高质量数据，而 ecotoxicity 数据长期存在标准化不足、元数据不完整、不可访问、需要人工抽取等问题。
  - 证据：[doi:10.1126/sciadv.adk6669, p.7]；[doi:10.1126/sciadv.adk6669, p.8]；[doi:10.1126/sciadv.adk6669, p.10]
- **limitations：** 数据覆盖仍受来源限制：algae 只用 population toxicity，fish 和 aquatic invertebrates 也只覆盖若干 endpoint 与 effect，因此对其它物种或终点的外推仍不确定。
  - 证据：[doi:10.1126/sciadv.adk6669, p.3]；[doi:10.1126/sciadv.adk6669, p.8]
- **limitations：** 论文没有新的湿实验验证，性能结论主要来自内部重复交叉验证和离线 benchmark。
  - 证据：[doi:10.1126/sciadv.adk6669, p.2]；[doi:10.1126/sciadv.adk6669, p.4]；[doi:10.1126/sciadv.adk6669, p.6]
- **method：** 模型由预训练ChemBERTa transformer encoder 和 DNN 组成；SMILES 先经 byte-pair encoding tokenization，再取 CLS 向量并拼接暴露时长、effect 和 endpoint 作为输入，输出 log10 effect concentration。
  - 证据：[doi:10.1126/sciadv.adk6669, p.2]；[doi:10.1126/sciadv.adk6669, p.8]；[doi:10.1126/sciadv.adk6669, p.9]
- **method：** 共训练9个模型：每个 organism group 分别建 EC50、EC10 与合并 EC50/EC10 版本；训练使用 MAE loss、AdamW、linear warmup/decay 和 layer-wise learning rate decay，并通过 Bayesian optimization 选择超参数。
  - 证据：[doi:10.1126/sciadv.adk6669, p.2]；[doi:10.1126/sciadv.adk6669, p.9]
- **method：** 验证采用 10-fold cross-validation repeated 10 times；EC50/EC10 按 chemical structure 切分，合并模型按 effect concentration + structure 切分，并用 CLS cosine similarity 描述结构距离与适用域。
  - 证据：[doi:10.1126/sciadv.adk6669, p.3]；[doi:10.1126/sciadv.adk6669, p.9]
- **results：** 单任务模型的交叉验证中位绝对误差大致为：fish EC50 2.66、aquatic invertebrates EC50 2.82、algae EC50 3.16；EC10 分别为 3.51、3.12、3.99，说明模型能在未见化合物上稳定预测。
  - 证据：[doi:10.1126/sciadv.adk6669, p.3]
- **results：** 合并 EC50/EC10 后性能进一步提升，例如 fish 的 EC50/EC10 中位误差降至 2.04/2.00，且跨效应外推的相关系数可达 0.80、0.83、0.80（fish、aquatic invertebrates、algae）。
  - 证据：[doi:10.1126/sciadv.adk6669, p.3]；[doi:10.1126/sciadv.adk6669, p.4]
- **results：** 与 ECOSAR、VEGA、T.E.S.T. 相比，提议模型的适用域更大，能对评估集全部化学结构给出预测；在共同 AD 子集上，多数鱼类和无脊椎动物场景的误差更低，EC10 的优势尤其明显。
  - 证据：[doi:10.1126/sciadv.adk6669, p.4]；[doi:10.1126/sciadv.adk6669, p.5]；[doi:10.1126/sciadv.adk6669, p.6]；[doi:10.1126/sciadv.adk6669, p.7]
- **results：** 论文还把结果与一个先前的 fish toxicity ensemble QSAR 模型对照，报告本模型在 EC50/EC10 的 RMSE 更低（0.56/0.65 对比 0.83/0.97）。
  - 证据：[doi:10.1126/sciadv.adk6669, p.6]

## 页码证据

- [doi:10.1126/sciadv.adk6669, p.1]
- [doi:10.1126/sciadv.adk6669, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
