# hysonlab/protein_redesign

- **仓库：** [https://github.com/hysonlab/protein_redesign](https://github.com/hysonlab/protein_redesign)
- **固定 commit：** `12d2f238912a4b709d4086e2800d7dcb86effdbc`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 22

## 仓库摘要

该仓库主要实现 ProteinReDiff 的扩散式蛋白重设计流程，包含模型定义、数据预处理、训练入口、批量推理脚本以及一个 results.pt checkpoint；代码许可为 MIT，但数据切分文件与权重文件的单独再利用边界未充分说明。

## 可复用模块与资源

### checkpoints

- `results.pt`
  - 能力：model_checkpoint
  - 用途：单个结果/权重 checkpoint，可用于继续训练或推理。
  - 复用状态：partial；类型：model_weight

### datasets

- `data/PRD_train_pdb_ids`
  - 能力：dataset_split
  - 用途：训练集 PDB ID 切分文件。
  - 复用状态：partial；类型：unknown
- `data/PRD_val_pdb_ids`
  - 能力：dataset_split
  - 用途：验证集 PDB ID 切分文件。
  - 复用状态：partial；类型：unknown
- `data/PRD_test_pdb_ids`
  - 能力：dataset_split
  - 用途：测试集 PDB ID 切分文件。
  - 复用状态：partial；类型：unknown
- `preprocess_pdbbind.py`
  - 能力：data_preparation
  - 用途：PDBbind 预处理与样本整理。
  - 复用状态：ready_for_review；类型：code_entry

### evaluation

- `ProteinReDiff/tmalign.py`
  - 能力：structure_alignment_helper
  - 用途：结构对齐/TM-align 风格的评估辅助。
  - 复用状态：partial；类型：code_entry
- `scripts/test_pdb.smiles`
  - 能力：test_fixture
  - 用途：推理/回归测试用的分子输入样例。
  - 复用状态：partial；类型：unknown
- `scripts/test_sequences_from_pdb.fasta`
  - 能力：test_fixture
  - 用途：推理/回归测试用的序列输入样例。
  - 复用状态：partial；类型：unknown

### inference

- `generate.py`
  - 能力：generation_entrypoint
  - 用途：生成式推理主入口。
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/predict_batch_seq_msk_inp.py`
  - 能力：batch_sequence_prediction
  - 用途：批量序列预测，支持 masked input。
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/predict_batch_strc_msk_inp.py`
  - 能力：batch_structure_prediction
  - 用途：批量结构预测，支持 masked input。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `ProteinReDiff/model.py`
  - 能力：model_architecture
  - 用途：定义主生成/重设计模型与前向计算。
  - 复用状态：ready_for_review；类型：code_entry
- `ProteinReDiff/models/AF2_modules.py`
  - 能力：model_architecture
  - 用途：提供 AF2 风格的结构模块与几何/注意力组件。
  - 复用状态：partial；类型：code_entry
- `ProteinReDiff/models/utils.py`
  - 能力：model_architecture
  - 用途：提供模型侧辅助函数与几何工具。
  - 复用状态：ready_for_review；类型：code_entry
- `ProteinReDiff/difffusion.py`
  - 能力：model_architecture
  - 用途：实现扩散过程与噪声调度相关逻辑。
  - 复用状态：ready_for_review；类型：code_entry
- `ProteinReDiff/features.py`
  - 能力：feature_engineering
  - 用途：构建输入特征。
  - 复用状态：ready_for_review；类型：code_entry
- `ProteinReDiff/protein.py`
  - 能力：representation
  - 用途：蛋白结构表示、解析与相关处理。
  - 复用状态：ready_for_review；类型：code_entry
- `ProteinReDiff/mol.py`
  - 能力：ligand_processing
  - 用途：配体/SMILES 处理与分子表示。
  - 复用状态：ready_for_review；类型：code_entry
- `ProteinReDiff/mask_utils.py`
  - 能力：masking
  - 用途：序列/结构 mask 逻辑。
  - 复用状态：ready_for_review；类型：code_entry

### training

- `train.py`
  - 能力：training_entrypoint
  - 用途：主训练入口。
  - 复用状态：ready_for_review；类型：code_entry
- `train_from_ckpt.py`
  - 能力：training_module
  - 用途：从 checkpoint 继续训练或微调。
  - 复用状态：ready_for_review；类型：code_entry
- `ProteinReDiff/data.py`
  - 能力：data_loader
  - 用途：训练/推理数据加载与 batch 构造。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码、未安装依赖、未运行测试。
- 未见原始训练数据打包；只有 PDB ID 切分文件与少量测试输入样例。
- evaluation 没有独立的 benchmark 脚本，主要只见 TM-align 辅助文件。
- checkpoint 的训练来源与可复现性未验证。

## 仍未知

- environment.yml 的依赖解析与 CUDA/PyTorch 兼容性未验证。
- results.pt 是否为最终权重、最佳验证权重或演示权重，静态清单无法确认。
- ProteinReDiff/tmalign.py 是否为项目自写实现或第三方移植，无法仅凭路径断定。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
