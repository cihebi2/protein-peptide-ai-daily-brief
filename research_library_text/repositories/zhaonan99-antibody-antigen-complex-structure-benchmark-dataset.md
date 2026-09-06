# Zhaonan99/Antibody-antigen-complex-structure-benchmark-dataset

- **仓库：** [https://github.com/Zhaonan99/Antibody-antigen-complex-structure-benchmark-dataset](https://github.com/Zhaonan99/Antibody-antigen-complex-structure-benchmark-dataset)
- **固定 commit：** `6891e6e6790c7a898a08471193f494adf6f16b48`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 4

## 仓库摘要

仓库是 antibody-antigen docking 的 benchmark 数据集发布版，主体为大量 PDB 结构文件和一个 PDBID 索引文本；未发现可执行方法、训练、推理、评估或 checkpoint 资产。

## 可复用模块与资源

### datasets

- `ABAG-Docking_benchmark_dataset/25cases_Not_truncated_file/6P50/6P50_l_b.pdb`
  - 能力：benchmark_structure_set
  - 用途：25 个案例的非截断结构子集；从文件命名看包含链/状态配对的 PDB 结构，用于 benchmark 分发
  - 复用状态：blocked；类型：unknown
- `ABAG-Docking_benchmark_dataset/25cases_Truncated_file/6P50/6P50_l_b.pdb`
  - 能力：benchmark_structure_set
  - 用途：25 个案例的截断结构子集；用于与非截断版本并行分发/对照
  - 复用状态：blocked；类型：unknown
- `ABAG-Docking_benchmark_dataset/87cases/5ZUF/5ZUF_l_b.pdb`
  - 能力：benchmark_structure_set
  - 用途：87 个案例的扩展结构集合；作为另一组 benchmark 样本分发
  - 复用状态：blocked；类型：unknown
- `ABAG-Docking_benchmark_dataset_PDBID.txt`
  - 能力：case_index
  - 用途：PDBID 索引/案例清单，辅助定位数据集条目
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态盘点，未执行任何代码、测试或数据处理流程。
- 仓库没有发现训练/推理/评估入口，不能据此推断可复现实验。
- 没有 LICENSE，代码与数据的授权边界不明。
- 仅凭文件存在不能证明这些 PDB 与论文中的最终发布版本完全一致。

## 仍未知

- `README.txt` 的完整使用说明、引用要求和数据来源未在当前清单中展开。
- `ABAG-Docking_benchmark_dataset_PDBID.txt` 的具体内容未读到，只能从文件名判断其为索引文本。
- `25cases_*` 与 `87cases` 的构造关系、筛选规则和去冗余标准未被当前静态清单直接证明。
- PDB 文件的上游来源及是否包含第三方整理/重命名步骤未能从库存中确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
