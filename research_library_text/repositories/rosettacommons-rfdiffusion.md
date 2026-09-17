# rosettacommons/rfdiffusion

- **仓库：** [https://github.com/rosettacommons/rfdiffusion](https://github.com/rosettacommons/rfdiffusion)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1101/2025.09.29.678898
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** BSD-2-Clause (University of Washington)
- **语言：** Python
- **复用度：** high —— 工业级标准工具：22个可直接套用的条件设计示例脚本、conda环境、Docker镜像、Colab教程与权重下载脚本齐备，社区维护活跃；不含训练代码但推理复现门槛极低。
- **能力：** inference、protocol、benchmark

## 仓库摘要

RFdiffusion：基于 RoseTTAFold 的开源蛋白质结构去噪扩散生成方法，支持无条件生成、motif 骨架化、binder 设计、对称寡聚体和大环肽(RFpeptides)等多种条件化设计模式，是蛋白质设计的标准引擎。

## 入口脚本

- scripts/run_inference.py
- examples/design_ppi.sh
- examples/design_motifscaffolding.sh
- examples/design_macrocyclic_binder.sh
- examples/design_unconditional.sh
- examples/ 内共22个条件设计示例脚本

## 数据加载

- rfdiffusion/inference/utils.py (PDB输入解析)
- examples/input_pdbs/

## 模型权重

- 仓库不含权重；scripts/download_models.sh 及 README 提供 files.ipd.uw.edu 下载链接 (Base_ckpt.pt, Complex_base_ckpt.pt, Complex_Fold_base_ckpt.pt, InpaintSeq_ckpt.pt 等)

## 评测基准

- tests/test_diffusion.py
- helper_scripts/make_secstruc_adj.py

## 文档

- README.md (详尽使用文档)
- tutorials/
- docker/ (官方Docker镜像 rosettacommons/rfdiffusion)
- env/SE3nv.yml (conda环境)

## 课题关联

- L1 蛋白设计(核心生成引擎)
- C004 binder/PPI(design_ppi*.sh)
- C007 条件生成(motif/折叠/对称性条件化)
- L4 肽生成(大环肽 RFpeptides: design_macrocyclic_*.sh)

## 与论文/课题的组合方式

- 按 examples/design_ppi*.sh 复现 binder/PPI 设计流程，作为 C004 与 L1 课题的生成基座
- 用 design_ppi_flexible_peptide*.sh 做柔性肽 binder 设计，其输出可直接接入 ProDCARL 的 pAMP/pTox 分类器做活性-毒性级联筛选
- 作为 C007 条件生成的结构级对照组：比较扩散条件化(RFdiffusion)与 RL 对齐条件化(ProDCARL)两种肽/蛋白生成范式
