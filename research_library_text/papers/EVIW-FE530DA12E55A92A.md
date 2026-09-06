# Programmable protein stabilization with language model-derived peptide guides

- **论文 ID：** `EVIW-FE530DA12E55A92A`
- **期刊 / 来源：** Nature Communications（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1038/s41467-025-58872-6](https://doi.org/10.1038/s41467-025-58872-6)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者声称把 target-specific peptide guides 与 OTUB1 去泛素化酶催化域融合，构建出可编程 deubiquibodies (duAbs)，并用 language model 设计的肽把这一平台扩展到 β-catenin、FOXP3、WEE1、p53 和 PAX3::FOXO1 等多类靶蛋白。

## 创新边界

`主要创新在平台组合与新靶点验证；它复用了既有 uAb/duAb 架构和既有肽生成器，没有独立证明新的通用算法、全新分子机制或体内治疗优势。`。这不是全球首创性检索或独立复现结论。

## 研究问题

作者要解决的是：如何在 ubiquitin-proteasome pathway 失衡时，用可编程、可模块化的方式选择性去除目标蛋白上的泛素信号，从而稳定原本被过度降解的蛋白，尤其是“undruggable”或结构无序靶点。

## 方法

- LM scoring/生成guide、binding/稳定性实验。

## 数据与基准

- 多target proteins与peptide guides。

## 比较基线

- 随机/sequence-derived guides。

## 结果证据

- 正文明确稳定化测量为实验；其余设计score为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- target/细胞context与delivery有限。

## 仍未知

- p53 实验的细胞系在正文与 Figure 2D 图注中不一致：正文写 RH4，图注写 HeLa。
- 冻结正文未提供补充文件内容，因此部分补充图表与序列细节无法直接核验。
- 未见体内递送、药效学或毒理学证据，转化可行性仍不明确。

## Pi 结构化证据摘录

- **baseline：** 关键结果均以 polyG-OTUB1、non-targeting duAb 或 empty vector 作为阴性对照；FOXP3 还对比了 P60D2A peptide。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.5]；[doi:10.1038/s41467-025-58872-6, p.8]；[doi:10.1038/s41467-025-58872-6, p.12]
- **baseline：** 作者把 enDUBO1 作为既有 stabilization 架构基线，并把 DUBTAC 作为化学小分子 stabilization 背景对照来定位 duAb 方案。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.4]；[doi:10.1038/s41467-025-58872-6, p.11]
- **baseline：** 所有流式实验都在 PR-619 存在与否的条件下比较，以证明观察到的稳定化依赖 DUB catalytic activity。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.4]；[doi:10.1038/s41467-025-58872-6, p.5]；[doi:10.1038/s41467-025-58872-6, p.11]
- **data：** 报告数据覆盖 KCNQ1-YFP、β-catenin-sfGFP、TOP-GFP、FOXP3-mCherry、WEE1、p53 和 PAX3::FOXO1 等多种 reporter 与 endogenous target 读出。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.4]；[doi:10.1038/s41467-025-58872-6, p.5]；[doi:10.1038/s41467-025-58872-6, p.6]；[doi:10.1038/s41467-025-58872-6, p.11]；[doi:10.1038/s41467-025-58872-6, p.12]；[doi:10.1038/s41467-025-58872-6, p.13]
- **data：** 作者声明每组至少 3 个 biological replicates；WEE1 的 densitometry 汇总到 n=6，而 p53 与 PAX3::FOXO1 为 n=3，且未排除数据点。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.8]；[doi:10.1038/s41467-025-58872-6, p.12]；[doi:10.1038/s41467-025-58872-6, p.13]
- **data：** 作者还声明 raw 和 processed data（含 raw immunoblots）已存入 Zenodo，duAb cloning vector 将在发表后提交 Addgene。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.9]
- **declared_resources：** Binder design 依赖已发布或外部可访问资源：SaLT&PepPr、PepPrCLIP、PepMLM，以及 AlphaFold3 server。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.6]；[doi:10.1038/s41467-025-58872-6, p.8]
- **declared_resources：** 作者在致谢中说明，UbiquiTx 提供了 SaLT&PepPr 和 PepPrCLIP 的 core codebases，并用于本研究的肽设计。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.9]
- **declared_resources：** 论文声明的可复用材料包括 Zenodo 数据集与即将提交的 Addgene cloning vector。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.9]
- **limitations：** 证据几乎全部来自 transient transfection 的细胞系实验，没有体内递送、药效或安全性数据。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.7]；[doi:10.1038/s41467-025-58872-6, p.8]；[doi:10.1038/s41467-025-58872-6, p.12]；[doi:10.1038/s41467-025-58872-6, p.13]
- **limitations：** 作者明确指出 duAbs 约 290 aa，细胞内递送是转化瓶颈，因此提出 mRNA/LNP 作为未来方向。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.6]
- **limitations：** 实验设计未随机化、未盲法，样本量按领域惯例而非功效分析预先确定。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.8]
- **method：** 先将 target-specific peptide guide 与 OTUB1 catalytic domain 融合，并比较 OTUD1、UCHL1、UBC9 以及不同 linker 构型，以筛选更强的稳定化效应。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.4]；[doi:10.1038/s41467-025-58872-6, p.11]
- **method：** 新 guide peptide 主要来自 SaLT&PepPr、PepPrCLIP 和 PepMLM，再克隆进 pcDNA3-CMV-P2A-eGFP 的 duAb backbone，通过 Esp3I/KLD 和 T4 ligase 组装。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.6]；[doi:10.1038/s41467-025-58872-6, p.7]
- **method：** 在 HEK293T、HepG2、HeLa 和 RH4 等细胞中，作者用 flow cytometry、TOP-GFP reporter、immunoblot 和 densitometry 评估 duAb，并用 PR-619 验证 DUB 依赖性。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.4]；[doi:10.1038/s41467-025-58872-6, p.7]；[doi:10.1038/s41467-025-58872-6, p.8]；[doi:10.1038/s41467-025-58872-6, p.11]；[doi:10.1038/s41467-025-58872-6, p.12]；[doi:10.1038/s41467-025-58872-6, p.13]
- **results：** OTUB1 catalytic domain 的 YFP Nb fusion 在 KCNQ1-YFP stabilization 上优于 OTUD1、UCHL1 和 UBC9，而且 PR-619 可以消除该效应。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.4]；[doi:10.1038/s41467-025-58872-6, p.11]
- **results：** β-cat_SnP_7 和 β-cat_SnP_8 连接 OTUB1 后，不仅提高 β-catenin-sfGFP 水平，也提升 TOP-GFP 读出，说明 Wnt signaling 被增强。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.5]；[doi:10.1038/s41467-025-58872-6, p.11]
- **results：** 语言模型生成的 peptide guides 进一步把 duAb 程序化到 FOXP3、WEE1、p53 和 PAX3::FOXO1；其中多个构型表现出显著稳定化。
  - 证据：[doi:10.1038/s41467-025-58872-6, p.5]；[doi:10.1038/s41467-025-58872-6, p.6]；[doi:10.1038/s41467-025-58872-6, p.12]；[doi:10.1038/s41467-025-58872-6, p.13]

## 页码证据

- [doi:10.1038/s41467-025-58872-6, p.1]
- [doi:10.1038/s41467-025-58872-6, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
