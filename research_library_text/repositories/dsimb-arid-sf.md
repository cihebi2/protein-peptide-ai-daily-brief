# dsimb/arid-sf

- **仓库：** [https://github.com/dsimb/arid-sf](https://github.com/dsimb/arid-sf)
- **固定 commit：** `dfb60e1c6969a7086455460e696de399153476db`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 16

## 仓库摘要

仓库包含 ARID 抗体-抗原 docking 评分的主实现、特征/嵌入生成、几何 Cython 扩展、示例 PDB 和两份权重；未见训练入口，数据与权重许可边界未明。

## 可复用模块与资源

### checkpoints

- `ARIDv2.0/ARID_20_Std.pt`
  - 能力：标准权重
  - 用途：推理期 scoring 权重。
  - 复用状态：unknown；类型：model_weight
- `ARIDv2.0/ARID_20_Std_preprint.pt`
  - 能力：preprint 权重
  - 用途：preprint 版本 scoring 权重。
  - 复用状态：unknown；类型：model_weight

### datasets

- `example/models/1a14/1A14_1_1578_R_1578.pdb`
  - 能力：示例对接结构集
  - 用途：bundled 示例抗体-抗原 docking 结构；同目录还有多组配对的 *_ti.pdb 变体。
  - 复用状态：partial；类型：unknown

### evaluation

- `ARIDv2.0/score_round.py`
  - 能力：round 级排序评测
  - 用途：对不同 round 的候选模型做排序/比较。
  - 复用状态：ready_for_review；类型：code_entry
- `ARIDv2.0/score_refs.py`
  - 能力：reference 对照评测
  - 用途：辅助 reference 打分或对照比较。
  - 复用状态：ready_for_review；类型：code_entry
- `example/outputs/example_output.csv`
  - 能力：示例结果表
  - 用途：示例输出，可用于人工核对排序结果格式。
  - 复用状态：partial；类型：unknown

### inference

- `ARIDv2.0/scorer.py`
  - 能力：模型打分推理
  - 用途：对输入结构计算分数并输出排名结果。
  - 复用状态：ready_for_review；类型：code_entry
- `ARIDv2.0/create_interface_features_v1.py`
  - 能力：输入特征生成
  - 用途：生成界面特征，供 scoring 推理使用。
  - 复用状态：ready_for_review；类型：code_entry
- `ARIDv2.0/get_esm_embeddings.py`
  - 能力：序列 embedding 推理
  - 用途：生成 ESM embeddings，作为推理特征输入。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `ARIDv2.0/models.py`
  - 能力：模型结构定义
  - 用途：定义 ARID 网络结构与前向组件，供打分器实例化与推理调用。
  - 复用状态：ready_for_review；类型：code_entry
- `ARIDv2.0/create_interface_features_v1.py`
  - 能力：界面特征构建
  - 用途：从抗体-抗原结构构造界面特征，作为 scoring 输入。
  - 复用状态：ready_for_review；类型：code_entry
- `ARIDv2.0/get_esm_embeddings.py`
  - 能力：序列嵌入生成
  - 用途：生成 ESM embeddings，为打分特征提供序列表征。
  - 复用状态：ready_for_review；类型：code_entry
- `ARIDv2.0/distances_v2.pyx`
  - 能力：几何距离内核
  - 用途：Cython 几何距离计算内核，支撑接触/距离类结构特征。
  - 复用状态：ready_for_review；类型：unknown
- `ARIDv2.0/voxel_features.pyx`
  - 能力：voxel 特征内核
  - 用途：Cython voxel 特征计算内核，支撑局部三维结构表示。
  - 复用状态：ready_for_review；类型：unknown
- `ARIDv2.0/scorer.py`
  - 能力：推理打分入口
  - 用途：加载模型与特征并执行 scoring / ranking 推理。
  - 复用状态：ready_for_review；类型：code_entry
- `ARIDv2.0/score_round.py`
  - 能力：排序辅助脚本
  - 用途：对候选模型进行 round 级排序或汇总，偏评测与推理辅助。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清点，未运行代码、测试或训练。
- 未见 training entrypoint / training module，训练流程无法从冻结清单中复原。
- 依赖未安装，外部模型/库调用是否可用未验证。
- 示例 PDB、CSV 与 checkpoint 的来源、许可与训练数据边界未冻结。
- 仓库含编译产物与 large blobs，部分文件可能只是静态存在而非可执行复现证据。

## 仍未知

- `example/models/1a14/` 中的结构是否全部由项目生成或从外部数据集整理不明。
- `ARID_20_Std.pt` 与 `ARID_20_Std_preprint.pt` 的训练数据、超参和验证集未见冻结证据。
- `score_round.py` / `score_refs.py` 的实际评测指标和阈值需读取源码后才能进一步确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
