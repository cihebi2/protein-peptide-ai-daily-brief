# Benchmarking AlphaFold3's protein-protein complex accuracy and machine learning prediction reliability for binding free energy changes upon mutation

- **论文 ID：** `EVIW-7B3BA40DB3C17D72`
- **期刊 / 来源：** arXiv preprint（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.48550/arxiv.2406.03979](https://doi.org/10.48550/arxiv.2406.03979)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `结构预测` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称系统比较 AF3 复合体结构与原始 PDB 结构在突变 ΔΔG 预测中的可用性：在 317 个复合体、8330 个样本上，AF3 结构仍能取得 Rp=0.86，但 RMSE 比 PDB 结构高 8.6%，且 ipTM 不能稳定反映 RMSD 或柔性区域失配。

## 创新边界

`这是 benchmark 与可靠性评估，不是新的候选生成方法。`。这不是全球首创性检索或独立复现结论。

## 研究问题

评估 AlphaFold3 生成的蛋白-蛋白复合体结构，是否足以支持 SKEMPI 2.0 上单点突变导致的结合自由能变化（ΔΔG/BFE）预测，并检验其结构误差、ipTM/pTM 与预测误差之间的关系。

## 方法

- AF3预测WT/mutant结构，输入多种structure-based ΔΔG模型，按complex accuracy分层。

## 数据与基准

- PPI mutation/ΔΔG benchmark。

## 比较基线

- experimental structures、AF2/AFM与多ΔΔG predictors。

## 结果证据

- 论文报告结构精度与ΔΔG可靠性关联；为计算benchmark。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- AF3可访问性/版本、预印本、预测结构不保证thermodynamics。

## 仍未知

- Supporting Information 未在正文中展开，完整超参数、训练细节与附录结果仍不可见。
- 冻结正文未提供独立外部测试集上的泛化验证，因此外推能力仍未明。
- GitHub 仓库是否包含可复现实验脚本、许可与版本锁定信息，未在本次作业中核验。

## Pi 结构化证据摘录

- **baseline：** 与原始 PDB 结构驱动的 MT-TopLap 相比，AF3 结构的 Rp 略低而 RMSE 更高。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.6]；[doi:10.48550/arxiv.2406.03979, p.11]
- **baseline：** 与 mCSM-PPI2 等非 topology baseline 相比，作者声称 MT-TopLapAF3 的 RMSE 有约 18% 的改善。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.6]
- **baseline：** 作者也把 MT-TopLapAF3 与 TopNetTree、TopNetGBT、TopLapNetGBT、LapNet、LapGBT 等既有方法并列，整体 Rp 位于 0.80–0.88 区间。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.6]
- **data：** 主数据集是 SKEMPI 2.0 的 S8338，原始规模为 317 个复合体与 8338 个突变样本；因 3NVN 和 4U6H 的受限序列无法由 AlphaFold Server 预测，最终分析 8330 个样本。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.5]
- **data：** AF3 复合体来自 AlphaFold Server，PDB 结构来自 RCSB PDB，SKEMPI 2.0 来自官方数据库页面。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.15]
- **data：** 作者对 317 个 AF3 复合体统计 RMSD、ipTM、pTM，并进一步分析 top 40 最差 RMSD 与最低 ipTM 的复合体。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.10]
- **declared_resources：** AF3 复合体可通过 AlphaFold Server 生成，作者给出仓库子目录 https://github.com/ExpectozJJ/MT-TopLap/alphafold/。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.15]
- **declared_resources：** 原始 PDB files 可从 RCSB PDB 下载，SKEMPI 2.0 可从 life.bsc.es/pid/skempi2 获取。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.15]
- **declared_resources：** 全部 source code 和 models 公开在 https://github.com/ExpectozJJ/MT-TopLap/，并附 Supporting Information。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.15]
- **limitations：** AlphaFold Server 对 3NVN 和 4U6H 的序列受限，导致 8 个样本无法纳入，说明覆盖并不完整。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.5]
- **limitations：** ipTM 不能可靠区分高低 RMSD，因此单靠 AF3 置信分数会掩盖结构失配。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.1]；[doi:10.48550/arxiv.2406.03979, p.9]；[doi:10.48550/arxiv.2406.03979, p.10]；[doi:10.48550/arxiv.2406.03979, p.11]
- **limitations：** AF3 对 intrinsically flexible regions/domains 不可靠，尤其在高 B-factor 区域出现明显 misalignment。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.1]；[doi:10.48550/arxiv.2406.03979, p.10]；[doi:10.48550/arxiv.2406.03979, p.11]
- **method：** 从 AlphaFold Server 生成 SKEMPI 2.0 中 317 个 PPI 复合体的 AF3 结构，并用这些结构替代 PDB 结构做突变 ΔΔG 预测。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.5]；[doi:10.48550/arxiv.2406.03979, p.15]
- **method：** 使用 MT-TopLapAF3 做 10-fold cross-validation，并以 Pearson correlation coefficient 和 RMSE 评估预测性能。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.6]
- **method：** 构造 element/site-specific persistent Laplacian 特征，把 mutation site、mutation neighborhood、binding-site 邻域与元素子集编码为 point clouds，再生成 VR/Alpha complex 特征。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.12]；[doi:10.48550/arxiv.2406.03979, p.13]；[doi:10.48550/arxiv.2406.03979, p.14]
- **method：** 将 AF3 结构与 PDB 结构做整体 RMSD 对齐，同时检查 ipTM 与 pTM 作为 AF3 置信度指标。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.9]；[doi:10.48550/arxiv.2406.03979, p.10]
- **results：** MT-TopLapAF3 在 S8338 上得到 Rp=0.86、RMSE=1.025 kcal/mol；作者报告相对 PDB 结构的 MT-TopLap（Rp=0.88、RMSE=0.937 kcal/mol）RMSE 增加 8.6%。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.6]；[doi:10.48550/arxiv.2406.03979, p.11]
- **results：** 317 个 AF3 复合体的平均 RMSD 为 1.61 Å，平均 ipTM 为 0.803，平均 pTM 为 0.847；其中 71.6% 的复合体 ipTM≥0.8，98.7% 的复合体 pTM≥0.5。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.9]
- **results：** 仅有 6 个复合体同时具有低 ipTM 与低 RMSD，说明 ipTM 与结构偏差的相关性很弱。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.10]
- **results：** 高 B-factor 残基与高 RMSD 残基明显对应，支持 AF3 对高柔性区域或结构域不可靠的判断。
  - 证据：[doi:10.48550/arxiv.2406.03979, p.10]；[doi:10.48550/arxiv.2406.03979, p.11]

## 页码证据

- [doi:10.48550/arxiv.2406.03979, p.1]
- [doi:10.48550/arxiv.2406.03979, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
