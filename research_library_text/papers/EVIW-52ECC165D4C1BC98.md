# Computationally designed proteins mimic antibody immune evasion in viral evolution

- **论文 ID：** `EVIW-52ECC165D4C1BC98`
- **期刊 / 来源：** Immunity（DOI 前缀识别）
- **发表时间：** 未记录
- **DOI：** [10.1016/j.immuni.2025.04.015](https://doi.org/10.1016/j.immuni.2025.04.015)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源`
- **Pi 状态：** 已完成结构化解析

## 作者主张的创新点

提出 EVE-Vax 计算设计流程，在五个 SARS-CoV-2 VOC 背景上生成 83 个多突变 spike 构型，并通过伪病毒中和、抗原图谱与 NHP 血清实验验证其可复现未来免疫逃逸。

## 创新边界

`新意主要在“计算生成并实验验证”多突变未来样式抗原面板；它不是临床疗效验证，也不是广义蛋白设计基准。`。这不是全球首创性检索或独立复现结论。

## 研究问题

当前疫苗和治疗评估主要基于过去或当下流行变体，难以前瞻性判断未来病毒进化下的免疫逃逸风险，因此需要能在安全伪病毒体系中生成未来样式抗原面板的计算方法。

## 方法

- 进化模型生成多突变spike，构建pseudovirus并用多组人血清neutralization assays验证。

## 数据与基准

- 83 designed constructs、66设计pseudovirus、20 SARS-CoV-2 variants、9组人血清。

## 比较基线

- 随机/常见突变组合、DMS-derived designs和自然variants。

## 结果证据

- 75/83（90%）设计在单轮pseudovirus assay具infectivity；多设计显示后续variant样escape。为明确实验。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 对其他病毒依赖足够进化记录；pseudovirus不等于真实传播/致病，10%设计失活。

## 仍未知

- 这些设计在真实流行环境中的前瞻预测能力尚未被独立外部验证。
- 对其他病毒或抗原的推广性仍取决于序列记录密度与功能约束是否足够。
- 研究主要覆盖中和抗体，未系统评估 T 细胞或其他免疫机制。
- 本次分析未额外核验所述 GitHub 仓库与资源库的实际可用性。

## Pi 结构化证据摘录

- **baseline：** 作者以 error-prone PCR 的 RBD、full spike、Lassa GPC 和 GFP 多突变库作为功能性基线，指出突变深度上升时可行序列比例会快速下降。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.5]；[doi:10.1016/j.immuni.2025.04.015, p.15]；[doi:10.1016/j.immuni.2025.04.015, p.16]
- **baseline：** 文中还把 EVE-Vax 与 pre-pandemic 的 EVEscape 以及 20 项 DMS 研究做历史对照，报告其在流行期间被观察到的 escape mutations 比例更高。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.8]；[doi:10.1016/j.immuni.2025.04.015, p.9]；[doi:10.1016/j.immuni.2025.04.015, p.16]
- **data：** 本研究设计了 83 个多突变 spike，覆盖 B.1、BA.4/5、BA.2.12.1、BA.2.75 与 XBB 五个背景，单个构型最多含 10 个相对背景的新增组合变异。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.5]
- **data：** 中和实验使用 115 份人血清样本，汇成 23 个 serum pools，覆盖自然感染、疫苗接种、加强针和多种 breakthrough infection 场景。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.11]；[doi:10.1016/j.immuni.2025.04.015, p.6]
- **data：** 还纳入 14 只 NHP 的 booster sera，比较 bivalent mRNA、mosaic-8b nanoparticle 与 homotypic nanoparticle 三种方案。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.11]；[doi:10.1016/j.immuni.2025.04.015, p.8]
- **data：** 测试对象包括 66 个设计 spike、20 个 SARS-CoV-2 变体以及 SARS-CoV-1 spike。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.6]
- **declared_resources：** 论文在 Data and code availability 中明确给出 GitHub 仓库 https://github.com/debbiemarkslab/Vax_design，并说明所有分析代码可公开获取。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.1]
- **declared_resources：** 生成的 plasmids 已存入 Addgene，且表 S2 提供了项目内构建体清单；这属于论文级资源声明而非外部可复用性核验。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.1]；[doi:10.1016/j.immuni.2025.04.015, p.31]
- **declared_resources：** Key Resources Table 列出了关键数据、结构与软件依赖，包括 GISAID、PDB、EVE-Vax、EVEscape、Racmacs 和 Jackhmmer。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.31]；[doi:10.1016/j.immuni.2025.04.015, p.32]
- **limitations：** 方法对其他抗原的可推广性取决于可用序列演化记录是否足够，尤其是欠采样病毒可能难以学习到可靠的功能约束。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.10]
- **limitations：** 作者明确承认该框架主要聚焦抗体中和，未系统纳入 T-cell mediated immunity 等长期保护机制。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.10]
- **limitations：** 作者也指出，未来变体预测在原则上可能被滥用，因此需要负责任地开发和共享相关信息。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.10]
- **method：** EVE-Vax 以 EVEscape 为基础，把 fitness、antibody accessibility 与 mutation dissimilarity 三类约束合成为单突变逃逸分数，再按高分单突变、双突变到多突变的顺序扩展设计。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.12]；[doi:10.1016/j.immuni.2025.04.015, p.13]
- **method：** 模型训练同时利用 pre-pandemic 与疫情期间的 spike 序列比对；对 B.1 还比较了仅用前疫情冠状病毒序列的模型与加入 SARS-CoV-2 序列后的更新模型。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.12]
- **method：** 设计后的 spike 以 pDMJ2 载体表达，并在 replication-incompetent lentiviral pseudotype 体系中，于 293T/ACE2 或 ACE2/TMPRSS2 细胞上测试感染性和中和敏感性。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.13]；[doi:10.1016/j.immuni.2025.04.015, p.14]；[doi:10.1016/j.immuni.2025.04.015, p.15]
- **method：** 抗原图谱使用 Racmacs 和 MDS，根据 23 个 serum pools 的中和滴度构建二维 antigenic cartography。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.18]；[doi:10.1016/j.immuni.2025.04.015, p.27]
- **results：** 83 个设计中有 75 个（90%）在伪病毒感染实验中保持感染性，整体成功率高于文中对随机多突变或高突变负担序列的经验参照。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.5]
- **results：** 设计 spike 的中和抗性总体上可复现后续自然演化变体，平均相对父背景约 1.9-fold 下降，且若干构型如 B.1-4a、BA.4/5-2a 和 BA.2.75-4c 与后续 VOC 的免疫逃逸水平相近。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.6]
- **results：** 抗原图谱显示，早期背景上设计的 construct 能在抗原空间上靠近更晚出现的变体，例如 BA.2.12.1-5a 近似 BA.2.75，而 XBB 设计可接近 HV.1 和 CH.1.1 的轨迹。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.7]；[doi:10.1016/j.immuni.2025.04.015, p.27]
- **results：** 对 B.1-BA.4/5 bivalent booster 而言，设计面板中出现的低滴度区间提示了后续 XBB.1、XBB.1.5 和 CH.1.1 的逃逸潜力。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.7]；[doi:10.1016/j.immuni.2025.04.015, p.28]
- **results：** 在 NHP 中，mosaic-8b nanoparticle 对设计构型的中和滴度普遍高于 bivalent mRNA 与 homotypic nanoparticle，提示更强交叉反应性。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.8]；[doi:10.1016/j.immuni.2025.04.015, p.28]
- **results：** 与 assay-derived constructs 相比，EVE-Vax constructs 在较少突变数下达到了可比的多克隆逃逸水平。
  - 证据：[doi:10.1016/j.immuni.2025.04.015, p.9]；[doi:10.1016/j.immuni.2025.04.015, p.29]；[doi:10.1016/j.immuni.2025.04.015, p.30]

## 页码证据

- [doi:10.1016/j.immuni.2025.04.015, p.10]
- [doi:10.1016/j.immuni.2025.04.015, p.2]
- [doi:10.1016/j.immuni.2025.04.015, p.5]
- [doi:10.1016/j.immuni.2025.04.015, p.6]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
