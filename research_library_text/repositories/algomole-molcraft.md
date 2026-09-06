# AlgoMole/MolCRAFT

- **仓库：** [https://github.com/AlgoMole/MolCRAFT](https://github.com/AlgoMole/MolCRAFT)
- **固定 commit：** `743dfb5198c44ca0cec180822bd54258f9d386f1`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** mixed
- **资产记录数：** 23

## 仓库摘要

该仓库是一个多子项目的结构基础分子设计套件，覆盖生成、引导优化、扩散采样、属性预测与对接评估；冻结库存仅见示例数据与占位目录，未发现可验证权重。

## 可复用模块与资源

### checkpoints

- `MolPilot/targetdiff/pretrained_models/.gitignore`
  - 能力：Pretrained checkpoint placeholder
  - 用途：仅用于忽略权重目录；未发现 tracked 的 `.pt`、`.ckpt` 或 `.pth` 权重文件。
  - 复用状态：blocked；类型：unknown

### datasets

- `MolPilot/core/examples/1h36_A_rec_1h36_r88_lig_tt_docked_0.sdf`
  - 能力：Demo complex 1h36
  - 用途：示例受体-配体复合物，供采样、对接与可视化 smoke test。
  - 复用状态：partial；类型：unknown
- `MolPilot/core/examples/3ug2_ligand.sdf`
  - 能力：Demo complex 3ug2
  - 用途：示例受体-配体复合物，供采样、对接与可视化 smoke test。
  - 复用状态：partial；类型：unknown

### evaluation

- `MolCRAFT/core/evaluation/metrics.py`
  - 能力：MolCRAFT metric stack
  - 用途：原子类型、键长/键角/扭转角、分布与综合指标。
  - 复用状态：ready_for_review；类型：code_entry
- `MolCRAFT/core/evaluation/docking_vina.py`
  - 能力：Docking / RMSD benchmark utilities
  - 用途：对接打分与构象/RMSD 评估。
  - 复用状态：ready_for_review；类型：code_entry
- `MolJO/test/pearson_r.ipynb`
  - 能力：Posthoc analysis notebooks
  - 用途：相关性、radar、R-group 与轨迹可视化分析。
  - 复用状态：ready_for_review；类型：unknown
- `MolPilot/eval/validate.py`
  - 能力：Evaluation orchestration
  - 用途：批量验证、统计、更新与绘图式结果汇总。
  - 复用状态：ready_for_review；类型：code_entry
- `MolPilot/targetdiff/scripts/evaluate_diffusion.py`
  - 能力：TargetDiff diffusion evaluation
  - 用途：扩散生成评估与对照分析。
  - 复用状态：ready_for_review；类型：code_entry
- `MolPilot/targetdiff/scripts/property_prediction/eval_prop.py`
  - 能力：TargetDiff property evaluation
  - 用途：属性预测评估。
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `MolCRAFT/sample_for_pocket.py`
  - 能力：MolCRAFT pocket-conditioned sampling
  - 用途：按 pocket 条件生成/采样。
  - 复用状态：ready_for_review；类型：code_entry
- `MolJO/sample_guided.py`
  - 能力：MolJO guided sampling
  - 用途：引导式采样。
  - 复用状态：ready_for_review；类型：code_entry
- `MolPilot/sample_for_pocket.py`
  - 能力：MolPilot pocket-conditioned sampling
  - 用途：口袋条件采样。
  - 复用状态：ready_for_review；类型：code_entry
- `MolPilot/targetdiff/scripts/sample_diffusion.py`
  - 能力：TargetDiff diffusion sampling
  - 用途：扩散式生成采样；还有 surface 版本。
  - 复用状态：ready_for_review；类型：code_entry
- `MolPilot/targetdiff/scripts/property_prediction/inference.py`
  - 能力：TargetDiff property inference
  - 用途：属性预测推理。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `MolCRAFT/core/models/bfn4sbdd.py`
  - 能力：MolCRAFT BFN-based SBDD generator
  - 用途：结构基础分子生成/优化主模型；配套训练入口与训练循环已在仓库内跟踪。
  - 复用状态：ready_for_review；类型：code_entry
- `MolJO/core/models/bfn4sbdd.py`
  - 能力：MolJO guided optimization / classifier-guided generation
  - 用途：引导式优化与口袋条件采样；配套分类器训练和采样脚本都已跟踪。
  - 复用状态：ready_for_review；类型：code_entry
- `MolPilot/core/models/sbdd4train_timewarp.py`
  - 能力：MolPilot time-warped SBDD generator
  - 用途：time-warp 变体的 SBDD 训练/生成管线。
  - 复用状态：ready_for_review；类型：code_entry
- `MolPilot/targetdiff/models/molopt_score_model.py`
  - 能力：TargetDiff diffusion / property-prediction family
  - 用途：扩散生成、score modeling 与属性预测；对应训练入口已跟踪。
  - 复用状态：ready_for_review；类型：code_entry
- `MolPilot/core/evaluation/utils/sascorer.py`
  - 能力：SA score / similarity evaluation utilities
  - 用途：synthetic accessibility 与相似性/打分辅助；属于评估侧可复用辅助资源。
  - 复用状态：partial；类型：code_entry

### training

- `MolCRAFT/train_bfn.py`
  - 能力：BFN SBDD training
  - 用途：主 SBDD 训练入口。
  - 复用状态：ready_for_review；类型：code_entry
- `MolJO/train_classifier.py`
  - 能力：Guided/classifier training
  - 用途：引导式优化所需分类器训练。
  - 复用状态：ready_for_review；类型：code_entry
- `MolPilot/train_bfn_twisted.py`
  - 能力：Twisted/time-warp SBDD training
  - 用途：MolPilot 变体 BFN 训练。
  - 复用状态：ready_for_review；类型：code_entry
- `MolPilot/targetdiff/scripts/train_diffusion.py`
  - 能力：Diffusion and property-prediction training
  - 用途：扩散生成训练；属性预测训练入口另有 `scripts/property_prediction/train_prop.py`。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态盘点；未执行代码、测试或训练。
- 依赖未安装，无法验证运行时行为、导入链与版本兼容性。
- 未初始化子模块，且 large blobs 可能仅为占位或 promisor。
- 路径存在不等于可复现；没有权重文件也不能推出已完成训练。

## 仍未知

- 示例 SDF/PDB 的上游来源、数据许可与是否来自外部基准集无法从静态库存确认。
- `MolPilot/targetdiff/LICIENCE` 文件名拼写异常，许可边界需要人工复核。
- `fpscores.pkl.gz` 等第三方辅助文件的上游许可未被解析。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
