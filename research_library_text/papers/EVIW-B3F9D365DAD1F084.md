# A multimodal Transformer Network for protein-small molecule interactions enhances predictions of kinase inhibition and enzyme-substrate relationships

- **论文 ID：** `EVIW-B3F9D365DAD1F084`
- **期刊 / 来源：** PLoS Comput Biol
- **发表时间：** 2024 May 20
- **DOI：** [10.1371/journal.pcbi.1012100](https://doi.org/10.1371/journal.pcbi.1012100)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称提出 ProSmith：将蛋白 amino acid sequence 与小分子 SMILES 放入同一 multimodal Transformer 生成 joint representation，并结合三路 XGBoost 集成 cls token、ESM-1b/ChemBERTa2 压缩向量和全量特征，在 DTA、enzyme-substrate 与 Km 三类任务上优于既有方法。

## 创新边界

`主要新意在跨模态早融合的 Transformer 表征与后续梯度提升集成；它是预测/排序型方法，不是候选生成、优化或 docking 系统。作者自称“首个”可同时处理不同模态分子的 Transformer，但冻结证据中没有独立 prior-art 核验。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何在蛋白序列与小分子结构同时参与表征生成时尽量保留跨模态信息交换，从而提升蛋白-小分子相互作用、亲和力与酶底物关系预测的泛化能力，尤其是对未见蛋白或未见小分子的泛化。

## 方法

- 蛋白词元用ESM-1b表示，分子词元用ChemBERTa2表示，映射到768维后经6层、每层6头Transformer联合编码；提取CLS后与独立ESM/ChemBERTa向量分别训练XGBoost，按验证集权重集成。

## 数据与基准

- 覆盖激酶抑制/DTA、酶-底物分类和Km回归。酶-底物实验集训练55418、测试13336，正负比1:3且测试酶与训练酶序列一致性不超过80%；扩展预训练集850291。ESM-1b预训练约2700万蛋白序列，ChemBERTa2预训练约7700万SMILES。

## 比较基线

- DTA对比NHGNN-DTA等；酶-底物任务沿用ESP数据与基线；最终模型还与仅CLS、仅ESM+ChemBERTa及全特征单模型做组合/消融比较。

## 结果证据

- 论文报告ProSmith在训练外相异激酶、酶-底物分类和Km预测上总体优于所选近期基线；酶-底物任务利用跨模态信息与大规模扩展训练受益明显。作者也承认随机划分时ProSmith的CI略低于NHGNN-DTA，只是在MSE和r_m^2上更好，因此不能概括为所有指标全胜。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 由于计算成本没有为每项任务充分调参，只使用6层并复用同一Transformer超参数；ESM-1b/ChemBERTa2权重冻结；特定蛋白家族数据足够时专用模型可能更强，小数据任务受益较小。

## 仍未知

- 未独立核验论文声称的 GitHub 代码仓库内容与可复现性
- 未独立核验 Zenodo/数据下载的实际可用性
- “首个可同时处理不同模态分子”的新颖性主张在冻结证据中没有外部 prior-art 复核

## Pi 结构化证据摘录

- **baseline：** Davis random split 的对照包括 DeepDTA、MT-DTI、GraphDTA、GEFA、rzMLP、Ensemble DLM、FusionDTA、MgraphDTA 和 NHGNN-DTA；ProSmith 在 MSE 与 r2m 上领先。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.8]
- **baseline：** Davis 的 cold target、cold drug 和 cold drug&target 对照沿用 GraphDTA、GEFA、FusionDTA、MgraphDTA、NHGNN-DTA 等方法；ProSmith 在前两类冷启动设定上总体最好，在 cold drug 上是混合结果。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.9]
- **baseline：** enzyme-substrate 任务的直接基线是 ESP，ProSmith 在 accuracy、MCC 和 ROC-AUC 三项都更高。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.11]
- **baseline：** Km 任务的基线包括 Kroll et al. (2021) 与 ENKIE (2022)，ProSmith 在报告的 MSE、R2 和 Pearson r 上都更优。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.12]
- **data：** Davis 数据集包含 30,056 个 kinase-drug 配对、72 个 drugs 和 442 个 target proteins，目标值用 Kd 的 log 变换 pKd 表示，并按 random、cold target、cold drug、cold drug&target 四种方案重复五次划分。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.7]；[doi:10.1371/journal.pcbi.1012100, p.8]；[doi:10.1371/journal.pcbi.1012100, p.9]
- **data：** IC50 预训练集来自 BindingDB，剔除 Davis 中出现过的 drugs 和 targets 后得到 1,039,565 条记录，并按 95%/5% 划分训练和验证。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.18]
- **data：** enzyme-substrate 任务使用的 ESP 数据集有 55,418 条训练样本和 13,336 条测试样本，正负比为 1:3；作者还把带 phylogenetic evidence 的训练数据扩到 850,291 条，但测试集不变。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.10]
- **data：** Km 任务的数据集包含 11,676 条实验测量值，按 80%/20% 划分训练和测试，并把原始训练集再切成 90%/10% 作为训练与验证。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.12]
- **declared_resources：** 实现栈明确写为 Python、PyTorch、XGBoost，超参数搜索使用 hyperopt；token embedding 依赖预训练的 ESM-1b 与 ChemBERTa2。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.16]；[doi:10.1371/journal.pcbi.1012100, p.18]
- **declared_resources：** 训练主要在 Heinrich Heine University Düsseldorf 的 HPC cluster 上使用单张 NVIDIA A100 GPU 完成；IC50 预训练因数据量大改用四张 A100。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.18]；[doi:10.1371/journal.pcbi.1012100, p.19]
- **declared_resources：** 论文声称代码可在 GitHub 获取，并给出 GitHub 与 Zenodo 的数据/代码入口。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.1]；[doi:10.1371/journal.pcbi.1012100, p.16]
- **limitations：** 作者明确承认，由于算力和时间限制，Transformer 不能做完整的超参数搜索；6 层结构主要靠 trial-and-error 选出，而且同一组 Transformer 超参数被复用到多个任务。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.6]；[doi:10.1371/journal.pcbi.1012100, p.15]
- **limitations：** 模型对训练数据规模很敏感：DTA 中测试 drug 若在训练集出现太少，性能会很低；enzyme-substrate 任务对稀有 substrate 也类似；Km 任务由于样本更少，整体增益更小。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.8]；[doi:10.1371/journal.pcbi.1012100, p.11]；[doi:10.1371/journal.pcbi.1012100, p.12]；[doi:10.1371/journal.pcbi.1012100, p.15]
- **limitations：** 输入长度存在硬截断：protein 最多保留 1024 个 amino acids，SMILES 最多保留 256 个 token，超长序列会丢失信息。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.17]
- **limitations：** 作者没有在 ProSmith 训练中微调 ESM-1b 和 ChemBERTa2 的参数，并建议未来把这些 embedding 与主模型一起联合微调。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.15]
- **method：** ProSmith 先把蛋白 amino acid sequence token 和 SMILES token 拼成同一输入序列，加入 cls 与 sep token，让两种模态在同一个 BERT-like Transformer 里通过 attention 直接交互。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.3]；[doi:10.1371/journal.pcbi.1012100, p.5]；[doi:10.1371/journal.pcbi.1012100, p.17]
- **method：** 蛋白 token 来自 ESM-1b 的 1280 维表示，小分子 token 来自 ChemBERTa2 的 600 维表示；两者先经 pooling/linear 映射到 768 维共享空间，再送入 6 层、6 heads 的 Transformer。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.4]；[doi:10.1371/journal.pcbi.1012100, p.16]；[doi:10.1371/journal.pcbi.1012100, p.17]
- **method：** Transformer 输出的 cls token 被送入全连接头做回归或二分类训练，训练过程端到端进行，并用验证集 early stopping 选取最好 epoch。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.5]；[doi:10.1371/journal.pcbi.1012100, p.17]
- **method：** 最终预测不是只用单个头，而是训练三路 XGBoost：仅 cls、仅 ESM-1b/ChemBERTa2 压缩向量、以及三者拼接，再按验证集调权重做加权平均。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.5]；[doi:10.1371/journal.pcbi.1012100, p.6]；[doi:10.1371/journal.pcbi.1012100, p.13]；[doi:10.1371/journal.pcbi.1012100, p.14]
- **method：** DTA 任务还先在 BindingDB 的 IC50 大样本上预训练 Transformer，Km 任务则先用 enzyme-substrate 任务参数初始化，以缓解小数据训练问题。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.7]；[doi:10.1371/journal.pcbi.1012100, p.12]；[doi:10.1371/journal.pcbi.1012100, p.18]
- **results：** 在 Davis random split 上，ProSmith 达到 MSE 0.186、CI 0.911、r2m 0.760；它在 MSE 和 r2m 上优于 NHGNN-DTA，但 CI 略低于 NHGNN-DTA。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.8]
- **results：** 在 Davis 的 cold target 与 cold drug&target 场景下，ProSmith 在三项指标上都明显优于先前方法；在 cold drug 场景下，它的 MSE 和 CI 略逊于 NHGNN-DTA，但 r2m 最好。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.9]
- **results：** enzyme-substrate 预测上，ProSmith 把 accuracy 提到 94.2%、MCC 提到 0.85、ROC-AUC 提到 0.972，明显高于 ESP 的 91.5%、0.78 和 0.956。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.11]
- **results：** Km 预测上，ProSmith 达到 MSE 0.604、R2 0.563、Pearson r 0.752，优于 Kroll et al. 2021 和 ENKIE 在论文中报告的对照结果。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.12]
- **results：** 作者还报告，ProSmith 对稀有或未见的 drug、substrate 和远缘 enzyme 改善更明显，但这些收益强依赖训练集中是否存在足够相似的样本。
  - 证据：[doi:10.1371/journal.pcbi.1012100, p.8]；[doi:10.1371/journal.pcbi.1012100, p.11]；[doi:10.1371/journal.pcbi.1012100, p.12]

## 页码证据

- [doi:10.1371/journal.pcbi.1012100, p.10]
- [doi:10.1371/journal.pcbi.1012100, p.13]
- [doi:10.1371/journal.pcbi.1012100, p.15]
- [doi:10.1371/journal.pcbi.1012100, p.16]
- [doi:10.1371/journal.pcbi.1012100, p.1]
- [doi:10.1371/journal.pcbi.1012100, p.4]
- [doi:10.1371/journal.pcbi.1012100, p.5]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
