# In silico screening of protein-binding peptides with an application to developing peptide inhibitors against antibiotic resistance

- **论文 ID：** `EVIW-CFF2D809F391FE3C`
- **期刊 / 来源：** PNAS Nexus
- **发表时间：** 2024 Nov 27
- **DOI：** [10.1093/pnasnexus/pgae541](https://doi.org/10.1093/pnasnexus/pgae541)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `肽与抗菌肽`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

作者提出 MDockPeP2_VS，把蛋白-肽对接、界面保守性评分和自动过滤结合起来，实现对蛋白结合肽的自动化大规模筛选，并在 TEM-1 β-lactamase 上发现了抑制肽 TF7。

## 创新边界

`该文的边界是一个面向 TEM-1 的 proof-of-concept 筛选流水线；冻结证据本身不足以独立验证其“first large-scale”全球新颖性主张，也未证明对所有靶标都同等有效。`。这不是全球首创性检索或独立复现结论。

## 研究问题

现有蛋白-肽对接与筛选方法因肽柔性高、序列空间巨大而难以扩展到任意蛋白靶标，因而缺少可用于大规模结构基础 peptide screening 的实用方案。

## 方法

- 结构fragment library、peptide docking/ranking、top candidates实验。

## 数据与基准

- PDB fragments、TEM-1 target、top10 peptides。

## 比较基线

- 常规peptide docking/library methods。

## 结果证据

- TF7实验抑制β-lactamase，Ki 1.37±0.37 µM。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 单靶/少候选，细胞/体内抗性恢复未知。

## 仍未知

- 外部网站下载包和源码未核验。
- 未独立验证“first large-scale”全球新颖性主张。
- 对非α螺旋肽、长肽和金属离子靶标的泛化仍需更多证据。

## Pi 结构化证据摘录

- **baseline：** 与 AutoDock Vina 相比，Vina_pep 在速度和 cL-RMSD 上都更优，是本文直接替换的基线方法。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.4]
- **baseline：** 作者还把 AlphaFold-Multimer 作为独立对照；其在 TF7 和 TF10 上的一致性被用来提升命中率，而对其他候选则常给出不同结合模式。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.6]；[doi:10.1093/pnasnexus/pgae541, p.7]
- **baseline：** 与先前 phage display 得到的 TEM-1 肽抑制剂 RRGHYY-NH2（Ki = 136 µM）相比，TF7 约强两个数量级。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.5]
- **data：** 基准评测使用 PepPro 数据集，共 89 个非冗余 protein–peptide complexes，肽长覆盖 5–29 aa。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.4]
- **data：** 面向 TEM-1 的筛选库最终输出前 10 个候选，其中 TF7 序列 KTYLAQAAATG 来自 1coyA_230–240；其中 4 条候选因低溶解度未进入酶学实验。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.5]
- **data：** 实验验证使用 5 nM TEM-1 与 nitrocefin 的 β-lactamase 活性测定，并对 TF7 在 TEM-1、N52A、E104A 和 M270R 上进行 MST 结合实验。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.5]；[doi:10.1093/pnasnexus/pgae541, p.6]；[doi:10.1093/pnasnexus/pgae541, p.9]
- **declared_resources：** 论文声明 MDockPeP2_VS 程序和相关数据可在项目网站下载，且计算资源来自 University of Missouri Bioinformatics Consortium 的 HPC 集群。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.5]；[doi:10.1093/pnasnexus/pgae541, p.10]
- **declared_resources：** TEM-1 重组蛋白来源于 Addgene plasmid #62729，并在 BL21(DE3) 中表达纯化。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.9]
- **limitations：** 当前库只覆盖 α 螺旋片段和 10–15 aa 区间，作者自己也指出可扩展到其他二级结构以及更短/更长肽。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.7]；[doi:10.1093/pnasnexus/pgae541, p.8]
- **limitations：** 对接中蛋白被视为刚性，且当前版本缺少对锌等离子的参数，因此不能直接用于 NDM 类金属 β-lactamase。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.7]；[doi:10.1093/pnasnexus/pgae541, p.8]
- **limitations：** 评分函数未显式建模溶剂化，而且部分候选肽存在低溶解度或需要 30 分钟预孵育才显效，说明构象诱导与可开发性仍是限制。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.7]；[doi:10.1093/pnasnexus/pgae541, p.5]；[doi:10.1093/pnasnexus/pgae541, p.9]
- **method：** MDockPeP2_VS 先从 PDB 单体蛋白中提取 10–15 aa 的 α 螺旋片段，构建 76,223 条非冗余肽条目；每条条目同时包含序列、由 MODELLER 生成的构象和 fragment–protein pair。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.8]
- **method：** 对接阶段使用改写版 AutoDock Vina（Vina_pep），把 exhaustiveness 提高到 64，并把搜索步数从默认公式改为 (m + 10n)；肽主链在对接时视为刚性，而侧链保持柔性。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.8]
- **method：** 排序阶段采用 PepProScore = Vina_Score + w×PC_Score，且 w 设为 −9；随后还按疏水暴露、连续疏水残基数以及 Proline 含量进行自动过滤。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.8]；[doi:10.1093/pnasnexus/pgae541, p.9]
- **results：** 在 PepPro 数据集上，Vina_pep 平均每个对接仅需 13 min/core，而 AutoDock Vina 约需 3.6 CPU hours；其 cL-RMSD 在 top1/5/10 分别为 1.5/1.2/1.1 Å，优于 Vina 的 1.8/1.5/1.5 Å。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.4]
- **results：** 在 TEM-1 筛选中，8 小时内用 1,000 cores 完成全库筛选，TF7 的 PepProScore 为 −12.12、PC_Score 为 0.55，并在 6 条可溶候选中表现出显著抑制。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.5]
- **results：** TF7 对 TEM-1 的抑制常数 Ki 为 1.37 ± 0.37 µM，MST 测得 Kd 为 0.96 ± 0.26 µM；Lineweaver–Burk 分析显示其为 competitive inhibition，且 E104A 与 M270R 削弱了结合。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.5]；[doi:10.1093/pnasnexus/pgae541, p.6]
- **results：** MDockPeP2_VS 与 AlphaFold-Multimer 对 TF7 和 TF10 给出相近构象，而多数未活性肽的 L-RMSD 较大，支持把两者一致性作为额外筛选条件。
  - 证据：[doi:10.1093/pnasnexus/pgae541, p.6]；[doi:10.1093/pnasnexus/pgae541, p.7]

## 页码证据

- [doi:10.1093/pnasnexus/pgae541, p.1]
- [doi:10.1093/pnasnexus/pgae541, p.2]
- [doi:10.1093/pnasnexus/pgae541, p.3]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
