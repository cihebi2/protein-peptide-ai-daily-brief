# Normalized Protein-Ligand Distance Likelihood Score for End-to-End Blind Docking and Virtual Screening

- **论文 ID：** `EVIW-7C3C8ADEABA829E3`
- **期刊 / 来源：** J Chem Inf Model
- **发表时间：** 2025 Jan 17
- **DOI：** [10.1021/acs.jcim.4c01014](https://doi.org/10.1021/acs.jcim.4c01014)
- **范围标签：** `Pi 已解析` / `核心相关` / `论文声明资源` / `蛋白-配体` / `数据集/基准`
- **基础层：** Codex 辅助专家全文审阅
- **增强层：** Pi 证据解析已完成

## 作者主张的创新点

作者提出 normalized mixture density network (NMDN) score，用 residue-atom distance likelihood 的归一化统计势做 pose selection，并加入 interaction module 预测实验 binding affinity；进一步把它与 DiffDock 结合成 DiffDock-NMDN 端到端 blind docking + virtual screening 流程，声称在 LIT-PCBA 上平均 EF1% 达到 4.96。[doi:10.1021/acs.jcim.4c01014, p.1][doi:10.1021/acs.jcim.4c01014, p.6][doi:10.1021/acs.jcim.4c01014, p.10]

## 创新边界

`主要新意在 NMDN 归一化、辅助 affinity regression 和与 DiffDock 的组合流程；本次冻结文本没有独立验证 global novelty，也不包含新的 wet-lab 发现。[doi:10.1021/acs.jcim.4c01014, p.4][doi:10.1021/acs.jcim.4c01014, p.11]`。这不是全球首创性检索或独立复现结论。

## 研究问题

在未知结合口袋的 blind docking 与 virtual screening 场景中，需要一种既能从采样姿态中稳定选出接近晶体结构的 pose，又能给出可用于筛选的 binding strength 估计；现有 DL scoring function 还存在 pocket 依赖和 cutoff 敏感的问题。[doi:10.1021/acs.jcim.4c01014, p.1][doi:10.1021/acs.jcim.4c01014, p.2]

## 方法

- ESM-2编码蛋白，混合密度网络生成几何似然分数，独立interaction模块回归pKd；DiffDock采样姿势后由NMDN排序并组合筛选分数。

## 数据与基准

- 使用PDBbind时间切分、CASF-2016、Merck FEP和LIT-PCBA；后者多为细胞表型活性，部分活性未验证直接靶点。

## 比较基线

- DiffDock、Vina/AD4、Lin_F9、GenScore及多种ML评分函数。

## 结果证据

- 作者报告LIT-PCBA上NMDN与pKd组合的平均EF1%=4.96；CASF归一化改善筛选，但不同任务优势并不一致。

## 可用资源与代码关系

- 论文中声明存在资源，但尚未建立与论文身份精确匹配的静态审计仓库。

## 已知限制

- 姿势生成受DiffDock能力约束，可能产生物理不合理构象；LIT-PCBA表型标签不能保证直接结合，且基准成本限制了完整比较。

## 仍未知

- Supporting Information 的具体超参、消融表格和原始代码实现未在主文中展开。
- 冻结文本未提供仓库 license 与数据集许可细节。
- 未独立核验 DiffDock-NMDN 在外部环境中的可复现性与性能稳定性。

## Pi 结构化证据摘录

- **baseline：** 作者明确将 DeepDock、RTMScore、GenScore 描述为依赖已知 binder pocket 或对 cutoff 敏感的 distance-likelihood/statistical-potential 类方法，并指出这限制了它们在无已知 binder 的真实虚筛场景中的适用性。[doi:10.1021/acs.jcim.4c01014, p.2]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.2]
- **baseline：** 在 PDBbind time-split blind docking 的对比中，DiffDock-NMDN(40) 的 top-1 success rate 与 DiffDock(40) 基本一致（38.4% vs 38.2%），优于 Gnina、Smina、Glide、EquiBind、TankBind 以及简单 pocket+docking 组合。[doi:10.1021/acs.jcim.4c01014, p.8]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.8]
- **baseline：** 在 blind-docked CASF-2016 评分/筛选对比中，NMDN 和 pKd 与 AD4、Vina、Vinardo、Lin_F9、ΔLin_F9 XGB、RTMScore、GenScore 同台比较；NMDN 的 screening EF1% 明显高于多数 baselines。[doi:10.1021/acs.jcim.4c01014, p.9]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.9]
- **data：** 训练 binder 数据来自 PDBBind 2020，共 19,129 complexes，经过滤后形成 12,554 training 和 1,083 evaluation complexes。[doi:10.1021/acs.jcim.4c01014, p.7]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.7]
- **data：** weak-binder 数据来自 EquiVS 和 Papyrus，经标准化和过滤后得到 250,267 protein-ligand pairs、137,417 unique molecules 与 1,196 unique proteins，其中 60,000 pairs 被随机选作 pose generation。[doi:10.1021/acs.jcim.4c01014, p.7]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.7]
- **data：** CASF-2016 包含 285 complexes/57 targets；Merck FEP 包含 264 active ligands/8 targets；PDBbind time-split 最终使用 363 entries；LIT-PCBA 包含 15 targets、10,030+ actives 和 2,798,737 inactives。[doi:10.1021/acs.jcim.4c01014, p.7][doi:10.1021/acs.jcim.4c01014, p.8]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.7]；[doi:10.1021/acs.jcim.4c01014, p.8]
- **declared_resources：** 作者在文中声明 source code 可在 GitHub 仓库公开获取，数据集可在 Zenodo 记录中获取。[doi:10.1021/acs.jcim.4c01014, p.3][doi:10.1021/acs.jcim.4c01014, p.12]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.3]；[doi:10.1021/acs.jcim.4c01014, p.12]
- **declared_resources：** 训练/推理依赖 ESM-2 650M、sPhysNet、KANO、DiffDock 及其 published pretrained weights，且 ligand solvation 还调用了先前的 sPhysNet-MT。[doi:10.1021/acs.jcim.4c01014, p.3][doi:10.1021/acs.jcim.4c01014, p.6]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.3]；[doi:10.1021/acs.jcim.4c01014, p.6]
- **declared_resources：** Acknowledgments 声明使用了 NYU-ITS computational resources，并得到 NIH R35-GM127040、Sokol fellowship 和 SCCPC fellowship 支持。[doi:10.1021/acs.jcim.4c01014, p.12]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.12]
- **limitations：** 作者承认 DiffDock-NMDN 的 pose generation 受 DiffDock 能力限制，且部分 diffusion-based docking 方法可能产生物理上不合理的构象，后处理能量最小化可能有帮助。[doi:10.1021/acs.jcim.4c01014, p.11]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.11]
- **limitations：** pKd score 只在 binder 上训练，因此在区分 binder 与 weak-binder 上表现不足；加入 weak-binder 后 screening 有改善，但仍不及 NMDN。[doi:10.1021/acs.jcim.4c01014, p.10]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.10]
- **limitations：** LIT-PCBA 中超过一半 target 采用 cell-based phenotypic assay，因此部分 actives 未必能被明确验证到假定 target；作者也说明只用一个 PDB template 以降低计算成本。[doi:10.1021/acs.jcim.4c01014, p.10]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.10]
- **method：** 蛋白残基用 ESM-2 650M 预训练模型编码，ligand atom 用 sPhysNet 编码，metal ion 用 KANO 编码；这些表征在训练中可加载预训练权重并联合微调。[doi:10.1021/acs.jcim.4c01014, p.3]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.3]
- **method：** NMDN 模块分别对 protein-ligand 与 metal-ligand pair 学习距离分布，使用 10-component Gaussian mixture，训练目标是实际距离处的负对数似然，并只对 9 Å cutoff 内的 pair 求和。[doi:10.1021/acs.jcim.4c01014, p.4]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.4]
- **method：** 推理时的 NMDN score 通过参考概率对 cutoff 附近 8.5–9.0 Å 的概率做归一化，从而增强对 cutoff 变化的稳健性。[doi:10.1021/acs.jcim.4c01014, p.4][doi:10.1021/acs.jcim.4c01014, p.5]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.4]；[doi:10.1021/acs.jcim.4c01014, p.5]
- **method：** interaction module 将 RBF 展开的 pairwise distance、protein/ligand embeddings、RMSD，以及 gas→water 和 oct→water transfer free energies 结合起来回归 experimental pKd，并可用 weak-binder 进行额外 fine-tuning。[doi:10.1021/acs.jcim.4c01014, p.5][doi:10.1021/acs.jcim.4c01014, p.6]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.5]；[doi:10.1021/acs.jcim.4c01014, p.6]
- **method：** DiffDock-NMDN 流程先用 DiffDock 采样多个 pose，再用 NMDN score 排序选 top pose，随后用 NMDN score 或 pKd score 进行 virtual screening 评估。[doi:10.1021/acs.jcim.4c01014, p.6][doi:10.1021/acs.jcim.4c01014, p.8]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.6]；[doi:10.1021/acs.jcim.4c01014, p.8]
- **results：** 在 PDBbind time-split blind docking 上，DiffDock-NMDN(40) 的 top-1 success rate 为 38.4% ± 1.5，median RMSD 为 2.98 ± 0.07 Å；与 DiffDock(40) 的 38.2% ± 1.0、3.30 ± 0.11 Å 相近且略优于 median RMSD。[doi:10.1021/acs.jcim.4c01014, p.8]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.8]
- **results：** 在标准 CASF-2016 上，NMDN score 报告 docking success 0.856、forward screening EF 34.38、forward screening success 66.7%；pKd score 报告 scoring power 0.866、ranking power 0.758。[doi:10.1021/acs.jcim.4c01014, p.8][doi:10.1021/acs.jcim.4c01014, p.9]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.8]；[doi:10.1021/acs.jcim.4c01014, p.9]
- **results：** 在 blind-docked CASF-2016 pose 上，NMDN score 的 EF1% 为 35.85、scoring power 0.376、ranking power 0.458；pKd score 的 scoring power 0.799、ranking power 0.646，而 pKd-screen 的 EF1% 提升到 7.60。[doi:10.1021/acs.jcim.4c01014, p.9][doi:10.1021/acs.jcim.4c01014, p.10]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.9]；[doi:10.1021/acs.jcim.4c01014, p.10]
- **results：** 在 Merck FEP blind-docked poses 上，pKd score 的平均 ranking power 为 0.39，NMDN score 为 0.26；在原始 benchmark 上，pKd score 的平均 ranking power 为 0.454。[doi:10.1021/acs.jcim.4c01014, p.9][doi:10.1021/acs.jcim.4c01014, p.10]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.9]；[doi:10.1021/acs.jcim.4c01014, p.10]
- **results：** 在 LIT-PCBA 上，NMDN score 平均 EF1% 为 3.90，pKd score 为 2.64，而 combined selection (pKd + NMDN) 达到 4.96，并满足 8/3/3 个 targets 在 EF1% > 2/>5/>10 阈值上。[doi:10.1021/acs.jcim.4c01014, p.10]
  - 证据：[doi:10.1021/acs.jcim.4c01014, p.10]

## 页码证据

- [doi:10.1021/acs.jcim.4c01014, p.10]
- [doi:10.1021/acs.jcim.4c01014, p.11]
- [doi:10.1021/acs.jcim.4c01014, p.1]
- [doi:10.1021/acs.jcim.4c01014, p.2]

> 发布边界：本文件仅为本地知识库的派生摘要，不含 PDF、全文抽取、源码或可执行环境。论文主张不等同于全球新颖性或独立复现结论。
