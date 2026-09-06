# HydrogelFinder: A Foundation Model for Efficient Self‐Assembling Peptide Discovery Guided by Non‐Peptidal Small Molecules

- **论文 ID：** `EVIW-C75DCBB690B8C2D3`
- **期刊 / 来源：** Adv Sci (Weinh)
- **发表时间：** 2024 May 5
- **DOI：** [10.1002/advs.202400829](https://doi.org/10.1002/advs.202400829)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `语言模型`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 HydrogelFinder，将文献挖掘、Transformer 生成模型、虚拟筛选和湿实验验证串联成闭环；通过引入非肽小分子扩展化学空间，生成并筛选出新的自组装肽候选，并实验确认其中多个分子可形成水凝胶且具有较好生物相容性。

## 创新边界

`创新边界主要是文献驱动的生成式自组装肽发现流程，而不是独立证明全局首创或完整解决 3D 结构建模。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在仅依赖分子结构信息、且面对肽序列空间与非肽小分子修饰高度多样的情况下，如何高效发现并验证可自组装形成水凝胶的肽分子。

## 方法

- HydrogelFinder-mining 从文献结构图构建 HYDROGEL-POSITIVE，包含肽和非肽小分子。 HydrogelFinder-GPT 先在 ChEMBL 小分子上做自回归预训练，再在正例上微调；HydrogelFinder-predict 用 2048-bit ECFP 的概率 SVM 过滤。 从 2000 个生成分子得到 111 个未报道候选，合成 17 个并进行成胶、流变、显微、光谱和细胞实验。

## 数据与基准

- 正例库共 2669 条：1292 个自组装肽和 1377 个自组装非肽小分子；公开数据库声明为 http://hydrogeldb.com。 SVM 正负数据高度不平衡，以重复采样平衡；生成器测试集 271 个正例。

## 比较基线

- CGMD aggregation propensity 与仅序列传统 ML 是主要被比较路径。 预训练缺失、非肽小分子缺失等消融用于评估各模块。

## 结果证据

- 17 个合成候选中 9 个在水相自组装成胶，覆盖 1-10 个氨基酸；完整流程约 19 天。 SVM 在其测试集报告 AUROC 0.9862；生成模型在 FCD 等指标总体优于消融版本。 随机选取的 2 个设计在论文细胞实验中表现低细胞毒性/生物相容性；所有含 proline 的测试肽均未成胶。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 实验验证仅 17 个候选，细胞相容性仅随机选 2 个，不能代表所有生成物安全性。 正负样本高度不平衡并通过上采样处理；AUROC 可能无法反映真实低阳性率下的 precision。 数据声明称详细数据需向作者请求；未发现明确开源代码入口。 proline 失败与训练库稀缺提示化学空间偏差，且成胶受 pH/修饰条件影响。

## 仍未知

- 111 个候选中哪些具体序列最关键、其完整清单与筛选规则在冻结文本中并不完整。
- hydrogeldb.com 的长期可访问性、内容完整性与是否提供可下载代码未被冻结材料验证。
- 训练标签由图像识别与文献归类生成，具体误差率和人工校正比例未知。
- 除文中展示的样本外，更多失败实验与负结果是否存在未披露，未知。

## Pi 结构化证据摘录

- **baseline：** 与仅 pre-training 或不引入 self-assembling small molecules 的设定相比，HydrogelFinder-GPT 在 active、unique 和 novel 上整体更优，尤其 active 从 1.99% 提升到 73.98%。
  - 证据：[doi:10.1002/advs.202400829, p.4]；[doi:10.1002/advs.202400829, p.10]
- **baseline：** MOSES 风格指标上，HydrogelFinder-GPT 的 FCD 为 4.9586，显著优于 pre-training 的 33.7017。
  - 证据：[doi:10.1002/advs.202400829, p.10]
- **baseline：** 作者也指出，在没有 small molecules 的训练设定里，SNN 和 Scaff 在部分情形会更偏向 pre-training network，说明该方法不是所有相似性指标都全面碾压，而是总体更平衡。
  - 证据：[doi:10.1002/advs.202400829, p.10]
- **baseline：** 文中把先前的 MCTS+CGMD、SVM+CGMD 和 deep learning+CGMD 路线作为相关背景参照，但冻结材料未显示对这些外部方法的统一复现比较。
  - 证据：[doi:10.1002/advs.202400829, p.2]
- **data：** 训练库最终包含 2669 个正样本和 16761 个负样本，其中正样本由 1292 个 self-assembling peptides 与 1377 个 self-assembling small molecules 组成。
  - 证据：[doi:10.1002/advs.202400829, p.2]；[doi:10.1002/advs.202400829, p.9]
- **data：** 作者从生成的 2000 个候选分子中筛得 111 个此前未报道的 peptide-based candidates，并随机选择 17 个进行合成。
  - 证据：[doi:10.1002/advs.202400829, p.2]；[doi:10.1002/advs.202400829, p.4]
- **data：** 模型评估使用 HYDROGEL-POSITIVE 的 271 个测试样本，整体训练、验证、测试划分为 70/20/10。
  - 证据：[doi:10.1002/advs.202400829, p.9]；[doi:10.1002/advs.202400829, p.10]
- **data：** 实验表征覆盖 HPLC、MALDI-TOF MS、rheology、TEM、CD、FTIR、MTT 与 live/dead assay。
  - 证据：[doi:10.1002/advs.202400829, p.10]；[doi:10.1002/advs.202400829, p.11]；[doi:10.1002/advs.202400829, p.8]
- **declared_resources：** 论文建立并公开了 hydrogel 资源网站 hydrogeldb.com，供社区检索候选分子。
  - 证据：[doi:10.1002/advs.202400829, p.2]
- **declared_resources：** 预训练资源来自 ChEMBL v25 的约 300000 个分子；负样本资源来自 CPPsite 与 ZINC。
  - 证据：[doi:10.1002/advs.202400829, p.9]
- **declared_resources：** 训练与推理使用 40GB NVIDIA V100，预训练耗时约 36 小时。
  - 证据：[doi:10.1002/advs.202400829, p.10]
- **declared_resources：** 实验资源包括 CS136 peptide synthesizer、HPLC、MALDI-TOF MS、Anton Parr rheometer、JEOL JEM-2100Plus、Jasco X spectropolarimeter、Nicolet In MX 与 EVOS FL Auto。
  - 证据：[doi:10.1002/advs.202400829, p.10]；[doi:10.1002/advs.202400829, p.11]；[doi:10.1002/advs.202400829, p.8]
- **limitations：** 作者明确承认 Transformer 主要擅长 1D sequence 信息，难以充分捕捉 peptide chain 的 3D 复杂性，因此正在开发 geometric deep learning。
  - 证据：[doi:10.1002/advs.202400829, p.8]
- **limitations：** 训练标签来自文献图像抽取和作者的正负样本归类，这条标注链路对识别误差与原始文献表述高度敏感。
  - 证据：[doi:10.1002/advs.202400829, p.9]
- **limitations：** 实验验证只覆盖 17 个随机候选中的 9 个成胶分子，且细胞相容性仅对 2 个代表分子做了测试，覆盖面仍然有限。
  - 证据：[doi:10.1002/advs.202400829, p.2]；[doi:10.1002/advs.202400829, p.8]
- **limitations：** 作者的数据可得性说明仅写为“upon reasonable request”，因此完整可复现数据包并未在冻结材料中公开。
  - 证据：[doi:10.1002/advs.202400829, p.11]
- **method：** HydrogelFinder 由 HydrogelFinder-mining、HydrogelFinder-GPT 和 HydrogelFinder-predict 三个模块组成，分别负责文献挖掘、分子生成与虚拟筛选。
  - 证据：[doi:10.1002/advs.202400829, p.2]
- **method：** 作者从 PubMed 检索到的 hydrogel 文献中抽取分子图像并转换为 SMILES，构建 HYDROGEL-POSITIVE；同时结合 CPPsite 与 ZINC 构建负样本集。
  - 证据：[doi:10.1002/advs.202400829, p.9]
- **method：** HydrogelFinder-GPT 采用 Transformer decoder，先在 ChEMBL v25 的约 300000 个分子上预训练，再用 HYDROGEL-POSITIVE 进行微调。
  - 证据：[doi:10.1002/advs.202400829, p.2]；[doi:10.1002/advs.202400829, p.9]
- **method：** HydrogelFinder-predict 使用基于 2048-bit ECFP 的概率 SVM 做活性判别，测试集 AUROC 达到 0.9862。
  - 证据：[doi:10.1002/advs.202400829, p.10]
- **results：** HydrogelFinder-GPT 的 active rate 为 73.98%，明显高于 pre-training 网络的 1.99%，也优于其他训练策略。
  - 证据：[doi:10.1002/advs.202400829, p.4]；[doi:10.1002/advs.202400829, p.10]
- **results：** 在 structural diversity 上，加入 non-peptidal small molecules 后模型得分 0.803，高于移除该部分数据后的 0.757。
  - 证据：[doi:10.1002/advs.202400829, p.4]
- **results：** 111 个 peptide-based candidates 的长度覆盖 1–14 个 amino acids，实验上 17 个候选里有 9 个能够 self-assemble 成 hydrogel。
  - 证据：[doi:10.1002/advs.202400829, p.4]；[doi:10.1002/advs.202400829, p.6]
- **results：** Rheology、TEM、CD 与 FTIR 一致支持若干候选形成以 β-sheet 为主的纳米纤维水凝胶网络。
  - 证据：[doi:10.1002/advs.202400829, p.6]；[doi:10.1002/advs.202400829, p.7]
- **results：** 两种代表性水凝胶的 MTT 和 live/dead 结果显示出较低毒性与较好的细胞相容性。
  - 证据：[doi:10.1002/advs.202400829, p.8]

## 页码证据

- [doi:10.1002/advs.202400829, p.10]
- [doi:10.1002/advs.202400829, p.11]
- [doi:10.1002/advs.202400829, p.1]
- [doi:10.1002/advs.202400829, p.2]
- [doi:10.1002/advs.202400829, p.6]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
