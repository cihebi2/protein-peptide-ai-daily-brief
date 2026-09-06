# aim-uofa/FADiff

- **仓库：** [https://github.com/aim-uofa/FADiff](https://github.com/aim-uofa/FADiff)
- **固定 commit：** `0c5bf8edab950ec7cf33b86abcc744849503da68`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** mixed
- **资产记录数：** 17

## 仓库摘要

这是 FADiff 的冻结仓库清单：包含自研 SE(3) diffusion 训练/推理/评估链路（`model/`、`data/`、`experiments/`、`analysis/`），并捆绑了 `openfold/` 与 `ProteinMPNN/` 两个第三方子树及其预训练权重；仓库未见顶层统一 LICENSE，仅在 `ProteinMPNN/` 与 `ProteinMPNN/training/` 下发现独立许可文件，且未发现可验证的独立训练数据集。

## 可复用模块与资源

### checkpoints

- `ProteinMPNN/ca_model_weights/v_48_002.pt`
  - 能力：ProteinMPNN CA-only checkpoint family
  - 用途：CA-only 预训练权重。
  - 复用状态：blocked；类型：model_weight
- `ProteinMPNN/vanilla_model_weights/v_48_002.pt`
  - 能力：ProteinMPNN vanilla checkpoint family
  - 用途：vanilla 预训练权重。
  - 复用状态：blocked；类型：model_weight

### datasets

- `ProteinMPNN/inputs/PDB_complexes/pdbs/3HTN.pdb`
  - 能力：示例复合物输入
  - 用途：示例复合物结构输入，不足以证明训练集。
  - 复用状态：unknown；类型：unknown
- `ProteinMPNN/inputs/PDB_homooligomers/pdbs/4GYT.pdb`
  - 能力：示例同源寡聚体输入
  - 用途：示例 homooligomer 结构。
  - 复用状态：unknown；类型：unknown
- `ProteinMPNN/inputs/PDB_monomers/pdbs/5L33.pdb`
  - 能力：示例单体输入
  - 用途：示例 monomer 结构。
  - 复用状态：unknown；类型：unknown
- `ProteinMPNN/test_samples/output/parsed_pdbs.jsonl`
  - 能力：测试样例输出
  - 用途：测试样例的解析结果、序列与结构输出。
  - 复用状态：blocked；类型：unknown

### evaluation

- `analysis/metrics.py`
  - 能力：评估指标
  - 用途：静态计算结果指标与分析。
  - 复用状态：blocked；类型：code_entry

### inference

- `experiments/inference_se3_diffusion.py`
  - 能力：主推理入口
  - 用途：生成 scaffold/候选结构的推理流程。
  - 复用状态：blocked；类型：code_entry
- `experiments/inference_se3_diffusion_tsp.py`
  - 能力：TSP 推理变体
  - 用途：TSP 变体推理流程。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `model/score_network.py`
  - 能力：核心生成方法 / score network
  - 用途：实现 FADiff 的分数网络与生成主干。
  - 复用状态：blocked；类型：code_entry
- `data/se3_diffuser.py`
  - 能力：SE(3)/R3 扩散算子
  - 用途：处理 SE(3) 与 R^3 噪声、采样和去噪流程。
  - 复用状态：blocked；类型：code_entry
- `data/process_pdb_dataset.py`
  - 能力：PDB 预处理与解析
  - 用途：把 PDB/mmCIF 数据转成训练或推理可用表示。
  - 复用状态：blocked；类型：code_entry
- `openfold/model/model.py`
  - 能力：OpenFold 结构建模子树
  - 用途：提供第三方结构网络与模板/结构模块依赖。
  - 复用状态：blocked；类型：code_entry
- `ProteinMPNN/protein_mpnn_run.py`
  - 能力：ProteinMPNN 推理/训练辅助
  - 用途：提供第三方蛋白序列设计与打分入口。
  - 复用状态：blocked；类型：code_entry

### training

- `experiments/train_se3_diffusion.py`
  - 能力：主训练入口
  - 用途：组装 FADiff 训练流程与参数。
  - 复用状态：blocked；类型：code_entry
- `train.sh`
  - 能力：训练启动脚本
  - 用途：命令行训练启动。
  - 复用状态：blocked；类型：code_entry
- `ProteinMPNN/training/training.py`
  - 能力：ProteinMPNN 训练示例
  - 用途：第三方 ProteinMPNN 子树的训练/微调示例。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、训练或推理。
- 依赖未安装、测试未运行，路径存在不代表可运行。
- `openfold/` 与 `ProteinMPNN/` 为 vendored 子树，具体许可条款未核验。
- 示例 PDB/FA/JSONL 与权重文件的来源和再分发权未核验。

## 仍未知

- `ProteinMPNN/LICENSE` 与 `ProteinMPNN/training/LICENSE` 的具体条款及覆盖范围未核验。
- `ProteinMPNN/inputs` 与 `ProteinMPNN/test_samples` 是否来自公开数据或作者自制样本未核验。
- `pt` checkpoint 是否可再分发、是否与论文训练一致未核验。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
