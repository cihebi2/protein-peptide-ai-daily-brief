# Empowering AlphaFold2 for protein conformation selective drug discovery with AlphaFold2-RAVE

- **论文 ID：** `EVIW-F561FB87AC7DBE6C`
- **期刊 / 来源：** eLife
- **发表时间：** 2024 Sep 6
- **DOI：** [10.7554/elife.99702](https://doi.org/10.7554/elife.99702)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `结构预测`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 AF2RAVE-Glide 工作流：先用 rMSA AF2 生成构象集合，再以 MD、SPIB/umbrella sampling 给 metastable decoy 赋予 Boltzmann 排名，最后结合 Glide XP/IFD/IFD-trim 对 DDR1、Abl1 和 Src 的 type II inhibitor 结合构象进行富集与 docking 评估。

## 创新边界

`主要新意在于把既有 AF2、RAVE/SPIB 与 docking 组合成可转移的工作流，并展示对 kinase metastable state 的排序与筛选；它不是新湿实验，也不是从头生成分子候选的全新算法。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何在缺少配体共晶结构时，仅从蛋白序列与AF2预测构象中识别可用于选择性小分子设计的 metastable holo-like pocket，尤其是难采样的 kinase classical DFG-out 状态。

## 方法

- 降低MSA深度产生AF2 decoy，聚类并运行MD，SPIB/RAVE学习反应坐标和PMF，再以Glide筛选构象选择性配体。

## 数据与基准

- DDR1、Abl1、Src等三种kinase及已知type-I/type-II inhibitor。

## 比较基线

- 直接AF2结构、AF2 cluster、PDB holo结构和常规Glide。

## 结果证据

- 论文/评审认为组合流程改善三种kinase的ligand docking和早期富集；均为计算验证。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- PMF赋值近似、力场/采样有限；AF2 steric clash和metastable状态覆盖仍可能失败。

## 仍未知

- 未做前瞻性虚拟筛选或实验验证
- 是否能泛化到非 kinase 蛋白仍未知
- PMF 受 umbrella 设置影响
- 对 A-loop/DFG 的先验依赖较强

## Pi 结构化证据摘录

- **baseline：** 与 AF2、rMSA AF2、AF2-cluster 和 DiffDock 相比，AF2RAVE 提供了更稳定的 metastable-state 选择与排序，而直接 AF2/tAF2 在 type II docking 上明显更差。
  - 证据：[doi:10.7554/elife.99702, p.5]；[doi:10.7554/elife.99702, p.10]；[doi:10.7554/elife.99702, p.11]
- **baseline：** AF2-cluster 虽然在 Abl1 中产生了更多 A-loop folded 构象（21/197），但仍没有 classical DFG-out decoy，说明仅靠序列聚类不足以找到可 docking 的状态。
  - 证据：[doi:10.7554/elife.99702, p.10]；[doi:10.7554/elife.99702, p.11]
- **baseline：** Table 1 显示，AF2-Abl1、AF2-DDR1、rMSA AF2-Abl1 都是 0/1 或 0/2 命中，而 rMSA AF2-DDR1、AF2RAVE-DDR1、AF2RAVE-Abl1 分别提升到 1/15、1/2、4/8。
  - 证据：[doi:10.7554/elife.99702, p.11]；[doi:10.7554/elife.99702, p.12]
- **data：** 研究对象是三种 kinases：Abl1、DDR1 和 Src；配体包括 type I 的 VX-680、dasatinib 与 type II 的 imatinib、ponatinib。
  - 证据：[doi:10.7554/elife.99702, p.3]；[doi:10.7554/elife.99702, p.12]；[doi:10.7554/elife.99702, p.13]
- **data：** 比较结构来源包括原始 AF2、rMSA AF2、AF2-cluster、tAF2，以及 PDB 中的晶体 holo 结构，用来对照 docking 结果。
  - 证据：[doi:10.7554/elife.99702, p.1]；[doi:10.7554/elife.99702, p.3]；[doi:10.7554/elife.99702, p.10]；[doi:10.7554/elife.99702, p.12]
- **data：** 分子模拟采用 Amber99SB*-ILDN、TIP3P、OpenMM、300 K、2 fs 步长、PME 和 LINCS，并在能量最小化后做 NVT/NPT 平衡。
  - 证据：[doi:10.7554/elife.99702, p.12]；[doi:10.7554/elife.99702, p.13]；[doi:10.7554/elife.99702, p.14]
- **declared_resources：** 代码和数据公开在 GitHub，且页面给出 Software Heritage 归档，便于复现与审计。
  - 证据：[doi:10.7554/elife.99702, p.13]；[doi:10.7554/elife.99702, p.16]
- **declared_resources：** 计算资源来自 NIH NIGMS 的 R35GM142719、UMD HPC Zaratan 和 NSF ACCESS CHE180027P。
  - 证据：[doi:10.7554/elife.99702, p.15]
- **declared_resources：** 工作流程依赖 ColabFold/mmseq2、Schrödinger Maestro/Glide/Prime、OpenMM，以及 DiffDock webserver 等现成工具。
  - 证据：[doi:10.7554/elife.99702, p.2]；[doi:10.7554/elife.99702, p.12]；[doi:10.7554/elife.99702, p.13]；[doi:10.7554/elife.99702, p.15]
- **limitations：** 作者承认 PMF 的绝对值和 Boltzmann rank 会随 umbrella window 与 simulation length 波动，而且 A-loop folded/extended 区域 overlap 不足。
  - 证据：[doi:10.7554/elife.99702, p.7]；[doi:10.7554/elife.99702, p.8]；[doi:10.7554/elife.99702, p.14]
- **limitations：** Abl1 的 umbrella sampling 出现较多 αC helix breakage，需要丢弃 broken windows，说明该流程对某些系统并不稳健。
  - 证据：[doi:10.7554/elife.99702, p.9]；[doi:10.7554/elife.99702, p.14]
- **limitations：** 当前工作只系统研究了 kinase 的 classical DFG-out 状态，而且还依赖 A-loop distance cutoff 与 Dunbrack DFG 定义等先验信息。
  - 证据：[doi:10.7554/elife.99702, p.3]；[doi:10.7554/elife.99702, p.12]；[doi:10.7554/elife.99702, p.14]
- **limitations：** 这是回顾性计算验证，没有湿实验或前瞻性大库筛选；作者也明确把更一般的无先验蛋白设计留给未来。
  - 证据：[doi:10.7554/elife.99702, p.1]；[doi:10.7554/elife.99702, p.12]；[doi:10.7554/elife.99702, p.15]
- **method：** 作者将 rMSA AF2、regular-space clustering、无偏 MD、SPIB 与 umbrella sampling 串成 AF2RAVE，再用 Glide XP/IFD 完成对接与重打分。
  - 证据：[doi:10.7554/elife.99702, p.1]；[doi:10.7554/elife.99702, p.2]；[doi:10.7554/elife.99702, p.3]；[doi:10.7554/elife.99702, p.7]；[doi:10.7554/elife.99702, p.13]；[doi:10.7554/elife.99702, p.14]
- **method：** rMSA AF2 通过降低 MSA 深度到 16 或 32，并对每个 kinase 用 128 个随机种子各生成 5 个模型，共得到 1280 个结构；随后按与最高 pLDDT AF2 结构的 RMSD >7 Å 过滤不合理构象。
  - 证据：[doi:10.7554/elife.99702, p.5]；[doi:10.7554/elife.99702, p.13]
- **method：** AF2RAVE 在 DDR1 上先选 12 个初始结构跑各 50 ns 无偏 MD，把 14 个 CV 中方差较大的 8 个输入 SPIB，随后用 11×11 umbrella sampling 在 2D latent space 上算 PMF。
  - 证据：[doi:10.7554/elife.99702, p.7]；[doi:10.7554/elife.99702, p.13]；[doi:10.7554/elife.99702, p.14]
- **method：** tAF2 通过把 DDR1 的 classical DFG-out decoys 作为模板，在 ColabFold 中为 Abl1 生成 30 个结构，并对 Src 用 DDR1 的代表性结构做模板转移。
  - 证据：[doi:10.7554/elife.99702, p.9]；[doi:10.7554/elife.99702, p.13]
- **results：** 默认 AF2 结构对 type I inhibitor 还能较好 docking，但对 type II inhibitor 基本失败；文中给出的最差 ligand RMSD 常在 8 Å 以上。
  - 证据：[doi:10.7554/elife.99702, p.4]；[doi:10.7554/elife.99702, p.5]
- **results：** DDR1 的 rMSA AF2 集合里确实出现了一个可称为 holo-model 的 classical DFG-out 构象，ponatinib 的 IFD RMSD 为 0.89 Å，imatinib 在 IFD-trim 下为 1.04 Å。
  - 证据：[doi:10.7554/elife.99702, p.5]；[doi:10.7554/elife.99702, p.6]；[doi:10.7554/elife.99702, p.7]
- **results：** AF2RAVE 用 PMF 将 DDR1 的 15 个 classical DFG-out 候选富集到至少 2 个高优先级结构，其中 holo-model 进入 top 2；DiffDock 的高置信 pose 也与 AF2RAVE 排名一致。
  - 证据：[doi:10.7554/elife.99702, p.7]；[doi:10.7554/elife.99702, p.8]；[doi:10.7554/elife.99702, p.9]
- **results：** 对 Abl1，tAF2 30 个 decoys 里有 4 个可将 type II inhibitors dock 到 <3 Å，而 AF2RAVE 又把这 4 个都排进 top 8；Src 的 tAF2 对 imatinib 也达到 2.82 Å。
  - 证据：[doi:10.7554/elife.99702, p.9]；[doi:10.7554/elife.99702, p.10]；[doi:10.7554/elife.99702, p.11]

## 页码证据

- [doi:10.7554/elife.99702, p.14]
- [doi:10.7554/elife.99702, p.1]
- [doi:10.7554/elife.99702, p.5]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
