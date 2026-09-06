# RLEAAI: improving antibody–antigen interaction prediction using protein language model and sequence order information

- **论文 ID：** `EVIW-BEED86C0B6E8B844`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2025 Jun 4
- **DOI：** [10.1093/bib/bbaf238](https://doi.org/10.1093/bib/bbaf238)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `语言模型`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出 RLEAAI：以预训练蛋白语言模型 ESM2 为基础，结合 CKSAAP、RCCA、LCNN 和 BiLSTM，对 antibody–antigen interaction 进行更准确的序列级二分类预测，并在多个基准上优于对照方法。

## 创新边界

`创新主要在序列级特征组合与网络集成，不在候选抗体/抗原生成或优化；它复用 ESM2、CKSAAP、RCCA、LCNN 等现有组件做针对 AAI 预测的改进。`。这不是全球首创性检索或独立复现结论。

## 研究问题

如何仅用序列信息提升 antibody–antigen interaction (AAI) 预测的准确率，并增强对 CDR 区域变化的敏感性。

## 方法

- 从预训练蛋白模型提取嵌入，再以CKSAAP编码序列次序；多分支网络融合局部、双向上下文和交互注意力后分类。

## 数据与基准

- 在两个独立测试集和HIV抗体-抗原数据上评估，并重新训练DeepAAI和S3AI进行比较。

## 比较基线

- DeepAAI、S3AI、AbAgIntPre及网络/CKSAAP参数消融。

## 结果证据

- 论文报告两个独立集平均准确率0.7787、MCC 0.5552，相对DeepAAI分别提高5.2%和15.8%；均为计算分类。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 类别不平衡使MCC波动，抗原和抗体序列相似性划分可能影响泛化；预测不等同于实验结合。

## 仍未知

- 未独立验证 GitHub 仓库中的代码与论文是否完全一致，也未执行实际复现。
- Supplementary 文件未在冻结正文中完整展开，部分显著性检验与超参数细节只能依赖正文转述。
- global novelty 未做外部 prior-art 核验，不能确认是否存在更早的相似 AAI 预测设计。

## Pi 结构化证据摘录

- **baseline：** 论文把 one-hot 与 ProtT5_XL 作为特征嵌入对照，结果显示 ESM2 在 HIV 与 SARS-CoV-2 上整体更优。
  - 证据：[doi:10.1093/bib/bbaf238, p.5]
- **baseline：** HIV 和 SARS-CoV-2 主比较基线包括 DeepAAI、S3AI 和 AbAgIntPre；作者对 DeepAAI 与 S3AI 重新训练，而 AbAgIntPre 通过在线服务器评测。
  - 证据：[doi:10.1093/bib/bbaf238, p.7]
- **baseline：** SAbDab 对比基线包括 AbAgIPA、AbAgIntPre、S3AI 和 DeepAAI。
  - 证据：[doi:10.1093/bib/bbaf238, p.8]
- **data：** HIV 数据集来自 DeepAAI/CATNAP/Los Alamos，训练集 HIVtr 有 24,843 对样本，测试集 HIVtst 有 4,551 对样本，并进一步构建了 HIVtst90 与 HIVtst85 两个去冗余测试集。
  - 证据：[doi:10.1093/bib/bbaf238, p.2]
- **data：** SARS-CoV-2 数据集由本研究从 CovAbDab 与 NCBI 收集，训练集 CoVtr 有 6,150 对样本，测试集 CoVtst 有 754 对样本，病毒序列覆盖 Alpha、Beta、Delta、Gamma 和 Omicron。
  - 证据：[doi:10.1093/bib/bbaf238, p.2]
- **data：** SAbDab 五折交叉验证数据集由 AbAgIPA 构建，去冗余后包含 3,800 个正样本和 3,800 个负样本。
  - 证据：[doi:10.1093/bib/bbaf238, p.2]
- **declared_resources：** 实现使用 PyTorch 2.0.1、Adam、binary cross-entropy，训练 80 个 epoch、batch size 128、learning rate 0.0005，在 Nvidia A100 40GB 上约训练 20 小时。
  - 证据：[doi:10.1093/bib/bbaf238, p.5]
- **declared_resources：** 作者声明代码与数据可在 GitHub `https://github.com/zhouyu9931/RLEAAI.git` 获取。
  - 证据：[doi:10.1093/bib/bbaf238, p.1]；[doi:10.1093/bib/bbaf238, p.11]
- **limitations：** 作者明确将方法限定为 sequence-only，因此没有直接利用已解析的结构信息，未来才计划在结构数据充分时加入结构特征。
  - 证据：[doi:10.1093/bib/bbaf238, p.10]
- **limitations：** 联合训练 HIV 与 SARS-CoV-2 后性能略降，说明不同病毒类型的判别信息可能彼此干扰，跨病毒泛化仍是问题。
  - 证据：[doi:10.1093/bib/bbaf238, p.7]
- **method：** 模型先用预训练蛋白语言模型 ESM2 将抗体与抗原序列编码为逐位 embedding，再送入后续特征提取模块。
  - 证据：[doi:10.1093/bib/bbaf238, p.1]；[doi:10.1093/bib/bbaf238, p.3]
- **method：** 一条分支把 CKSAAP 产生的序列顺序信息与 RCCA 结合，通过沿行/列方向聚合上下文来扩大感受野。
  - 证据：[doi:10.1093/bib/bbaf238, p.4]
- **method：** 另一条分支采用 LCNN 结构（CNN、max-pooling、BiLSTM 与残差机制）提取局部模式和长程依赖，最后用 MLP 输出二分类结果。
  - 证据：[doi:10.1093/bib/bbaf238, p.3]；[doi:10.1093/bib/bbaf238, p.4]
- **results：** 摘要声称在两个独立测试集上，RLEAAI 的平均 ACC 为 0.7787、平均 MCC 为 0.5552，较 DeepAAI 分别提升 5.2% 和 15.8%。
  - 证据：[doi:10.1093/bib/bbaf238, p.1]
- **results：** 在 HIVtst 上，RLEAAI 的 ACC/F1/MCC/AUC/AUPR 分别为 82.94/80.26/65.36/91.01/88.94，优于 DeepAAI、S3AI 和 AbAgIntPre。
  - 证据：[doi:10.1093/bib/bbaf238, p.7]
- **results：** 在 SARS-CoV-2 上，RLEAAI 的 ACC/F1/MCC/AUC/AUPR 为 0.7280/0.7573/0.4568/0.7813/0.7722，较 DeepAAI 分别高 9.0%、12.9%、35.0%、7.9% 和 7.2%。
  - 证据：[doi:10.1093/bib/bbaf238, p.7]
- **results：** 在 SAbDab 上，RLEAAI 的 Precision/Recall/Specificity/F1/AUC/AUPR 为 0.887/0.911/0.884/0.899/0.948/0.939，整体优于 AbAgIPA、AbAgIntPre、S3AI 和 DeepAAI。
  - 证据：[doi:10.1093/bib/bbaf238, p.8]
- **results：** CDR masking 实验表明，RLEAAI 对 CDR 区域的 MCC bias 明显高于 DeepAAI，Mask-CDRs 时高出 216.4%，说明模型更敏感于 CDR 变化。
  - 证据：[doi:10.1093/bib/bbaf238, p.10]
- **results：** 消融结果显示，LCNN 与 RCCA 组合后的完整模型在 HIV 和 SARS-CoV-2 上都优于单独的 LCNN 或 RCCA。
  - 证据：[doi:10.1093/bib/bbaf238, p.6]

## 页码证据

- [doi:10.1093/bib/bbaf238, p.10]
- [doi:10.1093/bib/bbaf238, p.1]
- [doi:10.1093/bib/bbaf238, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
