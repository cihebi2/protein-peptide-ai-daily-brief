# 24atang/SMILES-Alignment

- **仓库：** [https://github.com/24atang/SMILES-Alignment](https://github.com/24atang/SMILES-Alignment)
- **固定 commit：** `d09d55909c75e6811f290c2be0592fdb70f00251`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 8

## 仓库摘要

仓库主要是 SMILES alignment 的脚本集合，包含 all-vs-all / pairwise 对齐、打分和 canonicalization，以及示例 SMILES 和两个序列化分数文件；未见训练入口、模型 checkpoint 或明确 LICENSE。

## 可复用模块与资源

### datasets

- `smiles.txt`
  - 能力：input SMILES list / example set
  - 用途：脚本输入或示例分子集合
  - 复用状态：unknown；类型：unknown

### evaluation

- `All_vs_All_Scoring.py`
  - 能力：all-vs-all alignment scoring
  - 用途：对全对全对齐结果评分/排序；未见独立基准评测入口
  - 复用状态：blocked；类型：code_entry
- `Paired_Scoring.py`
  - 能力：paired alignment scoring
  - 用途：对两两对齐结果评分/排序；未见独立基准评测入口
  - 复用状态：blocked；类型：code_entry

### inference

- `All_vs_All_Alignment.py`
  - 能力：all-vs-all SMILES alignment
  - 用途：执行全对全的 dynamic programming 式对齐
  - 复用状态：blocked；类型：code_entry
- `Paired_Alignment.py`
  - 能力：paired SMILES alignment
  - 用途：执行两两 SMILES 对齐
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `Canonization_Script.py`
  - 能力：SMILES canonicalization
  - 用途：对输入 SMILES 做标准化/规范化，作为后续对齐前处理
  - 复用状态：blocked；类型：code_entry
- `score_all_v_all.pkl`
  - 能力：serialized all-vs-all score table
  - 用途：预计算/缓存的打分结果；更像运行产物而非模型 checkpoint
  - 复用状态：unknown；类型：unknown
- `score_pair_doubles.pkl`
  - 能力：serialized pairwise score table
  - 用途：预计算/缓存的打分结果；更像运行产物而非模型 checkpoint
  - 复用状态：unknown；类型：unknown

## 使用限制

- 仅做静态审计，未执行代码、未安装依赖、未运行测试
- path presence 不能证明脚本可运行或可复现
- 未核验第三方依赖的许可与兼容性
- score_*.pkl 与 smiles.txt 的 provenance 未确认，可能是运行产物、缓存或示例数据

## 仍未知

- smiles.txt 是示例输入、基准数据还是论文数据集未明
- score_all_v_all.pkl / score_pair_doubles.pkl 是否为运行产物、缓存还是可分发数据未明
- README 是否包含额外使用说明或许可信息未核验

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
