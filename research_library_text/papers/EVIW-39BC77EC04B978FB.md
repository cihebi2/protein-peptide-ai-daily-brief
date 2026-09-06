# AnnoPRO: a strategy for protein function annotation based on multi-scale protein representation and a hybrid deep learning of dual-path encoding

- **论文 ID：** `EVIW-39BC77EC04B978FB`
- **期刊 / 来源：** Genome Biol
- **发表时间：** 2024 Feb 1
- **DOI：** [10.1186/s13059-024-03166-1](https://doi.org/10.1186/s13059-024-03166-1)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `数据集/基准`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 AnnoPRO：先用 PROFEAT 构建多尺度表示 ProMAP/ProSIM，再用 7C-CNN 与 5FC-DNN 进行预训练，最后以三层 LSTM 完成 6,109 个 GO 家族的多标签功能注释，并声称在多组 benchmark 上优于现有方法。

## 创新边界

`就冻结证据看，这是一套面向功能注释的预测框架改进，不是蛋白生成、设计或优化；创新边界主要在表示学习与分类流水线，全球首创性未被独立验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

解决蛋白功能注释中的 long-tail 问题：大量 GO 家族标注极少，导致现有 sequence homology 与机器学习方法在尾部标签、跨物种新蛋白，以及同源但功能不同的蛋白上表现下降。

## 方法

- 蛋白序列以多尺度片段与全局表示编码，两个预训练路径融合后由LSTM按GO结构/标签序列解码。

## 数据与基准

- GO/Swiss-Prot类功能数据，多组公开benchmark和独立测试，按head/middle/tail标签层级评价。

## 比较基线

- DeepGOPlus、PFmulDL、NetGO3及序列同源方法，另有双路径/多尺度消融。

## 结果证据

- 论文报告在多benchmark尤其tail labels上优于DeepGOPlus/PFmulDL等；仍是计算功能注释。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- GO长尾和不完整标签仍存在；部分比较因NetGO3缺源代码未纳入统一重训，UMAP解释有限。

## 仍未知

- NetGO2/NetGO3 等方法的比较受源码不可完全获取影响。
- 冻结材料未提供独立外部复现实验或湿实验验证。
- global_novelty 只能按论文陈述判断，未做独立文献/专利检索。

## Pi 结构化证据摘录

- **baseline：** 整体对比对象包括 DiamondBLAST、DeepGO、DeepGOCNN、DeepGOPlus、TALE、PFmulDL、NetGO2 与 NetGO3；作者把 DeepGOPlus、PFmulDL、NetGO3 视为更强基线。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.6]；[doi:10.1186/s13059-024-03166-1, p.8]
- **baseline：** 文中也明确指出，sequence homology 方法如 BLAST 和 GoFDR 在序列 identity 下降后准确率会快速衰减，因此需要 ML 基线来处理低同源场景。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.3]
- **baseline：** 在独立测试与分层分析之外，作者还用 DeepGOPlus、PFmulDL 和 NetGO3 做重点对比，但 NetGO3 因源码不可用未能按相同流程重训。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.8]；[doi:10.1186/s13059-024-03166-1, p.9]
- **baseline：** 在 PROBE 与 ontology-based PFP benchmark 上，作者又将 AnnoPRO 与 DeepGOPlus、PFmulDL，以及原文中的 BPM 进行对比。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.14]；[doi:10.1186/s13059-024-03166-1, p.15]
- **data：** 模型构建主要使用 CAFA4 的 92,120 条蛋白序列，并仅保留蛋白数大于 50 的 6,109 个非重复 GO families；GO 层级从 LEVEL 1 到 LEVEL 11 组织。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.6]；[doi:10.1186/s13059-024-03166-1, p.16]
- **data：** 独立测试集采用 5,623 条带实验注释的 SwissProt 蛋白，时间范围为 2019-10-22 到 2022-05-31，并划分为 1,859 条 SameSP 与 3,764 条 DiffSP。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.6]；[doi:10.1186/s13059-024-03166-1, p.9]
- **data：** 稳定性验证还使用了 PROBE 数据集，共 20,421 条 human proteins，并按同样 cutoff 划分为 18,058 条训练/验证与 2,363 条独立测试。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.14]
- **data：** 作者还在 ontology-based PFP benchmark 上做了五折比较，该 benchmark 含 25 个子数据集与 18 个 GO categories。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.14]；[doi:10.1186/s13059-024-03166-1, p.15]
- **declared_resources：** 作者声明 AnnoPRO 的 source code、models、web server 与 PyPI package 已公开，且 GitHub 与 Zenodo 均标注为 MIT license。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.20]
- **declared_resources：** CAFA4 的可用数据可从项目网站下载，作者也给出了用于训练和测试的公开入口。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.20]
- **declared_resources：** 用于稳定性验证的 PROBE 与 ontology-based PFP benchmark 来自既有研究，文中将其作为额外 benchmark 引用。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.14]；[doi:10.1186/s13059-024-03166-1, p.20]
- **declared_resources：** 补充材料包含 ablation、UMAP/PCA、HSPA 案例与超参数等支持性结果，便于理解模型行为。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.19]；[doi:10.1186/s13059-024-03166-1, p.20]
- **limitations：** 作者把蛋白数不超过 50 的 GO families 排除在训练之外，因此对极端稀有标签的覆盖仍然有限。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.16]
- **limitations：** 层级评估显示，AnnoPRO 主要是在 Tail Label Levels 获益更大，而 Head Label Levels 只是大体持平，个别指标还有极小回落。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.8]
- **limitations：** 作者自己也提到 UMAP 可能带来 2D 距离扭曲，因此虽然 PCA/UMAP 结果接近，但表示学习步骤仍存在方法选择敏感性。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.7]；[doi:10.1186/s13059-024-03166-1, p.16]；[doi:10.1186/s13059-024-03166-1, p.17]；[doi:10.1186/s13059-024-03166-1, p.18]
- **limitations：** 部分强基线的源码不可完全获得，只能依赖在线服务器或作者报告结果，因而跨方法比较的可重复性仍受限制。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.6]；[doi:10.1186/s13059-024-03166-1, p.9]；[doi:10.1186/s13059-024-03166-1, p.15]
- **method：** M1 先用 PROFEAT 为每条蛋白序列生成 1,484 个描述符，再通过特征距离矩阵、UMAP/PCA 和 Jonker-Volgenant 分配，构建 39×39 的 template map 形成 ProMAP。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.17]；[doi:10.1186/s13059-024-03166-1, p.18]
- **method：** ProSIM 则基于 92,120 条蛋白的 protein distance matrix（PDM）生成，把原本独立的 1,484 维描述转为 92,120 维的全局相关表示。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.17]；[doi:10.1186/s13059-024-03166-1, p.18]
- **method：** M2 使用 7C-CNN 和 5FC-DNN 对 ProMAP/ProSIM 做 dual-path pre-training，并把两路编码拼接后进一步精炼为蛋白功能表示。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.4]；[doi:10.1186/s13059-024-03166-1, p.18]；[doi:10.1186/s13059-024-03166-1, p.19]
- **method：** M3 用三层 LSTM 对预训练后的蛋白编码进行解码，文中还给出 256 个神经元、time step 11、focal loss 与 early stopping 等训练设定。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.18]；[doi:10.1186/s13059-024-03166-1, p.19]
- **results：** 在 CAFA4 独立测试上，AnnoPRO 在 BP、CC、MF 的 Fmax 与 AUPRC 都是最优：BP 0.609/0.574，CC 0.746/0.749，MF 0.763/0.755。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.6]
- **results：** Ablation 结果显示，移除 ProMAP、ProSIM、LSTM 或单通道转换都会明显降绩效，作者报告整体下降幅度约为 Fmax 4.6–22.4% 与 AUPRC 13.6–24.2%。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.7]
- **results：** UMAP 与 PCA 两种 dimensionality reduction 的结果大体相近，UMAP 仅略优，约提升 0.6–1.9% 的 Fmax 与 1.4–2.1% 的 AUPRC。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.7]
- **results：** 在 level-based 分析中，AnnoPRO 对 Head Label Levels 基本持平或小幅领先，而对 Tail Label Levels 则在所有比较中都更好，提升幅度达到 1.7–28.2%。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.8]；[doi:10.1186/s13059-024-03166-1, p.9]
- **results：** 在 SameSP 与 DiffSP、以及 GDF8/GDF11 和 HSPA1A/HSPA2 等同源但功能不同的案例中，AnnoPRO 多数指标最好，并能更完整地恢复功能差异。
  - 证据：[doi:10.1186/s13059-024-03166-1, p.9]；[doi:10.1186/s13059-024-03166-1, p.10]；[doi:10.1186/s13059-024-03166-1, p.11]；[doi:10.1186/s13059-024-03166-1, p.12]；[doi:10.1186/s13059-024-03166-1, p.13]；[doi:10.1186/s13059-024-03166-1, p.14]

## 页码证据

- [doi:10.1186/s13059-024-03166-1, p.1]
- [doi:10.1186/s13059-024-03166-1, p.20]
- [doi:10.1186/s13059-024-03166-1, p.3]
- [doi:10.1186/s13059-024-03166-1, p.7]
- [doi:10.1186/s13059-024-03166-1, p.9]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
