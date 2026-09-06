# PractiCPP: a deep learning approach tailored for extremely imbalanced datasets in cell-penetrating peptide prediction

- **论文 ID：** `EVIW-BCFBFEF388C36C02`
- **期刊 / 来源：** Bioinformatics
- **发表时间：** 2024 Feb 1
- **DOI：** [10.1093/bioinformatics/btae058](https://doi.org/10.1093/bioinformatics/btae058)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 PractiCPP，一个面向极端不平衡 CPP 预测的深度学习框架，结合 hard negative sampling、Transformer 序列特征、Morgan fingerprint 局部特征和 ESM-2 预训练特征，在平衡与不平衡数据上都取得较强性能。

## 创新边界

`主要创新在不平衡训练策略与多路特征融合，不是新 CPP 分子设计、生成或湿实验筛选。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在极端类别不平衡的 cell-penetrating peptide (CPP) 预测中，已知正样本极少而大量肽序列仅处于未标注状态，如何在接近真实应用的 1:1000 场景下稳定识别 CPP。

## 方法

- 蛋白/肽表示与不平衡感知训练目标结合，并用极端负样本比例验证。

## 数据与基准

- CPP正例与大规模非CPP序列，构造1:1000测试场景。

## 比较基线

- 现有CPP预测器、平衡训练和不同不平衡策略。

## 结果证据

- 论文报告在极端不平衡集仍超过SOTA，并指出平衡集训练的embedding不适合实际筛选；为计算分类。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 负样本未必真实非CPP，类别先验和实验条件变化会影响precision；无新肽摄取实验。

## 仍未知

- Supplementary Notes 和补充图未读
- 独立测试集的完整抽样细节与随机种子未见
- 未标注负样本中可能混有真实 CPP

## Pi 结构化证据摘录

- **baseline：** Balanced 场景基线包括 CellPPD-1/2/3、SkipCPP-Pred、CPPred-RF、TargetCPP 和 StackCPPred。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.4]
- **baseline：** Imbalanced 场景基线包括 SiameseCPP、BChemRF-CPPred、ML-CPP2，以及无 hard sampling 的 PractiCPPbase。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.5]
- **baseline：** 作者明确指出，这些公开方法大多围绕 balanced datasets 设计，对极端不平衡场景缺乏专门处理。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.2]；[doi:10.1093/bioinformatics/btae058, p.5]
- **data：** CPP924 是来自 CPPsite 2.0 的平衡数据集，包含 462 个 CPP 和 462 个 non-CPP。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.2]
- **data：** 极端不平衡集的正样本来自 CPP924 与 CPPsite3/StackCPPred 相关来源，经 CD-HIT 80% 去冗余、去除非天然氨基酸和冲突标签后得到 649 个 positive。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.2]
- **data：** 负样本候选来自 UniProt 与 PeptideAtlas 的 17,059,888 条序列，长度阈值设为 50，去重后剩 16,689,857 条，再随机抽 649,000 条构建 1:1000 训练集，并另设独立 1:1000 测试集。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.2]
- **declared_resources：** 作者声明 PractiCPP 源码与 CPP924 平衡数据可通过 Figshare 获取，链接为 https://doi.org/10.6084/m9.figshare.25053878.v1。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.1]；[doi:10.1093/bioinformatics/btae058, p.8]
- **declared_resources：** 作者同时说明 1:1000 不平衡数据不会直接公开下载，而是可在合理请求下向通讯作者索取。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.8]
- **declared_resources：** Funding 声明包括 NSFC 12371290 以及 KAUST ORA 的多项资助。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.8]
- **limitations：** 作者把大量未标注肽近似当作 negative 使用，因此 1:1000 设定带有明显的标签不确定性，不等同于真阴性二分类。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.2]
- **limitations：** 关于新发现的 Q/N motif，作者也写明其生物学角色仍需进一步验证，说明该部分结论仍属于计算推断。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.7]
- **method：** PractiCPP 采用 hard negative sampling 与 PractiCPPbase 交替迭代：先从负集抽样，再用当前模型挑出最难负样本参与更新。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.3]
- **method：** 序列分支把氨基酸序列编码为数值向量并加入 positional embedding，经 Transformer encoder 与 pooling 得到 sequential features。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.3]
- **method：** 局部分支将 peptide 当作 molecule 计算 Morgan fingerprint，并用 1D conv、max-pooling 和 FC 提取 local features。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.3]；[doi:10.1093/bioinformatics/btae058, p.4]
- **method：** 预训练分支使用 ESM-2 生成上下文表示，均值池化后经 FC 投影为 pretrained features，三路特征拼接后送入 MLP，并用 cross-entropy 训练。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.4]
- **method：** 作者在不平衡实验中搜索 K ∈ {3,9,15,21,30}，并将负采样比例 M 固定为 3，最终报告 K=9 表现最佳。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.3]
- **results：** 在 CPP924 的 10-fold cross-validation 上，PractiCPP 的 Acc 95.65%、Sn 94.29%、Sp 97.06%、MCC 91.34%，优于 7 个基线。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.4]
- **results：** 在 1:1000 独立测试集上，PractiCPP 的 AUPR 为 0.6400；在 recall=0.6 时 precision 0.8056、F1 0.6864、FP/C 0.2414。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.5]
- **results：** 在 recall=0.7 时，PractiCPP 的 precision 0.2048、F1 0.317、FP/C 3.8824，仍优于对照方法。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.5]
- **results：** Ablation 表明去掉 ESM 或 Morgan fingerprint 都会降性能，其中 w/o ESM-FP 的 AUPR 最低为 0.483；hard negative sampling 相比 PractiCPPbase 还带来 7.08% 的 AUPR 提升。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.6]
- **results：** t-SNE 显示用 1:1000 数据训练的模型能分开 CPP、non-CPP 和 unlabeled peptides，而 balanced 训练对 unlabeled peptides 区分较差；MEME motif 还观察到 R/K 之外的 Q/N/F 信号。
  - 证据：[doi:10.1093/bioinformatics/btae058, p.6]；[doi:10.1093/bioinformatics/btae058, p.7]

## 页码证据

- [doi:10.1093/bioinformatics/btae058, p.1]
- [doi:10.1093/bioinformatics/btae058, p.2]
- [doi:10.1093/bioinformatics/btae058, p.8]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
