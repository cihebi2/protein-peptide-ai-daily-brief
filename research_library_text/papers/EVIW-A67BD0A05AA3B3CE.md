# Protein language model-embedded geometric graphs power inter-protein contact prediction

- **论文 ID：** `EVIW-A67BD0A05AA3B3CE`
- **期刊 / 来源：** eLife
- **发表时间：** 2024 Apr 2
- **DOI：** [10.7554/elife.92184](https://doi.org/10.7554/elife.92184)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `语言模型` / `图与几何学习`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 PLMGraph-Inter：把 SE(3) invariant geometric graphs 与多种 protein language models 结合，再经 GVP/GVPConv 与 dimensional hybrid residual blocks 预测 inter-protein contact map，并报告其在多套基准上优于既有方法且可辅助 AlphaFold-Multimer 与 HADDOCK。

## 创新边界

`新意主要限于结构感知的 inter-protein contact prediction 及其 docking 辅助，不是端到端蛋白复合体生成，也未做全球 prior-art 充分验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在给定两个蛋白单体结构或其预测结构时，如何更准确地预测 inter-protein contacts，并进一步用于辅助蛋白复合物结构预测与 docking。

## 方法

- 两单体残基图经GVP编码，PLM特征和跨链pair表示进入2D residual网络输出contact map，并作为HADDOCK约束。

## 数据与基准

- 多个PPI接触测试集，实验或预测单体结构输入。

## 比较基线

- 上述五种contact模型、AF-M和无PLM/结构消融。

## 结果证据

- 论文报告大幅超过DeepHomo、GLINTER、CDPred、DeepHomo2、DRN，并改善部分docking；高precision contacts仍不保证HADDOCK成功。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 历史benchmark折叠冗余可抬高结果；依赖单体结构，contact正确也可能因柔性/ranking docking失败。

## 仍未知

- 未独立复现训练、推理与 docking 流程。
- 仓库许可证与依赖锁定情况未在论文页内完整说明。
- 在真实、低同源、低 contact density 的 heteromeric 场景中的泛化仍不确定。
- 与 AlphaFold-Multimer 的比较受模板检索与数据库差异影响，严格公平性未知。

## Pi 结构化证据摘录

- **baseline：** 主要对比基线包括 DeepHomo、GLINTER、CDPred、DeepHomo2、DRN-1D2D_Inter；复合体结构预测部分还对比了 AlphaFold-Multimer 与 HADDOCK ab initio。
  - 证据：[doi:10.7554/eLife.92184, p.5]；[doi:10.7554/eLife.92184, p.12]；[doi:10.7554/eLife.92184, p.15]
- **baseline：** 结构表示的额外对照是 GVP Graph，用于说明作者自己的 geometric graph 设计更有效。
  - 证据：[doi:10.7554/eLife.92184, p.10]
- **data：** 训练集包含 7362 个 PPIs；独立测试集为 HomoPDB 400 个 homodimers、HeteroPDB 200 个 heterodimers；另有 DHTest 130 个 homomeric PPIs 和 DB5.5 59 个 heteromeric PPIs，均按 40% sequence identity 去冗余。
  - 证据：[doi:10.7554/eLife.92184, p.18]
- **data：** 评测既使用实验单体结构，也使用 AlphaFold2 预测单体结构；后者仅用 UniRef100、关闭 template，平均 TM-score 为 0.88。
  - 证据：[doi:10.7554/eLife.92184, p.5]
- **declared_resources：** 计算资源包括 Huazhong University of Science and Technology 的 HPC 平台和 1 张 NVIDIA TESLA A100 GPU；实现基于 pytorch 1.11。
  - 证据：[doi:10.7554/eLife.92184, p.20]；[doi:10.7554/eLife.92184, p.21]
- **declared_resources：** 数据与代码在 GitHub 提供，并有 Software Heritage 归档；流程依赖 UniRef100、ESM/ESM-MSA-1b、ESM-IF、HH-suite3、CCMpred、HADDOCK 等工具。
  - 证据：[doi:10.7554/eLife.92184, p.19]；[doi:10.7554/eLife.92184, p.22]；[doi:10.7554/eLife.92184, p.24]
- **limitations：** 作者明确指出 heteromeric PPIs 仍有较大提升空间；较低 contact density、较低 DTM-score 或较差单体结构质量都会降低准确率。
  - 证据：[doi:10.7554/eLife.92184, p.9]；[doi:10.7554/eLife.92184, p.13]；[doi:10.7554/eLife.92184, p.17]
- **limitations：** 更严格的 fold similarity 去冗余后，HomoPDB 性能下降较多，提示跨 fold 泛化仍有限。
  - 证据：[doi:10.7554/eLife.92184, p.11]
- **limitations：** HADDOCK 无法很好处理大的构象重排，部分高精度 contacts 仍会导致 docking 失败；与 AlphaFold-Multimer 的比较也不完全同 footing，因为后者使用更多模板和更大的数据库。
  - 证据：[doi:10.7554/eLife.92184, p.13]；[doi:10.7554/eLife.92184, p.17]
- **limitations：** 部分对照评测存在乐观偏差风险：GLINTER 在一些目标上运行报错，CDPred 的 DHTest 与其训练集完全重叠。
  - 证据：[doi:10.7554/eLife.92184, p.5]；[doi:10.7554/eLife.92184, p.12]
- **method：** 先把每个单体结构表示为 SE(3) invariant geometric graph，再用 GVP/GVPConv 编码，最后接 dimensional hybrid residual blocks 输出 contact map。
  - 证据：[doi:10.7554/eLife.92184, p.3]；[doi:10.7554/eLife.92184, p.4]；[doi:10.7554/eLife.92184, p.18]；[doi:10.7554/eLife.92184, p.19]；[doi:10.7554/eLife.92184, p.20]
- **method：** 节点特征融合了 ESM-1b、ESM-MSA-1b、PSSM 和 ESM-IF，2D 特征来自 paired MSA 的 CCMpred、alnstats、attention maps 以及 coevolution 信息。
  - 证据：[doi:10.7554/eLife.92184, p.4]；[doi:10.7554/eLife.92184, p.19]
- **method：** 训练采用 7-fold cross-validation、AdamW、A100 GPU，且序列长度上限为 400。
  - 证据：[doi:10.7554/eLife.92184, p.20]
- **results：** 在 HomoPDB 上，PLMGraph-Inter 的 top50 mean precision 达到 67.3%（实验结构）和 60.9%（预测结构）；在 HeteroPDB 上分别为 41.4% 和 37.8%，整体优于 DeepHomo、GLINTER、CDPred、DeepHomo2 和 DRN-1D2D_Inter。
  - 证据：[doi:10.7554/eLife.92184, p.5]
- **results：** 在 DHTest / DB5.5 上，PLMGraph-Inter 的 top50 mean precision 为 71.9% / 29.5%；使用预测结构时降至 61.1% / 23.8%，作者也报告更严格 fold 去冗余会让 HomoPDB 下降更明显。
  - 证据：[doi:10.7554/eLife.92184, p.12]；[doi:10.7554/eLife.92184, p.13]；[doi:10.7554/eLife.92184, p.11]
- **results：** 与 AlphaFold-Multimer 比较时，PLMGraph-Inter 在 AF-Multimer 失败子集上仍能给出更高接触精度；把其 contacts 作为 HADDOCK 约束后，homodimer top1 成功率从 15.37% 提升到 57.58%，heterodimer 从 1.72% 提升到 29.89%。
  - 证据：[doi:10.7554/eLife.92184, p.15]；[doi:10.7554/eLife.92184, p.16]；[doi:10.7554/eLife.92184, p.17]
- **results：** 消融结果显示几何图、sequence embeddings、MSA 1D/2D 特征与 ESM-IF 都有贡献，且作者自定义几何图优于 GVP Graph 对照。
  - 证据：[doi:10.7554/eLife.92184, p.9]；[doi:10.7554/eLife.92184, p.10]

## 页码证据

- [doi:10.7554/elife.92184, p.11]
- [doi:10.7554/elife.92184, p.17]
- [doi:10.7554/elife.92184, p.1]
- [doi:10.7554/elife.92184, p.22]
- [doi:10.7554/elife.92184, p.3]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
