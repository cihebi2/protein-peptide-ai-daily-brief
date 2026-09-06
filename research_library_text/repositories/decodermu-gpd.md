# decodermu/gpd

- **仓库：** [https://github.com/decodermu/gpd](https://github.com/decodermu/gpd)
- **固定 commit：** `b27609aeff223f25fdc6e10dadda0e94b3044c4d`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 20

## 仓库摘要

仓库是 Graphormer 蛋白设计代码与样本集的静态快照，包含核心建模、训练脚本、设计入口、若干 PDB 数据集和测试脚本，但未见显式 LICENSE 或可验证权重。

## 可复用模块与资源

### checkpoints

- `GPD/parameters/20220607_random_3.pkl`
  - 能力：checkpoint_adjacent
  - 用途：序列化参数文件，可能作为推断所需状态
  - 复用状态：unknown；类型：unknown

### datasets

- `data/sc103/1bctA00.pdb`
  - 能力：benchmark dataset
  - 用途：SC103 结构样本之一
  - 复用状态：blocked；类型：unknown
- `data/denovo14/EEHEE_rd3_0037.pdb`
  - 能力：benchmark dataset
  - 用途：denovo14 设计样本之一
  - 复用状态：blocked；类型：unknown
- `data/denovo39/1QYS.pdb`
  - 能力：benchmark dataset
  - 用途：denovo39 结构样本之一
  - 复用状态：blocked；类型：unknown
- `data/cath-dataset-nonredundant-S40-v4_3_0.pdb/download.txt`
  - 能力：external dataset pointer
  - 用途：外部 CATH 数据下载说明，未见本地完整数据
  - 复用状态：blocked；类型：unknown

### evaluation

- `test/submit_example_1.sh`
  - 能力：evaluation_harness
  - 用途：示例 1 的提交/评测脚本
  - 复用状态：blocked；类型：code_entry
- `test/submit_example_2_fixed.sh`
  - 能力：evaluation_harness
  - 用途：固定位点示例的提交/评测脚本
  - 复用状态：blocked；类型：code_entry
- `test/outputs/example_1_outputs/1tca.fasta`
  - 能力：reference_output
  - 用途：示例 1 的期望输出/断言基线
  - 复用状态：blocked；类型：unknown
- `test/outputs/example_2_fixed/1tca.fasta`
  - 能力：reference_output
  - 用途：示例 2 的期望输出/断言基线
  - 复用状态：blocked；类型：unknown

### inference

- `run_design.py`
  - 能力：code_entry
  - 用途：运行设计推断并输出候选序列
  - 复用状态：blocked；类型：code_entry
- `GPD/GPD.py`
  - 能力：code_entry
  - 用途：推断阶段的核心调用逻辑
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `GPD/GPD.py`
  - 能力：core model
  - 用途：主设计流程的核心实现
  - 复用状态：blocked；类型：code_entry
- `GPD/features/graph.py`
  - 能力：feature extraction
  - 用途：图结构/邻接特征构建
  - 复用状态：blocked；类型：code_entry
- `GPD/features/protein.py`
  - 能力：feature extraction
  - 用途：蛋白结构与序列特征预处理
  - 复用状态：blocked；类型：code_entry
- `run_design.py`
  - 能力：inference
  - 用途：设计/推断入口，生成候选序列输出
  - 复用状态：blocked；类型：code_entry
- `train/train_encoder3.py`
  - 能力：training
  - 用途：训练模块/训练流程实现
  - 复用状态：blocked；类型：code_entry
- `test/submit_example_1.sh`
  - 能力：evaluation
  - 用途：示例评测提交脚本
  - 复用状态：blocked；类型：code_entry
- `test/submit_example_2_fixed.sh`
  - 能力：evaluation
  - 用途：固定位点示例评测脚本
  - 复用状态：blocked；类型：code_entry
- `GPD/parameters/20220607_random_3.pkl`
  - 能力：checkpoint_adjacent
  - 用途：序列化参数/状态文件，可能被设计流程加载
  - 复用状态：unknown；类型：unknown

### training

- `train/train_encoder3.py`
  - 能力：training_module
  - 用途：训练/编码器训练逻辑
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- 仓库未见显式 LICENSE，代码/数据/模型的直接再利用边界不可确认。
- 未发现可验证的显式模型权重文件；`GPD/parameters/20220607_random_3.pkl` 仅能视作序列化参数/检查点邻接文件。
- 外部 CATH 数据仅见下载说明，无法区分本地冻结数据与外部依赖。

## 仍未知

- `GPD/parameters/20220607_random_3.pkl` 的实际内容未解析，无法确认是否为可直接加载的权重。
- `train/train_encoder3.py` 的真实输入数据与训练产物未从静态元数据中确认。
- README 内容未单独抽读，因此无法补充作者自述的许可或数据来源细节。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
