# E(3) equivariant graph neural networks for robust and accurate protein-protein interaction site prediction

- **论文 ID：** `EVIW-B8BCB4B14D4A9325`
- **期刊 / 来源：** PLoS Comput Biol
- **发表时间：** 2023 Aug 31
- **DOI：** [10.1371/journal.pcbi.1011435](https://doi.org/10.1371/journal.pcbi.1011435)
- **范围标签：** `Pi 已解析` / `可迁移方法` / `有静态审计仓库` / `图与几何学习` / `结构预测`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者声称提出 EquiPPIS：一个基于 E(3)-equivariant graph neural network 的残基级 PPI site 预测模型；它在公开基准上优于既有方法，并且对 unbound 结构与 AlphaFold2 预测结构表现出更强鲁棒性 [doi:10.1371/journal.pcbi.1011435, p.3][doi:10.1371/journal.pcbi.1011435, p.5][doi:10.1371/journal.pcbi.1011435, p.7][doi:10.1371/journal.pcbi.1011435, p.8].

## 创新边界

`新意主要在 E(3) 等变图网络、attention 消融和多粒度结构特征设计；边界在于它仍是基于公开数据的监督式残基分类，不是直接生成或优化新的 protein candidate，也没有 wet-lab 验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在实验结构稀缺、且需要在单体蛋白上识别 PPI site 的情况下，如何仅凭序列/结构信息做出更稳健的 partner-independent 预测，并尽量适配 AlphaFold2 预测结构，是本文要解决的核心问题 [doi:10.1371/journal.pcbi.1011435, p.2][doi:10.1371/journal.pcbi.1011435, p.4][doi:10.1371/journal.pcbi.1011435, p.8].

## 方法

- 以残基3D图为输入进行等变消息传递和注意力聚合，输出界面残基概率。[doi:10.1371/journal.pcbi.1011435, p.2][doi:10.1371/journal.pcbi.1011435, p.6]

## 数据与基准

- 训练/验证/测试来自公开结构集，并比较实验结构与AlphaFold2预测结构输入。[doi:10.1371/journal.pcbi.1011435, p.1]

## 比较基线

- GraphPPIS等既有方法及去注意力/不同架构消融；去注意力ROC-AUC约降至0.8。[doi:10.1371/journal.pcbi.1011435, p.6][doi:10.1371/journal.pcbi.1011435, p.7]

## 结果证据

- 论文报告优于既有方法，且使用预测结构时仍具稳健性；这是位点预测基准，不是实验PPI测定。[doi:10.1371/journal.pcbi.1011435, p.1][doi:10.1371/journal.pcbi.1011435, p.5]

## 可用资源与代码关系

- [https://github.com/Bhattacharya-Lab/EquiPPIS](https://github.com/Bhattacharya-Lab/EquiPPIS)
  - 固定 commit：`15fdccc532517dfaadbeea12759be59ef3f3f5de`
  - 静态复用层级：C_license_or_component_gaps
  - 许可证边界：license_identified_GPL-3.0_terms_require_review

## 已知限制

- 作者指出模型可解释性仍是开放挑战，MSA信息未显式纳入且值得后续研究。[doi:10.1371/journal.pcbi.1011435, p.11]

## 仍未知

- 外部基线与超参数复现实验是否在完全一致的软件/硬件环境中重跑，冻结 PDF 未给出全部可复现细节。
- AlphaFold2 失败样本与 ColabFold 替代流程仅提到 4cdgA，其他边缘案例的处理策略不完全透明。
- 论文没有提供独立 wet-lab 验证，因此实际生物学可用性仍需后续实验确认。

## Pi 结构化证据摘录

- **baseline：** 主对照包括 sequence-based 的 PSIVER、ProNA2020、SCRIBER、DLPred、DELPHI，以及 structure-based 的 DeepPPIS、SPPIDER、MaSIF-site、GraphPPIS。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.5]；[doi:10.1371/journal.pcbi.1011435, p.15]
- **baseline：** 作者还设置了 'EquiPPIS invariant'、'EquiPPIS w/o attention'、GCN 和 GAT 作为消融/替代架构基线。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.6]；[doi:10.1371/journal.pcbi.1011435, p.14]
- **baseline：** AlphaFold2 输入下的对比主要以 GraphPPIS 为最近邻基线，并同时报告 experimental structure 与 predicted structure 的差异。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.8]
- **data：** 训练与测试使用 Dset_186、Dset_72 和 Dset_164 组合后去冗余的数据；按 GraphPPIS 的划分得到 Train_335 与 Test_60，分别包含 10,374/55,992 和 2,075/11,069 个 interacting 与 non-interacting residues。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.4]；[doi:10.1371/journal.pcbi.1011435, p.15]
- **data：** 为评估构象变化鲁棒性，作者从 Test_60 中抽取 31 个具有 unbound monomeric structures 的蛋白作为 UBtest_31。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.7]；[doi:10.1371/journal.pcbi.1011435, p.15]
- **data：** 独立验证集 Validation_42 来自 Test_315，且过滤掉与测试集序列同一性超过 25% 的蛋白链，用于 feature ablation 和 hyperparameter selection。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.4]；[doi:10.1371/journal.pcbi.1011435, p.11]；[doi:10.1371/journal.pcbi.1011435, p.15]
- **data：** AlphaFold2 预测结构按默认参数本地运行，生成 5 个模型后选取最高 pLDDT；对 4cdgA 失败案例改用 ColabFold/MMseqs2。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.15]
- **declared_resources：** Data availability 声明给出原始数据来自公开来源，并可在 GraphPPIS 相关仓库获取。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.1]
- **declared_resources：** Code availability 声明给出 EquiPPIS 的开源 GitHub 仓库，且许可为 GNU GPL v3。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.1]
- **declared_resources：** 论文显式列出关键工具与依赖，包括 PSI-BLAST、DSSP、Pytorch、DGL、AlphaFold2、ColabFold 和 MMseqs2。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.12]；[doi:10.1371/journal.pcbi.1011435, p.14]；[doi:10.1371/journal.pcbi.1011435, p.15]
- **declared_resources：** Funding 来自 NIGMS 与 NSF，且资助方未参与研究设计、数据分析或投稿决策。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.1]
- **limitations：** 作者明确指出模型可解释性仍是 open challenge，latent representation 的生物学意义还需要系统研究。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.11]
- **limitations：** 论文也承认当前 MSA-free 方案可能错过额外信息，未来可探索加入 MSA 以进一步提升准确率。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.11]
- **limitations：** 按 secondary structure 分组时，主要 beta strand 蛋白的 ROC-AUC 低于 helices，说明该类样本仍有改进空间。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.9]
- **limitations：** 即便使用 AlphaFold2 结构，性能仍比 experimental input 略低，说明预测结构误差仍会影响下游 site prediction。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.8]
- **method：** 将单体蛋白表示为 residue-level graph：节点是残基，非连续残基对若 Cα 距离不超过 14Å 且序列间隔至少为 6，则连边。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.4]；[doi:10.1371/journal.pcbi.1011435, p.12]
- **method：** 模型主体是 10 层 EGCL 的 E(3)-equivariant GNN，通过 coordinate update 和 equivariant message passing 进行残基级分类；还可加入 attention 聚合。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.13]；[doi:10.1371/journal.pcbi.1011435, p.14]；[doi:10.1371/journal.pcbi.1011435, p.11]
- **method：** 节点特征拼接了 amino acid one-hot、PSSM、ESM2，以及 secondary structure、RSA、local geometry、residue orientation、virtual surface area、contact count 和 relative positioning。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.12]；[doi:10.1371/journal.pcbi.1011435, p.13]
- **method：** 训练采用 binary cross entropy、Adam(lr=1e-4)、cosine annealing，最多 50 epochs，并在 NVIDIA A40 上实现；Pytorch 1.12.0 与 DGL 0.9.0 为主要软件依赖。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.14]
- **results：** 在 Test_60 上，EquiPPIS 达到 Accuracy 0.787、MCC 0.366、ROC-AUC 0.805、PR-AUC 0.467，整体优于 GraphPPIS 的 0.776、0.333、0.786、0.429。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.5]
- **results：** 去掉 coordinate update 的 'EquiPPIS invariant' 与去掉 attention 的 'EquiPPIS w/o attention' 都低于完整模型；GCN 和 GAT 基线更弱，说明 equivariance 与 attention 都有贡献。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.6]；[doi:10.1371/journal.pcbi.1011435, p.7]
- **results：** 在 UBtest_31 上，EquiPPIS 对 unbound structure 的性能退化最小；相较之下，MaSIF-site 和 GraphPPIS 的 MCC 与 PR-AUC 下降更明显。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.7]
- **results：** 使用 AlphaFold2 预测结构时，EquiPPIS 的 PR-AUC 仍为 0.451，且高于 GraphPPIS 使用 experimental structure 的 0.429，也高于 GraphPPIS 使用预测结构的 0.399。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.8]
- **results：** 显著性检验显示 EquiPPIS 在 experimental 与 AlphaFold2 两种输入下，对 F1、MCC、ROC-AUC、PR-AUC 都达到 p<0.05；按 secondary structure 分组时，'Primarily helix' 的 ROC-AUC 最高，为 0.855。
  - 证据：[doi:10.1371/journal.pcbi.1011435, p.8]；[doi:10.1371/journal.pcbi.1011435, p.9]

## 页码证据

- [doi:10.1371/journal.pcbi.1011435, p.6]
- [doi:10.1371/journal.pcbi.1011435, p.7]
- [doi:10.1371/journal.pcbi.1011435, p.11]
- [doi:10.1371/journal.pcbi.1011435, p.1]
- [doi:10.1371/journal.pcbi.1011435, p.2]
- [doi:10.1371/journal.pcbi.1011435, p.5]
- [doi:10.1371/journal.pcbi.1011435, p.6]
- [doi:10.1371/journal.pcbi.1011435, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
