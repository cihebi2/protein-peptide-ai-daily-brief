# Protein stability prediction by fine-tuning a protein language model on a mega-scale dataset

- **论文 ID：** `EVIW-81ABABCCA0141DCD`
- **期刊 / 来源：** PLoS Comput Biol
- **发表时间：** 2024 Jul 22
- **DOI：** [10.1371/journal.pcbi.1012248](https://doi.org/10.1371/journal.pcbi.1012248)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `语言模型` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 ESMtherm：将预训练 ESM-2 在 mega-scale stability dataset 上端到端微调成稳定性回归器，声称可处理 deletions、insertions 和 multiple-point mutations，并能在小型蛋白域上实现可观泛化。

## 创新边界

`创新主要在于把现成 pLM 微调用于稳定性预测与跨域评测；它不是新湿实验，也不是候选蛋白生成或优化方法。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何利用蛋白语言模型从大规模稳定性数据中学习，并对未见过的蛋白域乃至更长蛋白的 folding stability / ΔG 做可靠预测，同时尽量提升跨域泛化能力。

## 方法

- 以Tsuboyama大规模稳定性数据微调ESM-2回归；按蛋白域拆分测试，并按与训练域最高序列一致性分析泛化。

## 数据与基准

- 训练52.8万条天然与de novo短序列、461个蛋白域；原始数据总计约77.6万序列、479个小域；测试含47个仅测试域。

## 比较基线

- Rosetta、FoldX、RaSP、ELASPIC-2及其他稳定性预测器。

## 结果证据

- 仅测试域的Spearman从约0.2至0.9不等且随相似性降低而变差；模型对短域表现合理，但在大支架上弱于部分结构方法。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 训练分布偏向短小蛋白域；即使域隔离，测试域仍可能与训练域高相似；论文明确指出较大蛋白支架泛化不足。

## 仍未知

- 代码仓库的精确链接与可复现状态未在冻结证据中核验。
- 长蛋白性能下降究竟主要来自长度偏置、实验差异还是分布漂移，作者仅提出假说。
- 作者未提供独立 prior-art 证据，因此 global novelty 不能验证。

## Pi 结构化证据摘录

- **baseline：** 文中主要 baseline 是 Rosetta Cartesian ΔΔG、MUPro、RaSP、ELASPIC-2 以及未微调的 ESM-2。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.6]；[doi:10.1371/journal.pcbi.1012248, p.7]
- **baseline：** 对照实验还包括“只在最近训练域上学习”与“多域联合学习”两种训练范式，用来检验 transfer learning 相对 collective training 的收益。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.5]
- **baseline：** 在更长蛋白 benchmark 上，作者把结果与 ProteinGym 相关 DMS 任务和 BglB 的独立数据集直接比较，以检验跨 assay 的可迁移性。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.6]；[doi:10.1371/journal.pcbi.1012248, p.9]
- **data：** 原始 mega-scale 数据含约 1.8M measurements、542 个 domains；过滤后保留 527,785 protein sequences，对应 258 natural 和 203 de novo domains。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.8]；[doi:10.1371/journal.pcbi.1012248, p.9]
- **data：** 外部 benchmark 包括 mega-scale、BglB、Bgl3、Acetyltransferase、Lipase EstA、PTEN 和 Methyltransferase，序列规模从 157 到 100,794 不等。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.6]
- **data：** 这些数据覆盖 cDNA display proteolysis、melting temperature、chemical stability、protein abundance 以及 catalytic susceptibility to heat shock 等不同读出。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.6]；[doi:10.1371/journal.pcbi.1012248, p.9]
- **declared_resources：** 作者声明代码和 materials 维护在 GitHub，且 mutant-level predictions 与 benchmark evaluation 放在 Supplementary Materials。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.1]
- **declared_resources：** 训练资源包括 A100 GPU、half precision、global batch size 2048 和 patience 500 steps。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.8]
- **declared_resources：** 作者使用的预训练底座是 ESM-2（UniRef50 预训练），并在 8M/35M/150M/650M 中选择 35M 模型；补充材料还提供 S1 Spreadsheet 和 S2 Spreadsheet。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.8]；[doi:10.1371/journal.pcbi.1012248, p.9]
- **limitations：** 模型只在 40–72 aa 的短 domains 上训练，因此对 177–501 aa 的 larger proteins 泛化明显较弱。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.6]；[doi:10.1371/journal.pcbi.1012248, p.7]
- **limitations：** 作者怀疑模型可能偏向数据集特异细节、实验条件和短序列分布，而不只是 folding stability 本身。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.7]
- **limitations：** ΔG 预测存在明显 offset 和 scale mismatch；若不做 per-domain recalibration，绝对数值解释会受限。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.7]
- **method：** 作者以预训练 ESM-2 为 backbone，将蛋白整序列输入到回归任务，并在起始 token 上接分类头，端到端微调整个参数集。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.8]
- **method：** 他们在 8M、35M、150M、650M 四种模型规模间做选择，最终采用 35M 参数模型以平衡性能与计算开销，并报告预训练优于随机初始化。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.8]
- **method：** 训练数据来自 Tsuboyama 的 mega-scale stability 测量：先按相同蛋白序列聚合，再按 ΔG / log K50 的标准差阈值过滤，只保留每个序列至少 100 条测量的 domains。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.8]；[doi:10.1371/journal.pcbi.1012248, p.9]
- **method：** 数据按 wildtype domain 划分为 train/validation/test，并将 10% domains 的全部 mutants 放入 test-set-only partition，其余 domains 以 80/10/10 随机分配。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.9]
- **method：** 为比较跨域泛化，作者用 MMseqs2 做 sequence alignment、用 Foldseek 做 structural alignment，把测试域匹配到训练集最近邻，再做 pairwise 比较与 Wilcoxon 检验。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.9]
- **method：** 外部 benchmark 覆盖七个 DMS 数据集，用于比较 direct 与 indirect stability measurements 的表现。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.6]；[doi:10.1371/journal.pcbi.1012248, p.9]
- **results：** ESMtherm 在 47 个 test-set-only domains 上总体还能保持中等泛化，域级 Spearman's R 约 0.2 到 0.9，唯独 yahO 表现很差。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.3]
- **results：** 在 13 个与训练集无序列比对（e-value < 10^-3）的案例中，模型仍可对自然蛋白和 de novo designs 给出合理相关，例如 1AOY、HEEH_KT_rd6_0790 和 r11_233_TrROS_Hall。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.3]；[doi:10.1371/journal.pcbi.1012248, p.4]
- **results：** 多域联合训练比只学最近的单域更好，test-set-only domains 的 Spearman's R 平均提升 0.16（p=6×10^-3），CdnL 等例子提升明显。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.5]
- **results：** 在 mega-scale dataset 上，ESMtherm 的 Spearman's R 为 0.65，接近 RaSP/ELASPIC-2 的 0.64，也高于 Rosetta 的 0.61 和 MUPro 的 0.31。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.6]
- **results：** 在更长蛋白的外部数据集上，ESMtherm 整体失效或明显落后；作者指出 ELASPIC-2 往往最好，而 ESMtherm 对这些数据几乎不相关。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.7]
- **results：** 对同尺寸 ESM-2，监督微调把相关性从 0.36 提升到 0.65；对 test-set-only domains 做 per-domain 线性重标定后，RMSE 从 1.34 降到 0.83、R2 从 -0.85 提到 0.45。
  - 证据：[doi:10.1371/journal.pcbi.1012248, p.7]

## 页码证据

- [doi:10.1371/journal.pcbi.1012248, p.1]
- [doi:10.1371/journal.pcbi.1012248, p.2]
- [doi:10.1371/journal.pcbi.1012248, p.3]
- [doi:10.1371/journal.pcbi.1012248, p.4]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
