# Adapting Co-Folding Models for Structure-Based Protein-Protein Docking Through Flow Matching

- **论文 ID：** `EVIW-649DEFAB11294A5F`
- **期刊 / 来源：** bioRxiv
- **发表时间：** 2025 Dec 23
- **DOI：** [10.1101/2025.11.28.691195](https://doi.org/10.1101/2025.11.28.691195)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `扩散/生成` / `结构预测` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称提出 AF2Dock：用 docking module 取代 AF-M 的 template module，并以 flow matching 端到端训练，使模型能够从非 holo 结构输入直接生成并排序蛋白复合体构象。

## 创新边界

`创新边界主要在 AF-M 的结构改造、去噪式对接模块与 flow matching 训练/推理流程；它不是新湿实验、新数据集或新任务定义。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何在不依赖 MSA 的情况下，把 co-folding 模型改造成可用于 structure-based protein-protein docking 的生成式方法，以应对 antibody-antigen、nanobody 等难以从序列共进化信号中获益的复合体。

## 方法

- 以OpenFold AF-M为骨干，对配体平移、旋转和内部坐标定义flow path；PINDER 230万二蛋白复合物训练，采样后用ipTM排序。

## 数据与基准

- PINDER训练集；无AF-M/AF3界面结构簇重叠的PINDER-AF2 benchmark，以及抗体/纳米抗体测试集。

## 比较基线

- single-sequence AF-M、co-folding AF-M、AF3、DiffDock-PP、DFMDock、HDock、ZDock。

## 结果证据

- AF2Dock在holo/apo结构输入下优于扩散docking并产生与共折叠模型正交的成功案例，但预测单体输入下明显低于AF-M/AF3，不能正确探索大幅内部柔性。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 内部柔性探索不足，预测单体输入性能大幅下降；简单合并AF2Dock与AF-M后ipTM重排多数情况下没有改善Top-1/Top-5；该文为未同行评议预印本。

## 仍未知

- 补充材料中的伪代码、超参数与更细的训练实现未在冻结正文中完整展开。
- 论文未提供独立的外部 novelty verification，因此全球新颖性只能保持未验证状态。
- ipTM 过置信问题被识别出来，但更稳健的 ranking 方案尚未在正文中定案。

## Pi 结构化证据摘录

- **baseline：** 论文系统比较了 single-sequence AF-M、co-folding AF-M、AF3、DiffDock-PP、DFMDock、HDock 和 ZDock，并使用 DockQ 阈值定义 success。
  - 证据：[doi:10.1101/2025.11.28.691195, p.5]；[doi:10.1101/2025.11.28.691195, p.6]
- **baseline：** 对 co-folding 对照，作者使用标准数据管线，而没有输入与 structure-based docking 相同的 templates。
  - 证据：[doi:10.1101/2025.11.28.691195, p.6]
- **data：** 训练集来自 PINDER training set，共 2.3 million bi-protein complexes；作者还构造 tri-protein complexes，并在训练中混用 holo、apo 与 predicted monomer structures。
  - 证据：[doi:10.1101/2025.11.28.691195, p.5]
- **data：** 测试集包括 PINDER-AF2 benchmark（180 holo、30 apo、127 predicted complexes）以及 antibody/nanobody set（49 antibody、60 nanobody complexes），后者还构造了 AF3-predicted inputs。
  - 证据：[doi:10.1101/2025.11.28.691195, p.5]
- **declared_resources：** Code for AF2Dock 公开在 GitHub，model weights 与 AF3-predicted inputs 放在 Zenodo entry 17782958。
  - 证据：[doi:10.1101/2025.11.28.691195, p.12]；[doi:10.1101/2025.11.28.691195, p.14]
- **declared_resources：** 研究还声明获得 NIH R35-GM141881 支持，并使用了 ARCH 计算资源。
  - 证据：[doi:10.1101/2025.11.28.691195, p.12]
- **limitations：** 核心限制是 AF2Dock 不能有效探索 subunit flexibility；input-output ps-iRMSD 变化很小，且对更难目标的成功率下降更明显。
  - 证据：[doi:10.1101/2025.11.28.691195, p.7]；[doi:10.1101/2025.11.28.691195, p.11]
- **limitations：** ipTM 对 false positive 可能过于自信，导致 AF2Dock 与 AF-M 的结果难以通过简单重排融合。
  - 证据：[doi:10.1101/2025.11.28.691195, p.8]；[doi:10.1101/2025.11.28.691195, p.11]
- **limitations：** 作者还指出，简单加入 MSA features 并未带来更好的 flexibility 或 overall performance。
  - 证据：[doi:10.1101/2025.11.28.691195, p.11]；[doi:10.1101/2025.11.28.691195, p.12]
- **method：** AF2Dock 将 AF-M 的 template module 替换为 docking module；该模块把 noisy complex structure 编码为 pair representation，并通过 pair denoiser 结合 AdaLN 进行去噪后再回馈 Evoformer。
  - 证据：[doi:10.1101/2025.11.28.691195, p.2]；[doi:10.1101/2025.11.28.691195, p.3]；[doi:10.1101/2025.11.28.691195, p.4]
- **method：** 训练采用 conditional flow matching，把 noise-to-data 的插值路径作为 conditional probability path，并用 AF-M 的原始损失进行优化，且省略 masked MSA loss。
  - 证据：[doi:10.1101/2025.11.28.691195, p.4]；[doi:10.1101/2025.11.28.691195, p.5]
- **method：** 推理时默认沿 learned velocity field 做 10 个 time steps 的积分，每个目标采样 20 或 40 个结构，并用 ipTM 进行排序。
  - 证据：[doi:10.1101/2025.11.28.691195, p.5]
- **results：** 在 PINDER-AF2 的 holo 输入下，single-sequence AF-M（带 recycling）意外优于 co-folding AF-M；AF2Dock 低于带 recycling 的 single-sequence AF-M，但明显优于 diffusion-based docking models。
  - 证据：[doi:10.1101/2025.11.28.691195, p.6]；[doi:10.1101/2025.11.28.691195, p.7]
- **results：** 在 apo 与 predicted 输入下，AF2Dock 仍能在部分目标上给出正确结构，但总体成功率明显下降；它通常与其他 structure-based docking methods 持平或更好，但仍落后于 co-folding AF-M 和 AF3。
  - 证据：[doi:10.1101/2025.11.28.691195, p.7]
- **results：** 在 antibody/nanobody set 上，AF2Dock 对 nanobody complexes 的 predicted inputs 优于所有其他 structure-based docking methods，但 Top-1 与 Top-5 仍低于 AF-M 和 AF3，说明排序环节仍不稳。
  - 证据：[doi:10.1101/2025.11.28.691195, p.8]；[doi:10.1101/2025.11.28.691195, p.9]；[doi:10.1101/2025.11.28.691195, p.10]
- **results：** AF2Dock 与 co-folding AF-M/AF3 的正确预测呈现 orthogonality，说明二者有互补性，但简单用 ipTM 重排通常不足以稳定提升整体成功率。
  - 证据：[doi:10.1101/2025.11.28.691195, p.7]；[doi:10.1101/2025.11.28.691195, p.8]；[doi:10.1101/2025.11.28.691195, p.11]

## 页码证据

- [doi:10.1101/2025.11.28.691195, p.11]
- [doi:10.1101/2025.11.28.691195, p.12]
- [doi:10.1101/2025.11.28.691195, p.1]
- [doi:10.1101/2025.11.28.691195, p.5]
- [doi:10.1101/2025.11.28.691195, p.6]
- [doi:10.1101/2025.11.28.691195, p.7]
- [doi:10.1101/2025.11.28.691195, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
