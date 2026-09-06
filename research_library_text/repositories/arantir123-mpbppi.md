# arantir123/MpbPPI

- **仓库：** [https://github.com/arantir123/MpbPPI](https://github.com/arantir123/MpbPPI)
- **固定 commit：** `9bf9241dc6392b9cf1e44f214e03bfd7cd8eec54`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 15

## 仓库摘要

该仓库是 MpbPPI 的静态快照，含预训练、ddG 预测、FoldX 基线、数据切分与结构预处理产物；仅能确认文件存在，不能证明可复现运行。

## 可复用模块与资源

### datasets

- `data/M1101.csv`
  - 能力：下游突变效应基准表
  - 用途：保存四套下游 ddG/突变效应数据表
  - 复用状态：partial；类型：unknown
- `data/M1101_foldx_cleaned/1_wt_pdb/1JRH__139.pdb`
  - 能力：处理后的结构与 FoldX 中间产物
  - 用途：保存 wild-type/mutant PDB、SASA 与 FoldX 输出，供下游预测与分析使用
  - 复用状态：partial；类型：unknown
- `data/pretraining_data_split.json`
  - 能力：预训练切分配置
  - 用途：定义 pretraining 数据划分与样本组织方式
  - 复用状态：partial；类型：config

### evaluation

- `data/M1101_CV10_random_data_split_256.jsonl`
  - 能力：10-fold 随机评测切分
  - 用途：提供四套下游任务的 CV10 评测划分
  - 复用状态：partial；类型：unknown
- `data/M1101_complex_data_split_256.jsonl`
  - 能力：complex-aware 评测切分
  - 用途：提供按 complex 组织的评测划分
  - 复用状态：partial；类型：unknown

### inference

- `_4_run_MpbPPI_ddg_prediction.py`
  - 能力：ddG 预测入口
  - 用途：对突变样本执行 MpbPPI 预测/打分
  - 复用状态：partial；类型：code_entry
- `inference_script_backup.py`
  - 能力：备用推理脚本
  - 用途：备份推理流程或历史入口
  - 复用状态：partial；类型：code_entry
- `_5_foldx_mutation_prediction.py`
  - 能力：FoldX 预测/对照推理
  - 用途：执行 FoldX 基线预测
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `_1_run_cleaning_pdb.py`
  - 能力：结构清洗、sidechain 补全与 mutation 规范化
  - 用途：清洗输入 PDB、补全侧链并统一突变表示，供后续特征构建与预测使用
  - 复用状态：ready_for_review；类型：code_entry
- `_3_generate_interface_mutation.py`
  - 能力：接口突变、JSON 输入与 residue features 生成
  - 用途：构建模型输入、接口突变样本与预训练/微调所需残基特征
  - 复用状态：ready_for_review；类型：code_entry
- `_3_datasplit_downstream.py`
  - 能力：数据切分生成器
  - 用途：生成下游评测切分与预训练切分
  - 复用状态：ready_for_review；类型：code_entry
- `gvp/models.py`
  - 能力：GVP 模型实现
  - 用途：提供图/几何感知模型结构定义
  - 复用状态：partial；类型：code_entry
- `_5_foldx_mutation_prediction.py`
  - 能力：FoldX 基线封装
  - 用途：执行基于 FoldX 的突变效应预测/对照实验
  - 复用状态：partial；类型：code_entry

### training

- `_4_run_pretraining_MpbPPI_aadenoising_rgraph.py`
  - 能力：预训练入口
  - 用途：运行 MpbPPI 的自编码/去噪图预训练流程
  - 复用状态：partial；类型：code_entry
- `_4_run_MpbPPI_ddg_prediction_gbtfeatselect.py`
  - 能力：下游特征选择/训练辅助
  - 用途：为 ddG 预测阶段做特征选择或训练辅助
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码、未安装依赖、未运行测试。
- 文件路径存在不等于可复现；数据、checkpoint 与脚本参数的一致性未验证。
- `gvp/models.py` 的外部来源、是否 vendored 以及是否与论文实现完全一致均未核实。
- `inference_script_backup.py` 仅表明存在备份入口，主推理路径与默认配置未验证。

## 仍未知

- 原始 CSV 数据的上游来源、版权与是否为作者自制整理未能从静态清单确认。
- `storage_pretraining/*.pt` 是否为最终论文同款权重，还是中间训练产物，未能确认。
- 仓库中未见独立 evaluation 脚本，CV10/complex 切分文件只能证明评测资产存在。
- `README.md` 和文档未解析其运行步骤，因此完整训练/推理命令链仍有空白。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
