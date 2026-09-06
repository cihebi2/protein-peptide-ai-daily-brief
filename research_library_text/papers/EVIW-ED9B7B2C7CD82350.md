# PhyloSuite v2: The development of an all-in-one, efficient and visualization-oriented suite for molecular dating analysis and other advanced features

- **论文 ID：** `EVIW-ED9B7B2C7CD82350`
- **期刊 / 来源：** Imeta
- **发表时间：** 2025 Nov 25
- **DOI：** [10.1002/imt2.70095](https://doi.org/10.1002/imt2.70095)
- **范围标签：** `Pi 已解析` / `背景资料` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者在 PhyloSuite v2 中新增 MDGUI、TimeTreeAnno 和 MCMCTracer，并把 MCMCtree/r8s 统一进一个图形化工作流，实现从文件导入、校准配置、模型选择、并行执行到 timetree 注释与收敛诊断的一体化分析。

## 创新边界

`主要创新在 GUI 工作流集成、可视化与工程优化，而不是新的分子钟理论或新的统计模型。`。这不是全球首创性检索或独立复现结论。

## 研究问题

MCMCtree 与 r8s 虽然是常用的 molecular dating 工具，但其输入格式、fossil calibration 设置、树可视化、模型选择和重复运行/收敛检查流程都较繁琐，尤其不利于大型数据集与非命令行用户。

## 方法

- 以图形界面封装MCMCtree/r8s，调用ModelFinder/IQ-TREE选择模型与计算Hessian，支持多链并行、暂停续跑、ESS与链间收敛统计以及时间树注释。

## 数据与基准

- 使用已发表的分子定年数据集比较多线程与命令行MCMCtree，并以示例数据演示完整工作流；不是蛋白/药物设计训练语料。

## 比较基线

- pamlX、MCMCtreeR、BEAST2、r8s/pyr8s、TVBOT和命令行MCMCtree。

## 结果证据

- 论文报告多线程在相同MCMC采样量下缩短运行时间，四线程PhyloSuite v2与命令行MCMCtree的节点时间估计差异很小；这属于软件功能与计算基准，不是生物实验结果。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- MDGUI当前不支持分区序列分析，统一转为非分区PML可能降低异质分区数据的模型准确性；TimeTreeAnno只覆盖基础注释，复杂性状/事件映射仍需iTOL或ChiPlot。

## 仍未知

- 补充图表 S1-S9 的具体数据规模、硬件环境和统计设置未在正文页完整展开。
- 代码仓库的许可证类型与第三方依赖许可边界未在论文页内明确说明。
- 外部独立复现结果与实际用户采用情况在冻结证据中不可见。

## Pi 结构化证据摘录

- **baseline：** 相较于 pamlX，MDGUI 补上了 timetree visualization、visual calibration、preview/edit config、multithreading 和 pause/resume 等能力。
  - 证据：[doi:10.1002/imt2.70095, p.3]；[doi:10.1002/imt2.70095, p.4]
- **baseline：** MCMCtreeR 与 TVBOT 分别偏向 time priors 准备/树可视化，无法独立完成完整的 molecular dating 分析流程。
  - 证据：[doi:10.1002/imt2.70095, p.3]
- **baseline：** 作者认为 BEAST 虽有 GUI 和 Tracer，但缺少自动格式转换、树界面上的 fossil calibration 管理、自动模型预测以及一键式 summarization/annotation。
  - 证据：[doi:10.1002/imt2.70095, p.3]；[doi:10.1002/imt2.70095, p.4]
- **baseline：** r8s/pyr8s 传统上依赖手写 command file，且在 Windows 部署不够便利；MDGUI 将其纳入图形化界面。
  - 证据：[doi:10.1002/imt2.70095, p.3]；[doi:10.1002/imt2.70095, p.8]
- **data：** 应用示例使用 PhyloSuite example.zip 中的 tree 和 sequence files，作为 MDGUI、MCMCTracer 和 TimeTreeAnno 的演示输入。
  - 证据：[doi:10.1002/imt2.70095, p.9]；[doi:10.1002/imt2.70095, p.10]；[doi:10.1002/imt2.70095, p.11]
- **data：** MCMCtree 分析会生成 results folder、run* 子目录，以及 repeat1/repeat2 和 mcmctree.ckpt，便于继续分析和汇总。
  - 证据：[doi:10.1002/imt2.70095, p.10]；[doi:10.1002/imt2.70095, p.11]
- **data：** r8s 运行后会产生 age_rates.csv 和 chronogram.nwk 等输出文件，供后续时间树可视化使用。
  - 证据：[doi:10.1002/imt2.70095, p.11]
- **declared_resources：** 论文明确声明最新源码仓库与下载页，包含 GitHub repository、releases 以及官网安装链接。
  - 证据：[doi:10.1002/imt2.70095, p.2]；[doi:10.1002/imt2.70095, p.12]
- **declared_resources：** 作者同时提供 step-by-step tutorials、demo 页面与 Supporting Information，包含 figures、tables、videos 和 Chinese translated version。
  - 证据：[doi:10.1002/imt2.70095, p.12]；[doi:10.1002/imt2.70095, p.14]
- **declared_resources：** 资金与算力支持来自 NSFC、Xizang Autonomous Region 项目、Lanzhou University 启动经费以及相关 supercomputing platform。
  - 证据：[doi:10.1002/imt2.70095, p.1]；[doi:10.1002/imt2.70095, p.12]
- **limitations：** 当前 MDGUI 不支持 partitioned sequence analysis，而是把输入统一转成 non-partitioned PML，这可能降低异质数据集上的模型精度。
  - 证据：[doi:10.1002/imt2.70095, p.11]
- **limitations：** TimeTreeAnno 被定位为轻量级基础注释工具，复杂的 trait data 或 evolutionary event mapping 更适合导出到 iTOL 或 ChiPlot。
  - 证据：[doi:10.1002/imt2.70095, p.11]
- **limitations：** MCMCtree 的 root node calibration 仍是强制要求，用户必须完成该步骤后才能继续分析。
  - 证据：[doi:10.1002/imt2.70095, p.10]
- **method：** MDGUI 提供 workflow input、drag-and-drop 和 import button 三种导入方式，并自动把 FASTA、NEXUS、PHYLIP 等常见比对格式转换为 MCMCtree 所需的 PML。
  - 证据：[doi:10.1002/imt2.70095, p.4]；[doi:10.1002/imt2.70095, p.6]；[doi:10.1002/imt2.70095, p.9]
- **method：** 系统把 fossil calibration 做成树界面上的可视化操作；MCMCtree 需要 root node calibration，而 r8s 支持 calibrate、constrain、fixage 和 unfixage 等命令格式。
  - 证据：[doi:10.1002/imt2.70095, p.6]；[doi:10.1002/imt2.70095, p.10]
- **method：** MDGUI 集成 ModelFinder 与 IQ-TREE，用于 best-fit model 选择和 Hessian matrix 计算，从而扩展到更多 nucleotide 与 amino acid models。
  - 证据：[doi:10.1002/imt2.70095, p.7]；[doi:10.1002/imt2.70095, p.9]；[doi:10.1002/imt2.70095, p.12]
- **method：** 工作流加入 pause/resume、repeat for convergence、multithreading 和 control file preview/edit，使重复链运行、参数修改和中断恢复更直接。
  - 证据：[doi:10.1002/imt2.70095, p.7]；[doi:10.1002/imt2.70095, p.8]；[doi:10.1002/imt2.70095, p.10]；[doi:10.1002/imt2.70095, p.11]
- **method：** TimeTreeAnno 基于 matplotlib 与 phyTreeViz 实现 timetree 注释与导出，MCMCTracer 基于 matplotlib 与 ArviZ 实现 MCMC 统计汇总、ESS 和收敛诊断。
  - 证据：[doi:10.1002/imt2.70095, p.8]；[doi:10.1002/imt2.70095, p.11]
- **results：** 作者在已发表数据集上报告，PhyloSuite v2 在相同 MCMC samples 条件下，4 threads 运行比 command-line MCMCtree 更快。
  - 证据：[doi:10.1002/imt2.70095, p.4]；[doi:10.1002/imt2.70095, p.12]
- **results：** 作者同时称，多线程版 PhyloSuite v2 与 command-line MCMCtree 的 node time estimates 差异很小。
  - 证据：[doi:10.1002/imt2.70095, p.4]
- **results：** MCMCTracer 可视化展示 posterior mean times、ESS、95% HPD 等统计量，并支持用散点图对两次分析的收敛性做对比。
  - 证据：[doi:10.1002/imt2.70095, p.8]；[doi:10.1002/imt2.70095, p.11]
- **results：** TimeTreeAnno 支持显示 geological timescales、confidence intervals、cluster annotation，并可导出 jpg、png、svg 和 pdf。
  - 证据：[doi:10.1002/imt2.70095, p.8]；[doi:10.1002/imt2.70095, p.11]

## 页码证据

- [doi:10.1002/imt2.70095, p.11]
- [doi:10.1002/imt2.70095, p.12]
- [doi:10.1002/imt2.70095, p.1]
- [doi:10.1002/imt2.70095, p.3]
- [doi:10.1002/imt2.70095, p.4]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
