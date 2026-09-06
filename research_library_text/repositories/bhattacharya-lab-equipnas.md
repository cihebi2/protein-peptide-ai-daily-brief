# Bhattacharya-Lab/EquiPNAS

- **仓库：** [https://github.com/Bhattacharya-Lab/EquiPNAS](https://github.com/Bhattacharya-Lab/EquiPNAS)
- **固定 commit：** `065563064f68ea9ec102ed524876df490dbc848d`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 12

## 仓库摘要

该仓库的冻结提交主要包含 EquiPNAS 的预处理脚本、特征生成脚本、数据加载器和模型相关代码；可见少量示例输入与派生特征，但未见独立训练入口、评估脚本或 checkpoint 文件。代码许可证为 GPL-3.0；示例数据与模型相关资产未见单独许可声明，因此数据/模型重用边界不完整。

## 可复用模块与资源

### datasets

- `Preprocessing/input/4zm2_B.pdb`
  - 能力：bundled example inputs
  - 用途：2 个样例复合体 4zm2_B、5cr2_A 的原始/中间输入，包含 .pdb、.fasta、.pssm、.dssp、.npy
  - 复用状态：partial；类型：unknown
- `Preprocessing/distmaps/4zm2_B.dist`
  - 能力：precomputed distance maps
  - 用途：样例复合体的距离/接触图
  - 复用状态：partial；类型：unknown
- `Preprocessing/processed_features/4zm2_B.5461featnew.npy`
  - 能力：preprocessed node features
  - 用途：样例复合体的 5461featnew.npy 特征缓存
  - 复用状态：partial；类型：unknown

### inference

- `EquiPNAS.py`
  - 能力：protein-nucleic acid binding site prediction
  - 用途：主模型/前向预测脚本的候选入口；仅有静态路径证据，未执行验证
  - 复用状态：unknown；类型：code_entry
- `egnn_clean.py`
  - 能力：EGNN backbone
  - 用途：图神经网络骨干/辅助实现，可能被主预测脚本调用
  - 复用状态：unknown；类型：code_entry

### reusable_assets

- `Dataloader.py`
  - 能力：data loading
  - 用途：读取并组织预处理后的样本与特征，供主模型流程消费
  - 复用状态：partial；类型：code_entry
- `Preprocessing/atomic_feature.py`
  - 能力：atomic / geometric feature preprocessing
  - 用途：生成原子级或结构级输入特征
  - 复用状态：partial；类型：code_entry
- `Preprocessing/extract_dssp_feat.py`
  - 能力：DSSP feature extraction
  - 用途：从 DSSP 提取二级结构相关特征
  - 复用状态：partial；类型：code_entry
- `Preprocessing/genpssmto20feat.py`
  - 能力：PSSM feature conversion
  - 用途：将 PSSM 转成 20 维特征
  - 复用状态：partial；类型：code_entry
- `input_details/supporting_scripts/esm2_15B_rep_5120.py`
  - 能力：protein LM feature generation
  - 用途：生成 ESM-2 5120 维 representation
  - 复用状态：partial；类型：code_entry
- `input_details/supporting_scripts/batch_save_msa_feat.py`
  - 能力：MSA feature generation
  - 用途：批量保存 MSA first-row 特征
  - 复用状态：partial；类型：code_entry
- `Preprocessing/prepare_pdb_feature.py`
  - 能力：PDB-based feature preparation
  - 用途：从 PDB 构建几何/结构特征
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态分析，未执行仓库代码
- 依赖未安装，无法验证运行时行为
- tests 未运行
- submodules 未初始化
- 可能存在大于 5MiB 的 promisor-only blob
- 路径存在不等于可复现性证据

## 仍未知

- EquiPNAS.py 与 egnn_clean.py 的实际调用关系、入口函数和数据流未从静态路径级证据确认
- Preprocessing/input/ 中样例数据的原始来源、公开数据许可与是否为外部重打包未说明
- 未见独立训练或评估脚本，超参数、指标与阈值未知
- 未见 checkpoint/权重文件，无法判断是否有预训练或已训练模型

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
