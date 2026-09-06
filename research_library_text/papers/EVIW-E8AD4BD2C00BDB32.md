# Enhanced antibody-antigen structure prediction from molecular docking using AlphaFold2

- **论文 ID：** `EVIW-E8AD4BD2C00BDB32`
- **期刊 / 来源：** Sci Rep
- **发表时间：** 2023 Sep 13
- **DOI：** [10.1038/s41598-023-42090-5](https://doi.org/10.1038/s41598-023-42090-5)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `结构预测` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出并验证 AF2Composite 重评分方案，将 AF2 的 pLDDT 与 pTMscore 标准化后相加，用于对 docking 生成的抗体-抗原复合物姿势进行重排序，并在多个基准集合上提升分类与 top-k 成功率。

## 创新边界

`创新边界主要是 AF2 作为 docking pose 的重评分与轻量重构器，而不是端到端生成新复合物模型。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在缺乏共进化信息的抗体-抗原复合物场景中，如何利用 AF2 改善 physics-based docking 的评分与排序，从而提高 near-native pose 的早期富集与命中率。

## 方法

- antibody/antigen docking产生poses，AF2/模板重构和置信度筛选。

## 数据与基准

- Ab-Ag benchmark。

## 比较基线

- AF2/AF-M、docking alone。

## 结果证据

- 论文报告结构精度提升；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- known structures/template leakage、CDR flexibility。

## 仍未知

- 未见独立代码仓库或可复用脚本链接。
- AF2Composite 在外部数据集上的泛化与阈值稳定性仍需进一步验证。
- 训练集重叠的潜在影响虽有后训练控制集缓解，但不能完全排除。

## Pi 结构化证据摘录

- **baseline：** 论文的主 baseline 是各 docking 方法自身的原始打分排序，再与 AF2Composite 重排序结果进行逐一比较。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.4]；[doi:10.1038/s41598-023-42090-5, p.7]
- **baseline：** ClusPro 对 PIPER 结果的聚类后处理本身也作为另一层传统 docking 处理链条，被拿来观察是否仍可被 AF2 进一步改善。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.2]；[doi:10.1038/s41598-023-42090-5, p.6]
- **baseline：** 作者用 template-free AF2-Multimer 作为与模板驱动 AF2 rescoring 相对照的外部比较基线。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.8]
- **baseline：** 文中还比较了 full atomistic template 与 gap indexing 等输入变体，作为 AF2 rescoring 流程的消融基线。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.7]；[doi:10.1038/s41598-023-42090-5, p.10]；[doi:10.1038/s41598-023-42090-5, p.11]
- **data：** 主数据集来自 protein-protein benchmark v5.0 与 antibody benchmark，形成 231 个 bound-backbone 体系；另有 25 个对应 unbound-backbone 体系，以及 88 个 2022 年后发表的额外 bound-backbone 体系。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.11]；[doi:10.1038/s41598-023-42090-5, p.8]
- **data：** 每个体系按方法生成 top 100 docking 模型，合计得到 76,383 个 bound-backbone 模型与 8,246 个 unbound-backbone 模型，并据 CAPRI 标注 positives / negatives。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.2]；[doi:10.1038/s41598-023-42090-5, p.3]
- **data：** 作者声明所有分析数据都已包含在正文与补充材料中，未在正文中给出独立代码仓库链接。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.13]
- **declared_resources：** AF2 计算在 Compute Canada 的 NVidia A100、P100 与 V100 上完成，ColabFold 则在本地 GeForce GTX 1080 Ti 和 RTX 2080 Ti 上运行。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.12]
- **declared_resources：** 关键软件栈包括 ProPOSE 1.0.2、ZDOCK 3.0.2、PIPER 0.0.4、ClusPro、SCWRL4、Amber、AlphaFold 2.2.2 / 2.3.1 与 ColabFold 1.5.2。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.11]；[doi:10.1038/s41598-023-42090-5, p.12]
- **declared_resources：** 作者在致谢中说明使用了 Digital Research Alliance of Canada 的算力配额，并给出补充材料中的运行时信息。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.14]；[doi:10.1038/s41598-023-42090-5, p.12]
- **limitations：** AF2 仍缺少显式物理约束，难以精确复现界面细粒度原子细节，因此高质量模板有时会在重建后反而下降。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.3]；[doi:10.1038/s41598-023-42090-5, p.10]
- **limitations：** 模型质量对 AF2Composite 影响很大，acceptable-quality decoy 往往更难被高置信度区分，ClusPro 在部分集合上还会出现 rescoring 退化。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.6]；[doi:10.1038/s41598-023-42090-5, p.9]；[doi:10.1038/s41598-023-42090-5, p.10]
- **limitations：** AF2Composite 依赖每个体系内足够多的 decoy 来稳定估计 Z-score；模型数太少时方差会明显变大。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.11]
- **limitations：** unbound-backbone 集规模较小，尤其是 ClusPro 的统计误差偏大，因此对 precision curve 和阈值结论应保留一定保守性。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.9]；[doi:10.1038/s41598-023-42090-5, p.10]
- **method：** 先用 ProPOSE、ZDOCK 和 PIPER 在 bound-backbone 与 unbound-backbone 抗体-抗原体系上生成 docking decoy，再对 PIPER 输出用 ClusPro 做聚类后处理。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.2]；[doi:10.1038/s41598-023-42090-5, p.12]
- **method：** 将 docking 复合物的多链结构用 50-residue artificial linker 合并成单链输入 AF2，同时把模板侧链去除并用 alanine 化模板、空 MSA 和 model_1_ptm 进行推理。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.12]
- **method：** AF2Composite 的定义是把系统内标准化后的 pLDDT 与 pTMscore 直接相加，用作无需额外训练或校准的重评分指标。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.10]；[doi:10.1038/s41598-023-42090-5, p.12]
- **method：** 成功判定沿用 CAPRI 体系，综合 native contacts、interface RMSD 和 ligand RMSD 来给模型分级。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.12]
- **method：** 作者还用 AlphaFold v2.3.1 / ColabFold v1.5.2 作为 template-free 对照，并关闭 AMBER 后处理以保持比较一致。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.8]；[doi:10.1038/s41598-023-42090-5, p.12]
- **results：** AF2 重建后平均保留了 56% 的模板接触，interface RMSD 为 1.24 Å，且整体重排可达 2.82 Å，说明 AF2 会对 docking 模板做显著结构修正。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.3]
- **results：** 在总数上，AF2-generated models 的 positives 多于原始 docking 模型：bound-backbone 为 4,974 对 3,931，unbound-backbone 为 362 对 291。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.3]
- **results：** AF2Composite 能显著提升 ROC-AUC 和分类：bound-backbone 上 ProPOSE、ZDOCK、PIPER 的平均 AUC 改善分别约为 0.09、0.11、0.26，unbound-backbone 上约为 0.20、0.20、0.22。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.4]；[doi:10.1038/s41598-023-42090-5, p.6]
- **results：** 早期富集也明显增强，例如 bound-backbone 中 ZDOCK / PIPER / ClusPro 的 top-1 成功率分别由 12% / 14% / 14% 提升到 29% / 32% / 30%。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.6]
- **results：** 在 2022 年后新加入的 bound-backbone 控制集上，AF2Composite 仍能提升 ZDOCK / PIPER / ClusPro 的 top-1 到 35% / 36% / 35%，top-5 到 42% / 42% / 49%；template-free AF2-Multimer 仅为 22% / 28%。
  - 证据：[doi:10.1038/s41598-023-42090-5, p.8]

## 页码证据

- [doi:10.1038/s41598-023-42090-5, p.1]
- [doi:10.1038/s41598-023-42090-5, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
