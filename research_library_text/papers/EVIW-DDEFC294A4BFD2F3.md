# NIMO: A Natural Product-Inspired Molecular Generative Model Based on Conditional Transformer

- **论文 ID：** `EVIW-DDEFC294A4BFD2F3`
- **期刊 / 来源：** Molecules
- **发表时间：** 2024 Apr 19
- **DOI：** [10.3390/molecules29081867](https://doi.org/10.3390/molecules29081867)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `扩散/生成`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 NIMO：把分子图经两套 motif 提取规则转成语义 motif 序列，再用 conditional transformer 生成 NP-like 分子，并分别构建 NIMO-M 与 NIMO-S 以支持多约束生成、scaffold-based 优化和三类应用任务。

## 创新边界

`创新主要集中在 motif 序列化与条件生成管线；底层仍依赖已知的 transformer、BRICS/Murcko 断键和 beam search，因此更像 fragment-based molecular generation 的整合增强，而非全新生成范式。`。这不是全球首创性检索或独立复现结论。

## 研究问题

面向天然产物化学空间扩展，解决复杂 NP 在 stereo、多环结构下的可控 de novo 生成、scaffold 优化，以及活性/口袋导向设计问题。

## 方法

- SMILES transformer与conditional property tokens。

## 数据与基准

- natural products/ChEMBL-like molecules。

## 比较基线

- RNN/VAE/Transformer generators。

## 结果证据

- 论文报告validity/NP likeness/diversity；为计算。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- NP score/合成/活性未知。

## 仍未知

- Supplementary Materials（S1-S13）未逐页读取，表图细节只能依赖正文引用。
- GitHub 仓库内容未在本任务中外部核验，无法确认实现与正文完全一致。

## Pi 结构化证据摘录

- **baseline：** 对比方法包括 MCMG、QBMG 和 FBMG；其中 MCMG 在文中指 MCMGM，需去 stereochemistry 后训练，QBMG 允许 stereo 但不加 constraints，FBMG 为 fragment-based 但不能处理 stereo 信息。
  - 证据：[doi:10.3390/molecules29081867, p.3]；[doi:10.3390/molecules29081867, p.13]
- **baseline：** 在 activity-oriented 生成中，评估设置 3 只允许 MCMG 作为 baseline 来做约束生成比较。
  - 证据：[doi:10.3390/molecules29081867, p.13]
- **data：** COCONUT 提供约 744,986 个 unique canonical SMILES，作为 NIMO 训练所用的天然产物主数据集。
  - 证据：[doi:10.3390/molecules29081867, p.12]
- **data：** TeroKIT 含约 173,914 个 annotated terpenoids；抗疟数据集是 MMV-St. Jude 的 2507 个 positive compounds；抗菌数据来自 ChEMBL，规模为 255,788。
  - 证据：[doi:10.3390/molecules29081867, p.12]
- **data：** 在评估设置 3 中，MAIP 以 44.36 为阈值将 10% 的 NP 标为抗疟 active，并与 2507 个实验活性化合物联合训练。
  - 证据：[doi:10.3390/molecules29081867, p.13]
- **declared_resources：** 作者在 Data Availability Statement 中给出 NIMO 代码仓库：https://github.com/shenxj9/NIMO。
  - 证据：[doi:10.3390/molecules29081867, p.14]
- **declared_resources：** 研究依赖的公开资源与工具包括 COCONUT、TeroKIT、ChEMBL、MAIP、NPClassifier、MOE 和 RDKit。
  - 证据：[doi:10.3390/molecules29081867, p.8]；[doi:10.3390/molecules29081867, p.12]；[doi:10.3390/molecules29081867, p.13]；[doi:10.3390/molecules29081867, p.14]
- **limitations：** 作者明确指出，当前工作只能模拟 fragment rearrangement、ring separation 和 ring combination，尚未实现 opening/closing ring 与 bridged ring 等更复杂的 pseudo-NP 设计。
  - 证据：[doi:10.3390/molecules29081867, p.9]
- **limitations：** 文中也承认 molecular generation 的 novelty 仍是 future endeavor，说明新颖性提升与更广泛设计能力仍有空间。
  - 证据：[doi:10.3390/molecules29081867, p.4]
- **method：** 作者先对公开 NP 数据做 desalination、charge neutralization、去 glycosylation、去重与有效性检查，再保留 stereochemistry 的 canonical SMILES 作为训练输入。
  - 证据：[doi:10.3390/molecules29081867, p.9]；[doi:10.3390/molecules29081867, p.12]
- **method：** NIMO-M 通过断开环内/环间单键与满足 BRICS 规则的键提取 fragments；NIMO-S 则围绕 Murcko scaffold、side chain 与 fused ring edge 切分结构，并用 dummy atoms 记录连接位点。
  - 证据：[doi:10.3390/molecules29081867, p.9]；[doi:10.3390/molecules29081867, p.12]
- **method：** 每个输入句子由 constraint、motif info 和 motif sequence 组成，conditional transformer 结合 positional encoding、masked multi-head self-attention、FFN 和 beam search 逐步采样，再经 reconstruction 还原分子。
  - 证据：[doi:10.3390/molecules29081867, p.10]；[doi:10.3390/molecules29081867, p.11]
- **results：** 总体生成评测中，NIMO-S 的 validity 为 99.3%，NIMO-M 为 94.5%；NIMO-S 的 MOSES novelty 达 89.0%，而 NIMO-M 的 SAS 为 0.78，显示较好的可合成性。
  - 证据：[doi:10.3390/molecules29081867, p.3]；[doi:10.3390/molecules29081867, p.4]
- **results：** Terpenoid 任务中，NIMO-S' 的 terpenoid success 达 95.4%，高于 NIMO-S 91.9%、QBMG 89.7% 和 MCMG 71.2%；其 ring-system recovery 69.5% 也明显优于基线。
  - 证据：[doi:10.3390/molecules29081867, p.5]
- **results：** Antimalarial 任务里，NIMO-M 的 active rate 为 55.9%，高于训练集 10.0% 与 MCMG 52.1%；用 Motif2 重采样得到的 NIMO-M' 将 active rate 提升到 85.5%，并把 EF[50%]/EF[10%]/EF[1%] 提升到 68.22/81.33/92.21。
  - 证据：[doi:10.3390/molecules29081867, p.6]；[doi:10.3390/molecules29081867, p.7]
- **results：** Pocket-based 任务中，2HMG 上 5000 个生成分子里有 82 个候选，26 个 docking score 优于 native ligand，65 个 RMSD < 2 Å；1BO7 上分别为 294、23、104。
  - 证据：[doi:10.3390/molecules29081867, p.8]

## 页码证据

- [doi:10.3390/molecules29081867, p.1]
- [doi:10.3390/molecules29081867, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
