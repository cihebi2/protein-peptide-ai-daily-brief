# Predicting drug‐perturbed transcriptional responses using multi‐conditional diffusion transformer

- **论文 ID：** `EVIW-E395FE01ADC316B7`
- **期刊 / 来源：** Quant Biol
- **发表时间：** 2025 Sep 21
- **DOI：** [10.1002/qub2.70016](https://doi.org/10.1002/qub2.70016)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `扩散/生成`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 PertDiT：一个将文本药物表示、扩散模型和 Transformer 融合的多条件生成框架，并设计 CrossDiT/CatCrossDiT 两种结构用于转录组预测。

## 创新边界

`创新点限于药物扰动转录组生成与预测，不是药物候选设计本身。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在缺少昂贵湿实验的情况下，基于药物文本和预扰动转录组准确预测药物扰动后的基因表达响应。

## 方法

- diffusion transformer联合pre-state、drug text和条件编码，去噪重建post-perturbation gene expression。

## 数据与基准

- 公开pre/post drug perturbation transcriptome。

## 比较基线

- 既有perturbation predictor和不同condition fusion。

## 结果证据

- 论文报告多指标和严格split上优于现有方法；为计算重建。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- gene数有限，drug metadata不足；作者计划FlashAttention/Mamba和更多机制标签。

## 仍未知

- 冻结证据中未见独立外部复现或第三方基准验证。
- 论文声明了 GitHub 仓库，但本任务未核验仓库是否可直接运行。
- 该方法是否能提升真实临床终点预测，冻结证据中尚未证明。

## Pi 结构化证据摘录

- **baseline：** 论文把 PRnet 作为主要 SOTA 对照，并与 ChemCPA 比较；在补充公平比较中又只与 PRnet 对齐，因为文中称 PRnet 已优于 ChemCPA。
  - 证据：[doi:10.1002/qub2.70016, p.2]；[doi:10.1002/qub2.70016, p.3]
- **baseline：** 结构消融还设置 AdaDiT、AdaDiT-RDKit、CatonlyCrossDiT 等变体，用于拆分评估 text embedding、cross-attention 与 self-attention 的贡献。
  - 证据：[doi:10.1002/qub2.70016, p.5]；[doi:10.1002/qub2.70016, p.6]
- **data：** 主要数据集是 L1000；预处理后得到 883,269 条观测，覆盖 17,202 个 compounds、82 个 cell lines 和 978 个 landmark genes。
  - 证据：[doi:10.1002/qub2.70016, p.7]
- **data：** 作者除了沿用 PRnet 风格的随机、未见 drug、未见 cell line 三类五折切分外，还提出 Drug_unseen、Cell_line_unseen、Both_unseen 三个测试集；并进一步扩展到 lung、kidney、pancreas 三个 organ-specific 测试集。
  - 证据：[doi:10.1002/qub2.70016, p.2]；[doi:10.1002/qub2.70016, p.4]；[doi:10.1002/qub2.70016, p.7]
- **declared_resources：** 数据可用性声明称 PertDiT 的 code 和 data 均可在 GitHub 仓库 wangkekekeke/PertDiT.git 获取。
  - 证据：[doi:10.1002/qub2.70016, p.10]
- **declared_resources：** 研究得到 NSFC 62133006、92268104 以及国家重点研发计划 2020YFA0712403、2021YFF1200901 的资助。
  - 证据：[doi:10.1002/qub2.70016, p.1]；[doi:10.1002/qub2.70016, p.10]
- **limitations：** 作者明确指出推理速度仍可通过 EDM、consistency models 或其他更快采样策略进一步提升。
  - 证据：[doi:10.1002/qub2.70016, p.7]
- **limitations：** 作者也承认可解释性仍有限，因为多层结构、diffusion 预测噪声而非直接 transcriptome，以及 token 与 drug structure 之间缺少显式连接。
  - 证据：[doi:10.1002/qub2.70016, p.7]
- **limitations：** 论文还指出当前 gene number 受限，并计划结合 flash attention、Mamba 以及扩展到 single-cell perturbation data。
  - 证据：[doi:10.1002/qub2.70016, p.7]
- **method：** PertDiT 将 post-perturbation transcriptome 建模为多条件 DDPM，在给定 pre-perturbation transcriptome 与 perturbation condition 的情况下逐步去噪生成输出。
  - 证据：[doi:10.1002/qub2.70016, p.2]；[doi:10.1002/qub2.70016, p.8]；[doi:10.1002/qub2.70016, p.9]
- **method：** 药物扰动先由 SMILES 生成自然语言描述，再通过 MolT5 与 Linkbert 构成 text embedding，并把 dosage prompt 拼接进同一表示。
  - 证据：[doi:10.1002/qub2.70016, p.2]；[doi:10.1002/qub2.70016, p.9]
- **method：** 作者设计 CrossDiT 与 CatCrossDiT 两种 transformer 结构，并用 R²、PCC(ln FC) 及五种分组策略构成 10 个评价指标，同时还提供两套数据切分方案。
  - 证据：[doi:10.1002/qub2.70016, p.2]；[doi:10.1002/qub2.70016, p.7]；[doi:10.1002/qub2.70016, p.8]
- **results：** 在自定义切分以及 PRnet 的随机/未见 drug/未见 cell line 设定下，CrossDiT 与 CatCrossDiT 在 10 个指标上总体都优于 PRnet 和 ChemCPA。
  - 证据：[doi:10.1002/qub2.70016, p.3]
- **results：** CatCrossDiT 更偏向提升 unseen cell line 与更细粒度分组下的 transcriptome reconstruction，而 CrossDiT 更偏向提升 unseen drugs 与更粗粒度分组下的 perturbation-induced change prediction。
  - 证据：[doi:10.1002/qub2.70016, p.3]；[doi:10.1002/qub2.70016, p.4]
- **results：** 器官级扩展实验表明，该方法在 lung、kidney、pancreas 三个测试集中都优于 PRnet；在 Lapatinib 与 DEG case study 中也取得更高的 PCC(ln FC) 表现。
  - 证据：[doi:10.1002/qub2.70016, p.4]；[doi:10.1002/qub2.70016, p.6]

## 页码证据

- [doi:10.1002/qub2.70016, p.1]
- [doi:10.1002/qub2.70016, p.3]
- [doi:10.1002/qub2.70016, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
