# DeepDTAGen: a multitask deep learning framework for drug-target affinity prediction and target-aware drugs generation

- **论文 ID：** `EVIW-6A06FBBBEE19026B`
- **期刊 / 来源：** Nature Communications（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1038/s41467-025-59917-6](https://doi.org/10.1038/s41467-025-59917-6)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 DeepDTAGen：用共享 latent space 同时做 DTA 预测与 target-aware drug 生成，并用 FetterGrad 缓解两任务间的 gradient conflicts。

## 创新边界

`仅按论文自述，创新边界集中在共享表征、多任务双目标与 FetterGrad；冻结证据未独立证明其全球首创。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何在同一模型中联合完成 drug-target affinity prediction 与 target-aware drug generation，并在共享表征下缓解多任务训练的梯度冲突。

## 方法

- 序列/图encoder、affinity回归和SMILES/图生成联合训练。

## 数据与基准

- Davis/KIBA等DTA与分子生成benchmark。

## 比较基线

- DeepDTA/GraphDTA与target-conditioned generative models。

## 结果证据

- 论文报告affinity和生成指标提升；无合成/活性实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 共享任务可能负迁移，生成被affinity predictor偏差引导。

## 仍未知

- 未见湿实验或体内验证，无法判断生成分子的真实生物学可转化性。
- FetterGrad 的外部复现与稳定性未在冻结证据中独立验证。
- 生成任务尚未把 QED、LogP、SAS 与 stereochemistry 作为条件约束。

## Pi 结构化证据摘录

- **baseline：** 亲和力基线覆盖 KronRLS、SimBoost、DeepDTA、WideDTA、GraphDTA、AttentionDTA、DeepCDA、CoVAE、ELECTRA-DTA、DoubleSG-DTA、SSM-DTA 和 GDilatedDTA；BindingDB 部分结果标注 RT 表示作者环境重训。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.4]
- **baseline：** 生成基线包括 CoVAE、ORGAN、SMILES LSTM、Syntalinker 和 PGMG；DeepDTAGen 在有效性和新颖性上普遍领先，但 uniqueness 低于 PGMG。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.6]
- **data：** 评估数据集为 KIBA、Davis 和 BindingDB；drug SMILES 来自 PubChem，protein sequences 来自 UniProt，作者沿用 GraphDTA 的 6-fold 切分方案，1 个 fold 作为 test。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.11]
- **data：** Davis 包含 68 drugs/442 targets，KIBA 包含 2111 drugs/229 targets/118254 interactions，BindingDB 包含 18044 unique drugs/1620 proteins/56525 interactions。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.11]
- **data：** 数据可追溯到公共资源：论文在 Figshare 提供预处理数据、generated drugs 和 pre-trained models，且原始靶标 EGFR 可从 UniProt 获取。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.14]
- **declared_resources：** 论文给出 DeepDTAGen 的 GitHub、Zenodo 记录，以及包含预处理数据和 generated drugs 的 Figshare 链接；pre-trained models 也托管在 Figshare。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.14]
- **declared_resources：** 作者还声明使用了 AlphaFold3、AutoDock VINA、PyMol、PyTorch 1.12.1、RDKit 2022.09.1、ChemDraw 21.0.0、Numpy 1.23.5 和 Matplotlib 3.5.1。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.14]
- **limitations：** 作者明确写到模型尚未把 QED、LogP、SAS 作为条件输入，也忽略了 stereochemistry dynamics。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.11]
- **limitations：** KIBA/BindingDB 上较低的 uniqueness 被作者归因于 polypharmacological 训练数据和同一 drug 出现在多条 interaction 中。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.6]
- **limitations：** 冻结页中的证据主要是公开 benchmark、randomization、cold-start 与 docking 的 in silico 评估，未见湿实验验证。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.4]；[doi:10.1038/s41467-025-59917-6, p.5]；[doi:10.1038/s41467-025-59917-6, p.8]；[doi:10.1038/s41467-025-59917-6, p.10]
- **method：** 模型由 Gated-CNN、Graph-Encoder、Fully-Connected 和 Transformer-Decoder 四个模块组成，分别用于蛋白编码、药物图编码、亲和力回归与 SMILES 生成。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.11]；[doi:10.1038/s41467-025-59917-6, p.12]
- **method：** 药物侧把 SMILES 转为带丰富 atom features 的 graph，并通过 PMVO/AMVO 两套 latent 表征同时服务于回归与生成；生成侧用 MTS 作为条件输入做 cross-attention 和 autoregressive decoding。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.11]；[doi:10.1038/s41467-025-59917-6, p.12]
- **method：** 训练目标包含 MSE、KL divergence 和 language-model loss；FetterGrad 用 ESS 阈值 0.5 判断梯度冲突，并结合 MSS 进行梯度去冲突后再送入 Adam。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.13]
- **results：** 在 Table 1 中，DeepDTAGen 在 KIBA/Davis/BindingDB 的 CI/MSE/r2m/AUPR 分别达到 0.897/0.146/0.765/0.843、0.890/0.214/0.705/0.772 和 0.876/0.458/0.760/0.870。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.4]
- **results：** 随机化测试（y、drug、protein、protein descriptor）使性能接近随机水平，作者据此主张模型没有依赖偶然相关。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.4]；[doi:10.1038/s41467-025-59917-6, p.5]
- **results：** cold-start 的 drug-wise 和 protein-wise split 显示模型对 unseen drugs/proteins 具有较强鲁棒性，在 Davis 与 BindingDB 上多项指标优于或接近最佳。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.5]
- **results：** 生成任务中，Validity 几乎达到 99.9%，BindingDB 上 Novelty 可达 99.0%-99.9%，但 KIBA/BindingDB 的 Uniqueness 仅 8%-22%；作者还用 docking、QED/LogP/SAS 和 Tanimoto similarity 说明生成分子具有 target-aware 性质。
  - 证据：[doi:10.1038/s41467-025-59917-6, p.6]；[doi:10.1038/s41467-025-59917-6, p.8]；[doi:10.1038/s41467-025-59917-6, p.10]

## 页码证据

- [doi:10.1038/s41467-025-59917-6, p.1]
- [doi:10.1038/s41467-025-59917-6, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
