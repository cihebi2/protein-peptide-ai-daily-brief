# sekijima-lab/diffint

- **仓库：** [https://github.com/sekijima-lab/diffint](https://github.com/sekijima-lab/diffint)
- **固定 commit：** `1678c4d121e5b9a500d3d837db0885684e896d99`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 17

## 仓库摘要

该仓库是 DiffInt 的核心实现，覆盖条件扩散配体生成、训练、推理、对接/指标评估和示例输入输出；静态审查仅确认源码为 MIT，数据与 checkpoint 的独立许可未验证。

## 可复用模块与资源

### checkpoints

- `checkpoints/best_model.ckpt`
  - 能力：best_model_checkpoint
  - 用途：预训练/训练后权重，用于生成推理。
  - 复用状态：partial；类型：model_weight

### datasets

- `example/1a2g_A_rec.pdb`
  - 能力：demo_receptor_structure
  - 用途：示例口袋/受体结构输入。
  - 复用状态：partial；类型：unknown
- `example/1a2g_A_rec.sdf`
  - 能力：demo_structure_pair
  - 用途：与示例 PDB 配套的结构文件，供演示生成流程使用。
  - 复用状态：partial；类型：unknown

### evaluation

- `analysis/metrics.py`
  - 能力：metrics
  - 用途：生成结果指标汇总。
  - 复用状态：partial；类型：code_entry
- `analysis/docking.py`
  - 能力：docking_evaluation
  - 用途：对接评分/筛选评估；GPU 与 Py2.7 变体位于同目录。
  - 复用状态：partial；类型：code_entry
- `test_single.py`
  - 能力：smoke_test_single
  - 用途：单样本测试/回归检查。
  - 复用状态：partial；类型：code_entry
- `test_npz.py`
  - 能力：smoke_test_npz
  - 用途：NPZ 批量测试/回归检查。
  - 复用状态：partial；类型：code_entry

### inference

- `generate_ligands.py`
  - 能力：ligand_generation_entrypoint
  - 用途：按口袋条件采样并生成候选配体。
  - 复用状态：partial；类型：code_entry
- `example/DiffInt_generated_molecules.tar.gz`
  - 能力：sample_output_bundle
  - 用途：示例推理输出包，展示生成结果的导出格式。
  - 复用状态：partial；类型：unknown

### reusable_assets

- `equivariant_diffusion/en_diffusion.py`
  - 能力：model_architecture
  - 用途：条件扩散生成主干；与 conditional_model.py、dynamics.py、egnn_new.py 配合实现结构条件配体生成。
  - 复用状态：partial；类型：code_entry
- `dataset.py`
  - 能力：data_pipeline
  - 用途：训练/推理样本读取与批处理入口。
  - 复用状态：partial；类型：code_entry
- `hbond_double.py`
  - 能力：interaction_guidance
  - 用途：显式 hydrogen bond 交互约束/特征辅助。
  - 复用状态：partial；类型：code_entry
- `environment.yml`
  - 能力：environment_recipe
  - 用途：依赖环境声明，便于重建训练/推理运行时。
  - 复用状态：partial；类型：config
- `analysis/SA_Score/sascorer.py`
  - 能力：vendored_sa_score
  - 用途：SA score 计算器；同目录 fpscores.pkl.gz 提供碎片分数表。
  - 复用状态：partial；类型：code_entry

### training

- `train.py`
  - 能力：training_entrypoint
  - 用途：训练主入口，连接数据管线、模型和优化流程。
  - 复用状态：partial；类型：code_entry
- `configs/DiffInt_ca_double.yml`
  - 能力：training_config
  - 用途：DiffInt_ca_double 训练超参/模型配置。
  - 复用状态：partial；类型：config
- `lightning_modules.py`
  - 能力：training_module
  - 用途：PyTorch Lightning 训练封装。
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态审查，未执行训练、推理或测试。
- 依赖未安装，无法验证环境兼容性与运行结果。
- checkpoint 仅见文件，不确认权重来源、训练数据或可再分发许可。
- 示例数据和生成样例未见独立许可证。

## 仍未知

- 训练数据集的完整来源与规模未从冻结库存中确认。
- vendored 的 SA_Score 资源原始许可未逐文件核对。
- best_model.ckpt 与 README/配置的精确对应关系未运行验证。
- 对接/评估脚本是否在实际论文实验中全程使用，静态库存无法证明。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
