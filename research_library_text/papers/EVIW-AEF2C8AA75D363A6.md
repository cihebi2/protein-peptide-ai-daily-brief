# Graphormer supervised de novo protein design method and function validation

- **论文 ID：** `EVIW-AEF2C8AA75D363A6`
- **期刊 / 来源：** Brief Bioinform
- **发表时间：** 2024 Mar 31
- **DOI：** [10.1093/bib/bbae135](https://doi.org/10.1093/bib/bbae135)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白质设计`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

提出 Graphormer-based Protein Design (GPD) 方法，把 3D 蛋白骨架图编码为 Transformer 可处理的节点/边特征，并结合随机矩阵与功能筛选流程，在 CalB 上实现可实验验证的 de novo 设计。

## 创新边界

`创新边界主要在固定骨架序列设计与功能筛选，不涉及全新 backbone 生成或通用蛋白发现；其方法创新是 Graphormer 图编码 + 随机扰动增多样性 + 湿实验验证。`。这不是全球首创性检索或独立复现结论。

## 研究问题

在固定骨架条件下生成既能保持结构可折叠性，又兼顾序列多样性与实验功能活性的蛋白序列，并评估其在酶设计中的可用性。

## 方法

- 结构图节点/边含距离、方向、旋转与二面角特征，经Graphormer预测mask残基；计算过滤后选择9条序列表达和酶活测定。

## 数据与基准

- CATH40%非冗余训练/验证/测试29,868/1,000/103；多独立结构集与CalB功能设计案例。

## 比较基线

- ProteinMPNN、ESM-IF1、ProteinSolver等inverse-folding方法。

## 结果证据

- 论文报告整体优于ProteinMPNN尤其多样性；9条候选中功能筛选得到相对WT催化活性提高1.7倍且保留C2-C16底物选择性。该部分为论文报告的湿实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 需计算过滤，部分设计折叠能力不足；功能验证只覆盖单一CalB任务和9条序列，不能外推。

## 仍未知

- 公开 GitHub 仓库与 webserver 未在本次冻结证据中实际执行验证。
- CalB 仅是单一酶例子，跨蛋白类型与跨任务泛化仍不确定。
- 1.7 倍活性提升来自单个候选 D323，相对重复性与统计稳健性在冻结证据中未完全展开。

## Pi 结构化证据摘录

- **baseline：** 主要基线包括 ProteinSolver、Structure Transformer、ESM-IF1 与 ProteinMPNN；作者指出 ProteinSolver recovery 偏低，ESM-IF1 虽 diversity 较高但计算时间长，而 ProteinMPNN 在部分 de novo 集合上 recovery 更高。
  - 证据：[doi:10.1093/bib/bbae135, p.3]；[doi:10.1093/bib/bbae135, p.5]；[doi:10.1093/bib/bbae135, p.10]
- **baseline：** 作者还把 3DCNN、ABACUS-R、ProteinMPNN 的晶体结构验证，以及 ProteinSolver 和 ProDESIGN-LE 的二级结构/圆二色验证，作为既有实验性工作对照，强调此前方法普遍缺少功能验证。
  - 证据：[doi:10.1093/bib/bbae135, p.6]
- **data：** 论文的通用 benchmark 包含 103 个 single-chain proteins、39 个 de novo proteins 和 14 个 de novo proteins；CalB 结构来自 PDB 1TCA，底物为 p-nitrophenyl acetate C2。
  - 证据：[doi:10.1093/bib/bbae135, p.2]；[doi:10.1093/bib/bbae135, p.7]；[doi:10.1093/bib/bbae135, p.11]
- **data：** CalB 设计阶段生成了 1 million 条序列；其中 40,278 条在指定七个位点满足非极性偏好，485 条通过首轮 folding/solubility 过滤，151 条进入 MD，最终 9 条进入实验验证。
  - 证据：[doi:10.1093/bib/bbae135, p.7]；[doi:10.1093/bib/bbae135, p.12]
- **declared_resources：** 训练与评测资源包括 CATH 40% sequential non-redundancy dataset、14/39/103 的 benchmark 蛋白集合，以及 CalB 的 PDB 结构 1TCA。
  - 证据：[doi:10.1093/bib/bbae135, p.7]；[doi:10.1093/bib/bbae135, p.11]
- **declared_resources：** 计算与实验资源包括 1 张 NVIDIA 40G A100 GPU、ESMFold、AlphaFold2、MOE、mdtraj、cpptraj、ff03CMAP、TIP4P-Ew，以及对外发布的 GitHub code 和 GPDGenerator webserver。
  - 证据：[doi:10.1093/bib/bbae135, p.1]；[doi:10.1093/bib/bbae135, p.7]；[doi:10.1093/bib/bbae135, p.11]；[doi:10.1093/bib/bbae135, p.12]；[doi:10.1093/bib/bbae135, p.13]
- **limitations：** 作者明确承认设计序列的 folding 仍然有限；讨论中指出单链蛋白里仅 23.6% 的 ProteinMPNN 设计达到 RMSD < 2 Å，且所有方法都仍存在 folding deficiency。
  - 证据：[doi:10.1093/bib/bbae135, p.5]；[doi:10.1093/bib/bbae135, p.10]
- **limitations：** GPD 的表达/可溶比例只有 56%，低于 ProteinMPNN 的 76% 和 ABACUS-R 的 86%；作者也说明不同类型蛋白仍需要更多湿实验来验证泛化性。
  - 证据：[doi:10.1093/bib/bbae135, p.10]
- **method：** GPD 将单个蛋白主链表示为图，节点特征包含 phi/psi 二面角、二级结构、中心性、预设计序列和随机种子，边特征包含距离、movement vector、最短路径和 rotation quaternion。
  - 证据：[doi:10.1093/bib/bbae135, p.10]；[doi:10.1093/bib/bbae135, p.11]
- **method：** 模型使用 6 层 Graphormer attention block、10 个 heads 和 1024 维 FFN，以 cross-entropy 训练；训练数据来自 CATH 40% sequential non-redundancy dataset，按 29,868:1000:103 划分，并用 Adam、batch size 64、learning rate 0.002 训练 400 epochs。
  - 证据：[doi:10.1093/bib/bbae135, p.11]
- **method：** CalB 设计流程先固定 62 个关键位点，再用 ESMFold、AlphaFold2、solubility 估计和 MD simulation 逐级筛选候选序列，最后进入湿实验表达与活性测定。
  - 证据：[doi:10.1093/bib/bbae135, p.7]；[doi:10.1093/bib/bbae135, p.12]；[doi:10.1093/bib/bbae135, p.13]
- **method：** 湿实验部分在 E. coli Rosetta(DE3) 中表达 pET22b-CalB 设计序列，并用 Nickel 柱纯化后，以 p-nitrophenyl acetate C2 的水解活性作为读出。
  - 证据：[doi:10.1093/bib/bbae135, p.13]
- **results：** 在 103 个 single-chain proteins 上，GPD 的 recovery 为 27.9%±5.4%，diversity 为 28%±5.6%，而设计 10,000 条 261 aa 序列仅需 0.97 h CPU；表中对照显示 ESM-IF1 与 ProteinMPNN 分别约为 55 h 和 3.11 h。
  - 证据：[doi:10.1093/bib/bbae135, p.3]；[doi:10.1093/bib/bbae135, p.5]；[doi:10.1093/bib/bbae135, p.10]
- **results：** 在 14 个与 39 个 de novo proteins 上，GPD 的 diversity 均优于 Structure Transformer 与 ProteinMPNN，且最小 RMSD 可达 0.469 Å 和 0.511 Å，说明其在折叠可行性上达到作者设定的可接受水平。
  - 证据：[doi:10.1093/bib/bbae135, p.3]；[doi:10.1093/bib/bbae135, p.4]；[doi:10.1093/bib/bbae135, p.5]
- **results：** CalB 湿实验中，9 个候选里有 5 个成功表达且可溶，2 个显示催化活性；D323 的 specific activity 为 0.361 ± 0.0089 U/mg，高于 wild type 的 0.210 ± 0.0065 U/mg，且文中给出 P=0.029 和约 1.7 倍提升，并显示对 C2–C16 底物的选择性。
  - 证据：[doi:10.1093/bib/bbae135, p.1]；[doi:10.1093/bib/bbae135, p.7]

## 页码证据

- [doi:10.1093/bib/bbae135, p.10]
- [doi:10.1093/bib/bbae135, p.13]
- [doi:10.1093/bib/bbae135, p.1]
- [doi:10.1093/bib/bbae135, p.2]
- [doi:10.1093/bib/bbae135, p.5]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
