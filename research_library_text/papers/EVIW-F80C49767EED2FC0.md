# Structure-aware deep learning model for peptide toxicity prediction

- **论文 ID：** `EVIW-F80C49767EED2FC0`
- **期刊 / 来源：** Protein Sci
- **发表时间：** 2024 Jun 22
- **DOI：** [10.1002/pro.5076](https://doi.org/10.1002/pro.5076)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `肽与抗菌肽`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 tAMPer，一个把 ESM2 序列 embedding、ColabFold 预测结构图、Bi-GRU、GVP/GNN 和 self-attention 结合的多模态模型，并声称首次同时利用序列与结构做 in silico peptide toxicity prediction，同时给出新整理的溶血标注数据集。

## 创新边界

`本次审核仅确认论文自述的结构感知毒性预测方案与实验结果；是否“首次”以及全球新颖性未由冻结证据独立验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在 AMP/peptide 筛选中，如何在湿实验前利用序列与预测 3D 结构准确预测毒性/溶血性，从而减少昂贵且耗时的毒性筛查。

## 方法

- 节点为氨基酸、边为空间邻接的结构图由GNN编码，序列由RNN编码，两路表示经attention/融合后分类。

## 数据与基准

- 评估含公开蛋白毒性基准和作者整理的AMP溶血数据；数据、代码和模型随仓库发布。

## 比较基线

- 既有序列、PSSM和结构感知毒性预测器，以及单模态消融。

## 结果证据

- 作者报告AMP溶血数据F1=68.7%，比次优方法高23.4个百分点；蛋白基准F1较当时SOTA提高超过3个百分点。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- ColabFold静态结构不能覆盖肽在不同环境中的多构象，结构预测误差会传递；毒性标签知识与数据仍不完备。

## 仍未知

- 未独立复现作者代码或模型，论文中的性能提升仅能视为自报结果。
- ATSE 基线未能获得预测输出，完整横向比较并不完整。
- 论文未量化结构预测误差对毒性分类性能的敏感性。
- 公开仓库是否与文中实现完全一致，本次未核验。

## Pi 结构化证据摘录

- **baseline：** 在 in-house set 上比较的基线包括 HAPPENN、HemoPI、ToxinPred、ToxDL、Toxify（原版与重训）和 ToxIBTL；ATSE 在线服务不可用，因此未获得该方法结果。
  - 证据：[doi:10.1002/pro.5076, p.4]；[doi:10.1002/pro.5076, p.9]
- **baseline：** 在 protein benchmark 上比较的基线包括 BLAST、BLAST-score、InterProScan、HmmSearch、ClanTox、ToxinPred、ToxDL、ToxIBTL 与重训 Toxify。
  - 证据：[doi:10.1002/pro.5076, p.5]；[doi:10.1002/pro.5076, p.9]
- **baseline：** 作者为公平比较，在 protein benchmark 上不额外做结构增强，只选取平均 pLDDT 最高的单个结构进行评测。
  - 证据：[doi:10.1002/pro.5076, p.5]
- **data：** 训练/验证集来自 DBAASP v3、Hemolytik、APD3 与 Swiss-Prot，过滤为 5–50 aa、自然氨基酸、去冗余后得到 1929 条 hemolytic 与 4047 条 nonhemolytic peptide，并用 CD-HIT 做 <80% 相似度切分。
  - 证据：[doi:10.1002/pro.5076, p.8]
- **data：** 作者还构建了独立的 in-house peptide hemolysis 测试集，共 340 条序列；其中 56 条为 hemolytic、284 条为 nonhemolytic，标签来自猪 RBC 溶血实验的 HC50。
  - 证据：[doi:10.1002/pro.5076, p.8]；[doi:10.1002/pro.5076, p.9]
- **data：** 结构输入使用 local ColabFold v1.3.1 生成 5 个不同随机种子的预测结构，并在训练时把这 5 个结构都作为独立样本。
  - 证据：[doi:10.1002/pro.5076, p.10]
- **data：** 蛋白 toxicity benchmark 采用 toxDL 数据集，训练集包含 4472 个 toxic 与 6341 个 nontoxic 序列，测试集与训练集序列一致性低于 40% 且不共享 Pfam clan。
  - 证据：[doi:10.1002/pro.5076, p.5]
- **declared_resources：** 作者声明 datasets、code 和 models 可在 GitHub 仓库 https://github.com/bcgsc/tAMPer 获取。
  - 证据：[doi:10.1002/pro.5076, p.13]
- **declared_resources：** 实现基于 PyTorch 1.13.1 与 PyTorch Geometric 2.3.0，并使用 Adam、early stopping 和固定的训练超参数设置。
  - 证据：[doi:10.1002/pro.5076, p.12]
- **declared_resources：** 结构预测使用 local ColabFold 1.3.1，序列 embedding 使用 ESM2 t12/t33；数据来源还包括 DBAASP v3、Hemolytik、APD3、UniProtKB/Swiss-Prot 和 AlphaFold Protein Structure Database。
  - 证据：[doi:10.1002/pro.5076, p.8]；[doi:10.1002/pro.5076, p.10]；[doi:10.1002/pro.5076, p.12]
- **limitations：** 作者明确指出 static 3D structure 不能完全捕捉 peptide 在不同细胞环境中的动态构象。
  - 证据：[doi:10.1002/pro.5076, p.7]
- **limitations：** 论文也承认 ColabFold/AF2 对短蛋白和 peptide 的覆盖有限，结构预测本身带有方法假设与误差。
  - 证据：[doi:10.1002/pro.5076, p.7]
- **limitations：** 作者强调 in silico toxicity 不能替代 in vitro 验证，因此筛出的 AMP 候选仍需要后续实验确认。
  - 证据：[doi:10.1002/pro.5076, p.7]
- **limitations：** 训练数据规模有限且类别不平衡，原因是毒性实验昂贵、标注稀缺以及 peptide 毒性机制尚未完全厘清。
  - 证据：[doi:10.1002/pro.5076, p.7]
- **method：** 模型先用 ESM2 为每个残基生成初始 embedding，再通过 Bi-GRU 提取序列方向上的上下文特征。
  - 证据：[doi:10.1002/pro.5076, p.10]；[doi:10.1002/pro.5076, p.11]
- **method：** 蛋白/肽的 3D 结构由 local ColabFold 预测，并按 Cα 距离阈值构图后交给 GVP/GNN 编码节点与边特征。
  - 证据：[doi:10.1002/pro.5076, p.10]；[doi:10.1002/pro.5076, p.11]
- **method：** 序列特征与结构特征在拼接后进入 8-head self-attention，再附加 amidation 二值特征，最后经全连接层输出毒性概率。
  - 证据：[doi:10.1002/pro.5076, p.12]
- **method：** 训练目标是毒性分类损失与 secondary-structure 辅助损失的线性组合，并且 GNN 部分还先做了 reverse folding 预训练。
  - 证据：[doi:10.1002/pro.5076, p.11]；[doi:10.1002/pro.5076, p.12]
- **results：** 在 in-house hemolysis set 上，tAMPer 达到 F1 68.7%、MCC 62.7%、auROC 91.7%、auPRC 69.0%，论文报告其优于第二名方法。
  - 证据：[doi:10.1002/pro.5076, p.4]；[doi:10.1002/pro.5076, p.9]
- **results：** 在 toxDL protein benchmark 上，tAMPer 达到 F1 86.0%、MCC 85.0%、auROC 99.2%、auPRC 91.6%，略优于 ToxIBTL、ToxDL 等对照。
  - 证据：[doi:10.1002/pro.5076, p.5]；[doi:10.1002/pro.5076, p.9]
- **results：** 消融实验显示 sequence-only 强于 structure-only，而双模态组合进一步提升各项指标；作者还报告毒性概率与 HC50 呈反相关。
  - 证据：[doi:10.1002/pro.5076, p.4]；[doi:10.1002/pro.5076, p.5]；[doi:10.1002/pro.5076, p.9]

## 页码证据

- [doi:10.1002/pro.5076, p.13]
- [doi:10.1002/pro.5076, p.1]
- [doi:10.1002/pro.5076, p.2]
- [doi:10.1002/pro.5076, p.3]
- [doi:10.1002/pro.5076, p.6]
- [doi:10.1002/pro.5076, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
