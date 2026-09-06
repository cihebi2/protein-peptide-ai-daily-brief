# hongliangduan/HighFold

- **仓库：** [https://github.com/hongliangduan/HighFold](https://github.com/hongliangduan/HighFold)
- **固定 commit：** `278aab210114af9c28b00f95664f70c9f4056dfd`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 9

## 仓库摘要

该冻结仓库主要是 HighFold 的推理与评测快照：包含 AlphaFold/ColabFold 风格的结构预测主干、MSA/模板特征流水线、MMseqs/ColabFold 批处理封装，以及面向 cyclic peptide 与二硫键约束的少量项目特定工具；未见训练入口或 checkpoint，数据与第三方代码的许可边界需要分开审视。

## 可复用模块与资源

### datasets

- `HighFold_data/monomer_native/1bh4.pdb`
  - 能力：monomer benchmark structures
  - 用途：成对的 PDB/FASTA 基准样本，用于单体 native 对照与结构评测。
  - 复用状态：partial；类型：unknown
- `HighFold_data/mul_baseline_native/1sfi.pdb`
  - 能力：multimer baseline native structures
  - 用途：多聚体 baseline 的 native 结构集合。
  - 复用状态：partial；类型：unknown
- `HighFold_data/mul_ex_native/3wng.pdb`
  - 能力：multimer extra/native structures
  - 用途：多聚体额外评测样本的 native 结构集合。
  - 复用状态：partial；类型：unknown

### evaluation

- `utils/eval.py`
  - 能力：prediction-vs-native evaluation helper
  - 用途：评测结果汇总与指标计算入口。
  - 复用状态：ready_for_review；类型：code_entry
- `utils/fnat/dockq.py`
  - 能力：DockQ / fnat metric support
  - 用途：接触/对接类评测的底层指标实现与辅助代码。
  - 复用状态：partial；类型：code_entry

### inference

- `alphafold/model/model.py`
  - 能力：AlphaFold-style structure inference
  - 用途：核心结构推理与 folding / all-atom 组装主干。
  - 复用状态：partial；类型：code_entry
- `alphafold/data/pipeline.py`
  - 能力：feature / MSA / template construction
  - 用途：生成推理输入特征，包含 MSA 搜索、模板解析与 pair/multimer 处理。
  - 复用状态：partial；类型：code_entry
- `colabfold/batch.py`
  - 能力：ColabFold / MMseqs batch orchestration
  - 用途：批处理预测、下载、MSA 搜索与执行封装。
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `utils/cycpoem.py`
  - 能力：cyclic peptide / disulfide bridge constraint handling
  - 用途：提供项目特定的闭环与二硫键组合逻辑，支撑约束型 peptide/complex 处理。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- Static inventory only; code was not executed and tests were not run.
- No training entrypoint or training module was identified in the frozen inventory.
- No checkpoint files were identified in the frozen inventory.
- Bundled PDB/FASTA datasets are present, but their provenance/licensing is not explicit in the static evidence.
- Several large code regions look vendored from AlphaFold/ColabFold-style trees, so upstream license obligations may differ by subtree.

## 仍未知

- The exact degree of HighFold-specific modification versus vendored upstream code is not proven by path presence alone.
- The bundled datasets' original source and redistribution terms are not established by the frozen inventory.
- No inference CLI or end-user wrapper was singled out as the canonical entrypoint.
- No model checkpoints are included, so reproducible weight-based inference cannot be assessed.
- The fnat/DockQ helper subtree may have its own upstream provenance and license, which is not resolved here.

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
