# CLDN18.2 antibody design with protein language models: A deep learning optimization framework

- **论文 ID：** `EVIW-BE033C46CCB9A3C9`
- **期刊 / 来源：** PLOS Computational Biology（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1371/journal.pcbi.1014499](https://doi.org/10.1371/journal.pcbi.1014499)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `语言模型` / `结构预测`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 cdrGPT：以 GPT-2 decoder 为核心，先在 OAS 的 CDRH3 上预训练，再用 rejection sampling fine-tuning 和多目标打分优化 CLDN18.2 相关 CDRH3，并通过 ESM2、LASSO、AlphaFold3 与 MD 做候选优选。

## 创新边界

`创新边界主要是 scaffold-constrained 的 CDRH3 生成/优化流水线与多指标筛选组合，不是湿实验验证，也不是全抗体通用生成的终局方法。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在固定 zolbetuximab scaffold 中，自动生成并筛选面向 CLDN18.2 的 CDRH3 序列，同时兼顾亲和力、可开发性和免疫原性。

## 方法

- 生成CDRH3后按亲和力代理、MHC-II binding risk和结构一致性迭代筛选，ESM2/PCA聚类多样性。

## 数据与基准

- OAS抗体序列、zolbetuximab模板和AlphaFold3结构预测。

## 比较基线

- zolbetuximab模板、无优化生成和不同cluster。

## 结果证据

- 7条代表序列预测结构与模板接近，CDRH3 RMSD 1.331 Å、关键paratope偏差<0.4 Å；无结合实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- isoform specificity未解决，需cross-reactivity、humanness和immunogenicity实验；AF3结构相似不证明功能。

## 仍未知

- 候选序列在真实实验中的 CLDN18.2 结合强度是否成立
- CLDN18.2 与 CLDN18.1 的选择性是否足够
- GitHub 源码仓库内容未在本次冻结证据中独立核验

## Pi 结构化证据摘录

- **baseline：** 本文以 zolbetuximab 作为主要参考基线，并把其 CDRH3 模板作为 grafting 与排序锚点。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.1]；[doi:10.1371/journal.pcbi.1014499, p.7]；[doi:10.1371/journal.pcbi.1014499, p.12]
- **baseline：** 模型层面比较了 Pre、FT1、FT2，以及随机抽样训练集 reference baseline，用于衡量 novelty、uniqueness 和 diversity。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.8]；[doi:10.1371/journal.pcbi.1014499, p.10]
- **baseline：** 共享 grafting 框架下又对照了 AbLang 和 AntiBERTy，HER2 场景则以 trastuzumab 作为迁移参照。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.10]；[doi:10.1371/journal.pcbi.1014499, p.11]
- **data：** 训练集最终得到 637,887 条非冗余且唯一的 CDRH3 序列，来源于 2024-12-12 获取的 OAS 数据并经 IMGT 统一编号。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.3]；[doi:10.1371/journal.pcbi.1014499, p.8]
- **data：** 候选生成从 50,000 条序列开始，最终筛到 313 条高置信候选；其中 7 条代表序列进入 AF3 结构验证。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.1]；[doi:10.1371/journal.pcbi.1014499, p.12]；[doi:10.1371/journal.pcbi.1014499, p.14]；[doi:10.1371/journal.pcbi.1014499, p.17]
- **data：** HER2 作为外部 generalization 场景，用 trastuzumab scaffold 验证迁移性；另以 adalimumab、bevacizumab 和 panitumumab 做跨抗体测试。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.10]；[doi:10.1371/journal.pcbi.1014499, p.11]
- **declared_resources：** 论文声明使用 OAS、IMGT、Pandas、GPT-2、AlphaBind、NetMHCIIpan 4.0、ESM2、AlphaFold3、msa、UCSF Chimera、PyMOL 与 MD 等资源。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.3]；[doi:10.1371/journal.pcbi.1014499, p.4]；[doi:10.1371/journal.pcbi.1014499, p.5]；[doi:10.1371/journal.pcbi.1014499, p.7]；[doi:10.1371/journal.pcbi.1014499, p.13]；[doi:10.1371/journal.pcbi.1014499, p.15]；[doi:10.1371/journal.pcbi.1014499, p.16]；[doi:10.1371/journal.pcbi.1014499, p.17]
- **declared_resources：** 算力资源写明为 4 张 NVIDIA A100 用于训练、1 张 A100 用于推理，20,000 条候选的生成与计算评估约耗时 4 小时。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.4]；[doi:10.1371/journal.pcbi.1014499, p.19]
- **declared_resources：** 数据可用性声明给出源码仓库 https://github.com/HomerCui/cdrGPT。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.1]
- **limitations：** 作者明确把该工作定义为 candidate prioritization workflow，而不是标准 supervised benchmark；因此 AlphaBind 只是相对排序工具，不应视作校准亲和力。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.7]；[doi:10.1371/journal.pcbi.1014499, p.19]
- **limitations：** 未做 BioPhi 或 OASis 之类的显式 humanness 评估，MHC II 也只是免疫原性代理，不能完整代表治疗性抗体风险。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.5]；[doi:10.1371/journal.pcbi.1014499, p.19]
- **limitations：** CLDN18.1 交叉反应性尚未被排除；AF3 和 100 ns MD 只能提供结构假设与短期稳定性信息。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.18]；[doi:10.1371/journal.pcbi.1014499, p.19]
- **limitations：** 全文仍是计算优选结果，作者也要求后续用 SPR、BLI、ELISA、细胞结合与功能实验做湿实验验证。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.19]
- **method：** 用 OAS 中经 IMGT 标准化的 CDRH3 作为先验语料，训练 8 层 GPT-2 式 decoder 做 next-token 生成。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.3]；[doi:10.1371/journal.pcbi.1014499, p.4]
- **method：** 通过 RFT 将 AlphaBind 的 kd_Pred、FvNetCharge、FvCSP、HISum 与 MHC II minPR 纳入多目标优化。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.4]；[doi:10.1371/journal.pcbi.1014499, p.5]
- **method：** 生成时固定 zolbetuximab CDRH3 的 N-terminal 'TR' 和 C-terminal 'W' motif，并限制长度在 8–14 aa，单步生成 64 条候选。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.3]；[doi:10.1371/journal.pcbi.1014499, p.6]
- **method：** 后续用 ESM2 embedding + PCA/clustering、LASSO、AF3 complex prediction 和 100 ns MD 对候选进行分层筛选。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.7]；[doi:10.1371/journal.pcbi.1014499, p.13]；[doi:10.1371/journal.pcbi.1014499, p.14]；[doi:10.1371/journal.pcbi.1014499, p.16]；[doi:10.1371/journal.pcbi.1014499, p.18]
- **results：** Epoch 6 被选为最优 checkpoint；Epoch 8 和 10 出现明显过拟合，并生成 >100 aa 的异常长序列。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.8]
- **results：** FT2 相比 Pre 和 FT1 在 FvNetCharge、FvCSP、HISum 和 MHC II 分布上更集中，说明多属性控制更稳定。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.9]；[doi:10.1371/journal.pcbi.1014499, p.10]
- **results：** Pretrained model 的 uniqueness=1.000、novelty=0.999、diversity=9.54；fine-tuned models 仍保持高 novelty/uniqueness，但 diversity 下降。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.10]
- **results：** 在 zolbetuximab 基准下，cdrGPT 在 HISum 和 FvNetCharge 上优于 AbLang/AntiBERTy，但 MHC II minPR 较弱。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.11]
- **results：** 313 条筛选候选形成三簇结构，Cluster 0 包含 zolbetuximab；7 条代表候选的 AF3 对齐保持高结构一致性，CDRH3 loop RMSD 为 1.331 Å。
  - 证据：[doi:10.1371/journal.pcbi.1014499, p.1]；[doi:10.1371/journal.pcbi.1014499, p.13]；[doi:10.1371/journal.pcbi.1014499, p.17]

## 页码证据

- [doi:10.1371/journal.pcbi.1014499, p.18]
- [doi:10.1371/journal.pcbi.1014499, p.1]
- [doi:10.1371/journal.pcbi.1014499, p.7]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
