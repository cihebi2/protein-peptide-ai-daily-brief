# Benchmarking inverse folding models for antibody CDR sequence design

- **论文 ID：** `EVIW-AEAE9AA5539B2E45`
- **期刊 / 来源：** PLOS ONE（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1371/journal.pone.0324566](https://doi.org/10.1371/journal.pone.0324566)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白质设计` / `结构预测` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者声称建立了一个统一 benchmark，对 ProteinMPNN、ESM-IF、LM-Design、AntiFold 在抗体 CDR 设计、残基级别恢复、结构一致性和突变效应预测上的能力做系统比较，并引入 sequence similarity 等补充指标。

## 创新边界

`这是比较评测与方法分析，不是新设计算法，也没有新的湿实验验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

评估用于抗体 CDR 序列设计的 inverse folding 模型在 Fab/VHH 场景下的真实表现，并判断它们是否能识别关键结合残基与突变效应。

## 方法

- 固定backbone输入多种inverse folding model，按CDR区和抗体任务评价。

## 数据与基准

- SAbDab/antibody structures及CDR测试集。

## 比较基线

- ProteinMPNN/ESM-IF/antibody-specific模型。

## 结果证据

- 论文揭示模型在不同CDR/指标差异；为计算benchmark。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 序列恢复不等于affinity，结构/同源泄漏与实验缺失。

## 仍未知

- GitHub 仓库是否可直接复现，冻结页内未给出代码审计结果。
- 未见新的 wet-lab 实验验证，因此功能性改进是否能转化到真实亲和力仍未知。
- 对更多 antibody subclasses、不同 antigen 类型以及更大规模 VHH 数据的泛化仍不清楚。
- Boltz-1 与 sequence similarity 这些替代指标在其他 benchmark 上的稳定性尚未验证。

## Pi 结构化证据摘录

- **baseline：** 主比较对象是 ProteinMPNN、ESM-IF、LM-Design、AntiFold；其中 ProteinMPNN 与 ESM-IF 属于 general protein model，LM-Design 结合 protein language model 与 structure encoder，AntiFold 是从 ESM-IF fine-tune 而来。
  - 证据：[doi:10.1371/journal.pone.0324566, p.2]
- **baseline：** 作者还提到先评估过 AbMPNN，但最终主要聚焦 AntiFold，因为其结果更强并与文献一致。
  - 证据：[doi:10.1371/journal.pone.0324566, p.4]
- **baseline：** 突变预测部分额外加入了 ESM2 作为 sequence language model baseline。
  - 证据：[doi:10.1371/journal.pone.0324566, p.15]；[doi:10.1371/journal.pone.0324566, p.16]
- **data：** 序列设计基准从 SAbDab 过滤得到 203 个 Fab 和 61 个 VHH 结构，排除了低分辨率、缺残基、多 antigen 链、重复序列和部分 coronavirus antigen。
  - 证据：[doi:10.1371/journal.pone.0324566, p.5]
- **data：** 突变效应基准来自 SKEMPI2 中的 1VFB/1MHP、CR9114、CR6261 与 1MLC 等公开数据；作者还公开了数据和 notebook 链接。
  - 证据：[doi:10.1371/journal.pone.0324566, p.7]；[doi:10.1371/journal.pone.0324566, p.1]
- **declared_resources：** 页面 1 给出 Zenodo 链接，声明 data and notebooks available。
  - 证据：[doi:10.1371/journal.pone.0324566, p.1]
- **declared_resources：** 页面 7 给出 GitHub repo，并声称包含 scripts、PDB files、raw designed sequences、processing/analysis scripts 和 Rosetta XML files。
  - 证据：[doi:10.1371/journal.pone.0324566, p.7]
- **limitations：** 作者明确指出 recovery rate 不能完整反映功能，因为保守替换会被惩罚，而且 CDR 里存在明显 amino acid bias。
  - 证据：[doi:10.1371/journal.pone.0324566, p.4]
- **limitations：** Boltz-1 refolding 的噪声较大，因此 CDR folding accuracy 难以被可靠评估。
  - 证据：[doi:10.1371/journal.pone.0324566, p.9]
- **limitations：** ProteinMPNN 和 ESM-IF 在抗体特异性，尤其 H3 与 VHH 上表现不足，说明一般蛋白训练集对 antibody design 仍有限。
  - 证据：[doi:10.1371/journal.pone.0324566, p.8]；[doi:10.1371/journal.pone.0324566, p.18]
- **limitations：** 作者建议未来纳入更大规模 antibody-specific datasets、VHH 和 functional data，但这些改进尚未在本研究中完成。
  - 证据：[doi:10.1371/journal.pone.0324566, p.18]；[doi:10.1371/journal.pone.0324566, p.19]
- **method：** 作者把评估分成 CDR 序列设计和抗体亲和突变效应预测两项任务；Fab 评估 6 个 CDR，VHH 评估 3 个 heavy-chain CDR。
  - 证据：[doi:10.1371/journal.pone.0324566, p.4]；[doi:10.1371/journal.pone.0324566, p.5]
- **method：** 设计时每个样本通常采样 100 条序列，temperature 为 0.2；还比较了有/无 antigen 输入，并用 Rosetta FastRelax 与 Boltz-1 做结构一致性检查。
  - 证据：[doi:10.1371/journal.pone.0324566, p.5]；[doi:10.1371/journal.pone.0324566, p.6]；[doi:10.1371/journal.pone.0324566, p.9]
- **method：** 残基按 buried、key interaction、surface contact 分类，其中 key interaction 由 alanine scanning 后 ΔΔG > 1.5 kcal/mol 定义；突变效应用 SKEMPI2、CR9114、CR6261、1MLC 数据集和 Spearman correlation 评估。
  - 证据：[doi:10.1371/journal.pone.0324566, p.6]；[doi:10.1371/journal.pone.0324566, p.7]；[doi:10.1371/journal.pone.0324566, p.15]；[doi:10.1371/journal.pone.0324566, p.16]
- **method：** 序列相似度使用 BLOSUM62 归一化计算，作者同时分析 amino acid composition bias、sequence logos 和 design 后的 refolding RMSD。
  - 证据：[doi:10.1371/journal.pone.0324566, p.6]；[doi:10.1371/journal.pone.0324566, p.9]；[doi:10.1371/journal.pone.0324566, p.10]；[doi:10.1371/journal.pone.0324566, p.11]
- **results：** Fab 上总体排序为 AntiFold > LM-Design > ESM-IF > ProteinMPNN；VHH 上则是 LM-Design > AntiFold ≈ ESM-IF ≈ ProteinMPNN。
  - 证据：[doi:10.1371/journal.pone.0324566, p.7]；[doi:10.1371/journal.pone.0324566, p.8]
- **results：** AntiFold 在大多数 amino acid type 的恢复率最高，但 Pro/Gly 例外；即便预测错误，很多替换仍保持相近的理化性质。
  - 证据：[doi:10.1371/journal.pone.0324566, p.10]；[doi:10.1371/journal.pone.0324566, p.11]
- **results：** buried 残基最容易被恢复；ESM-IF 对 key interaction 和 surface contact 更依赖 antigen 结构，而 AntiFold 对 antigen presence 几乎不敏感。
  - 证据：[doi:10.1371/journal.pone.0324566, p.12]；[doi:10.1371/journal.pone.0324566, p.13]；[doi:10.1371/journal.pone.0324566, p.14]
- **results：** 突变效应预测中，ESM-IF、ProteinMPNN、LM-Design 多数数据集为正相关，ESM-IF 平均 Spearman 相关最高；ESM2 在 CR6261 上较强但整体波动大。
  - 证据：[doi:10.1371/journal.pone.0324566, p.15]；[doi:10.1371/journal.pone.0324566, p.16]
- **results：** Refolding RMSD 上不同模型没有显著差异，作者认为 Boltz-1 本身会引入较大噪声。
  - 证据：[doi:10.1371/journal.pone.0324566, p.9]

## 页码证据

- [doi:10.1371/journal.pone.0324566, p.1]
- [doi:10.1371/journal.pone.0324566, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
