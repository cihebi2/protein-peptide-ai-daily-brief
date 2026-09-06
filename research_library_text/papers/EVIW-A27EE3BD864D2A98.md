# Sequence-only prediction of binding affinity changes: a robust and interpretable model for antibody engineering

- **论文 ID：** `EVIW-A27EE3BD864D2A98`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2025 Aug 9
- **DOI：** [10.1093/bioinformatics/btaf446](https://doi.org/10.1093/bioinformatics/btaf446)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 ProtAttBA：一种仅基于序列的深度学习框架，结合冻结的预训练蛋白语言模型与 cross-attention 回归头，用于预测抗体-抗原复合物的结合亲和力变化，并声称在多个开放基准上具备鲁棒性与可解释性。

## 创新边界

`Novelty is in the sequence-only encoding plus cross-attention regression for ΔΔG prediction; it does not generate or optimize antibody candidates, and no wet-lab validation is shown.`。这不是全球首创性检索或独立复现结论。

## 研究问题

在结构缺失或不可靠时，基于序列预测抗体-抗原突变导致的结合亲和力变化（ΔΔG_bind），以支持抗体工程中的突变筛选。

## 方法

- BERT式蛋白序列预训练后，分别编码抗体和抗原，通过cross-attention学习相互作用并监督回归。

## 数据与基准

- 在三个公开抗体亲和力变化基准及不同结构不确定条件下评估。

## 比较基线

- 序列PLM、结构亲和力模型及cross-attention/预训练消融。

## 结果证据

- 论文报告与序列和结构基线相比具有竞争力，并在结构不确定时更稳健；属于计算回归。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 序列模型缺少显式几何机制，训练标签有限；结构模型比较也受结构质量影响。

## 仍未知

- 补充材料中的 Table 1/2 与 Figure 1/2/3 未完整展开，部分超参数和消融细节不可见。
- attention 权重的可解释性仅做案例展示，未见系统性因果验证。
- 未见独立外部测试集或湿实验验证，泛化证据主要来自公开基准拆分。

## Pi 结构化证据摘录

- **baseline：** 对比基线覆盖 RF/GB、DeepEP-PPI、LSTM-PHV、PIPR、TransPPI、AttABseq，以及 BeAtMuSiC、FoldX、DDGPred 等结构/能量方法。
  - 证据：[doi:10.1093/bioinformatics/btaf446, p.5]
- **baseline：** 作者特别区分了 PDB、AF2 与 ESM 三类结构输入，结果显示结构方法对输入结构质量高度敏感，预测结构下性能通常下降。
  - 证据：[doi:10.1093/bioinformatics/btaf446, p.5]
- **data：** 使用三套开放基准 AB645、S1131 和 AB1101；前两者为单点突变，AB1101 含 1–7 位点突变。
  - 证据：[doi:10.1093/bioinformatics/btaf446, p.2]
- **data：** 标签来自实验测得的结合自由能变化 ΔΔG_bind；S1131 源自 SKEMPI，AB645/AB1101 源自 AB-bind，且采用 Jin et al. 处理后的版本。
  - 证据：[doi:10.1093/bioinformatics/btaf446, p.2]
- **declared_resources：** 论文声明源码和数据可在 GitHub 仓库 ProtAttBA 获取。
  - 证据：[doi:10.1093/bioinformatics/btaf446, p.1]；[doi:10.1093/bioinformatics/btaf446, p.8]
- **declared_resources：** 实现与实验依赖 PyTorch 2.1.2 和单张 NVIDIA RTX-3090；基金来自 NSFC 62302291。
  - 证据：[doi:10.1093/bioinformatics/btaf446, p.4]；[doi:10.1093/bioinformatics/btaf446, p.8]
- **limitations：** 作者在结论中明确承认结构信息仍然重要，并建议未来融合 predicted/partial structure、binding site annotation 或 contrastive learning 来提升鲁棒性。
  - 证据：[doi:10.1093/bioinformatics/btaf446, p.7]
- **limitations：** 解释性分析只基于从 AB-bind 和 S1131 随机选取的两个复合物案例，尚不足以证明 attention-score 与真实机制的普适对应关系。
  - 证据：[doi:10.1093/bioinformatics/btaf446, p.6]
- **method：** 首先用冻结的预训练蛋白语言模型分别编码野生型与突变型抗体/抗原序列，文中比较了 ProtBert、ESM1b、ESM2 和 Ankh 四种嵌入器。
  - 证据：[doi:10.1093/bioinformatics/btaf446, p.3]
- **method：** 随后通过 1D convolution、双向 multi-head cross-attention 和 convolutional pooling 将 residue-level 表示压缩为蛋白级向量，以显式建模抗体-抗原交互。
  - 证据：[doi:10.1093/bioinformatics/btaf446, p.3]；[doi:10.1093/bioinformatics/btaf446, p.4]
- **method：** 最终将野生型与突变型复合体特征拼接后，经三层全连接回归 ΔΔG_bind；训练采用 AdamW、MSE、early stopping，并在单张 NVIDIA RTX-3090 上用 PyTorch 实现。
  - 证据：[doi:10.1093/bioinformatics/btaf446, p.4]
- **results：** 在表 1 的 K-fold 结果中，ProtAttBA 的各变体在 AB645 与 AB1101 上表现较强，且 ESM2 变体通常最好；但在 S1131 上，DDGPred-PDB 的 RMSE/R2/PCC/ρ 明显优于 ProtAttBA 变体。
  - 证据：[doi:10.1093/bioinformatics/btaf446, p.5]
- **results：** 在序列相似度拆分与 mutation-depth 拆分中，ProtAttBA 维持相对稳定，而多种结构方法在 AF2/ESM 输入下明显退化；AB1101-MutDepth 上 ProtAttBA-ESM2 的 RMSE 为 2.10、PCC 为 0.55、ρ 为 0.45。
  - 证据：[doi:10.1093/bioinformatics/btaf446, p.6]；[doi:10.1093/bioinformatics/btaf446, p.7]
- **results：** 注意力可视化案例显示，1IAR 的 R53Q 与 1DQJ 的 S91A 都与氢键网络改变相关，模型把较高权重放在邻近的关键残基上。
  - 证据：[doi:10.1093/bioinformatics/btaf446, p.6]

## 页码证据

- [doi:10.1093/bioinformatics/btaf446, p.1]
- [doi:10.1093/bioinformatics/btaf446, p.2]
- [doi:10.1093/bioinformatics/btaf446, p.6]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
