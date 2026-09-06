# Protein language model embeddings improve HIV drug resistance prediction: a comprehensive benchmark with attention-based interpretability

- **论文 ID：** `EVIW-2298CD3BA71BF0DF`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2026 May 9
- **DOI：** [10.1093/bioinformatics/btag260](https://doi.org/10.1093/bioinformatics/btag260)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `论文声明资源` / `语言模型` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 attention-weighted ESM-2 池化，并在 Stanford HIVDB 上对 18 种抗逆转录病毒药物做系统 benchmark，与传统编码和其他 PLM backbone 比较。

## 创新边界

`新增的是表征/分类方法，不是候选分子设计。`。这不是全球首创性检索或独立复现结论。

## 研究问题

利用蛋白语言模型嵌入改进 HIV 药物耐药性预测，并评估其可解释性与泛化能力。

## 方法

- ESM-2 650M残基嵌入经可学习注意池化后分类；五折分层验证、20%外部留出、时间留出与亚型分层，并比较ESM-C/ESM-1v。

## 数据与基准

- Stanford HIVDB 6,308条带PhenoSense定量敏感性的序列，18种药物、PI/NRTI/NNRTI三类。

## 比较基线

- 二进制突变XGBoost、mean/max pooling、LR/MLP/RF及ESM-C、ESM-1v。

## 结果证据

- attention ESM-2平均AUC 0.968 vs XGBoost 0.955（P=0.0017），15/18药物改善；已知耐药位点注意富集2.48倍；20%留出AUC 0.934。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 单一公开HIVDB、类别不平衡和历史提交偏差；缺少整合酶抑制剂及前瞻临床结局验证；attention不等于因果解释。

## 仍未知

- 近似 subtype 结果与官方亚型标签的一致性未给出
- 时间 holdout 是否真正反映采样日期未知
- novel high-attention 位点尚未做湿实验验证
- 不同药物上的校准质量细节仅部分展开

## Pi 结构化证据摘录

- **baseline：** 主 baseline 是 binary mutation encoding + XGBoost，mean AUC 0.955；作者还补充比较了 random forest、SVM 与 AAC encoding。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.3]；[doi:10.1093/bioinformatics/btag260, p.5]
- **baseline：** 在 frozen ESM-2 上，mean pooling 为 0.961、max pooling 更低，说明 learned attention pooling 比简单聚合更优。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.5]
- **baseline：** 多 PLM 对照统一采用 mean-pooled embeddings + logistic regression，显示不同 backbone 间的性能差异很小。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.4]；[doi:10.1093/bioinformatics/btag260, p.9]
- **data：** 最终数据集包含 6308 条 unique sequences，覆盖 18 种药物：PI 2171、NRTI 1867、NNRTI 2270。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.3]
- **data：** Resistance 标签来自 PhenoSense assay 的 fold-change，相对于 wild-type reference，超过阈值即判为 resistant。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.3]
- **data：** 已知 DRM 来自 IAS-USA 2022 指南；序列预处理仅保留 20 个 canonical residues，并排除缺失超过 10% 的样本。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.3]；[doi:10.1093/bioinformatics/btag260, p.5]
- **data：** 亚型分析使用基于 Hamming distance 的近似分类，而时间验证则按 HIVDB sequence identifier 顺序做 80/20 划分。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.5]
- **declared_resources：** 代码开源在 GitHub `https://github.com/hayden-farquhar/HIV-ESM-2`，并声明采用 MIT license。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.1]；[doi:10.1093/bioinformatics/btag260, p.14]
- **declared_resources：** 作者还给出 Zenodo archive DOI 10.5281/zenodo.19466629，以及 Figshare DOI 10.6084/m9.figshare.31958688 作为存档与输出。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.1]；[doi:10.1093/bioinformatics/btag260, p.14]
- **declared_resources：** 数据来源是 Stanford HIV Drug Resistance Database，IAS-USA 2022 指南用于生物学解释与验证。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.1]；[doi:10.1093/bioinformatics/btag260, p.3]；[doi:10.1093/bioinformatics/btag260, p.14]
- **limitations：** 作者承认 HIVDB 是唯一可公开下载且带配对 phenotype 的资源，因此独立外部 benchmark 受限。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.5]；[doi:10.1093/bioinformatics/btag260, p.13]
- **limitations：** 亚型与时间验证都带有近似性：subtype 来自 Hamming distance 估计，时间分割依赖 sequence identifier 顺序而非真实日期。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.5]
- **limitations：** 3TC、TDF、RPV 上 ESM-2 仅持平或略差于 baseline，说明 PLM 并非对所有药物都稳定增益。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.13]
- **limitations：** 作者识别出的 novel high-attention positions 仍需结构与实验验证，当前只能视为候选位点。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.7]；[doi:10.1093/bioinformatics/btag260, p.13]
- **limitations：** fine-tuning 只解冻最后两层，未系统探索更复杂的适配策略，结果仍可能受限。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.13]
- **method：** 作者从 Stanford HIVDB 获取 HIV-1 protease 与 RT 的配对 genotype–phenotype 数据，并用临床阈值把 fold-change 转成 resistant/susceptible 二分类标签。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.3]；[doi:10.1093/bioinformatics/btag260, p.5]
- **method：** 序列先对齐到 HXB2，去除缺失过多样本，并把 stop codon 与歧义氨基酸替换为训练集共识残基后再送入模型。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.3]；[doi:10.1093/bioinformatics/btag260, p.5]
- **method：** 使用 ESM-2 650M 生成逐残基 embedding，再比较 mean pooling、max pooling、attention-weighted pooling 与 DRM-focused pooling。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.4]
- **method：** 分类器层面比较了 logistic regression、MLP、XGBoost 和 random forest；树模型还先经 PCA 保留 95% 方差。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.4]
- **method：** 评估采用五折分层交叉验证、20% holdout 外部验证、DeLong 与配对 t 检验，并补充校准、DRM 富集、亚型与时间 holdout 分析。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.4]；[doi:10.1093/bioinformatics/btag260, p.5]
- **method：** 作者还横向比较了 ESM-2、ESM C 600M 与 ESM-1v，并统一用 mean-pooled embedding 加 logistic regression 做对照。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.4]；[doi:10.1093/bioinformatics/btag260, p.7]；[doi:10.1093/bioinformatics/btag260, p.9]
- **results：** attention-weighted ESM-2 的总体 mean AUC 为 0.968，高于 binary mutation XGBoost baseline 的 0.955，配对 t 检验 P=.0017。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.1]；[doi:10.1093/bioinformatics/btag260, p.5]
- **results：** 该方法在 18 个药物中的 15 个上优于 baseline，提升最明显的是 DDI、AZT 与 FPV。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.5]
- **results：** 冻结 embedding 上，logistic regression 表现最好（mean AUC 0.935），说明 ESM-2 表征已较线性可分。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.5]
- **results：** fine-tuning 解冻最后两层仅带来小幅提升（0.979 versus 0.973 frozen），作者据此认为预训练表征已覆盖大部分信号。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.6]
- **results：** attention 权重在已知 DRM 位点上平均富集 2.48 倍，且 54 个 drug/metric 组合中有 34 个达到 P<.05。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.6]
- **results：** 外部 20% holdout 的 mean AUC 为 0.934，校准后 ECE 从 0.071 降至 0.040。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.7]
- **results：** ESM C 600M 与 ESM-1v 的 mean AUC 分别为 0.944 和 0.946，与 ESM-2 的 0.942 差异未达显著。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.7]；[doi:10.1093/bioinformatics/btag260, p.9]
- **results：** subtype B、B-divergent、non-B 的 mean AUC 分别为 0.924、0.900、0.884，时间 holdout mean AUC 为 0.930。
  - 证据：[doi:10.1093/bioinformatics/btag260, p.8]

## 页码证据

- [doi:10.1093/bioinformatics/btag260, p.13]
- [doi:10.1093/bioinformatics/btag260, p.14]
- [doi:10.1093/bioinformatics/btag260, p.1]
- [doi:10.1093/bioinformatics/btag260, p.3]
- [doi:10.1093/bioinformatics/btag260, p.5]
- [doi:10.1093/bioinformatics/btag260, p.7]
- [doi:10.1093/bioinformatics/btag260, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
