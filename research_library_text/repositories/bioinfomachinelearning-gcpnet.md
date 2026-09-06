# BioinfoMachineLearning/GCPNet

- **仓库：** [https://github.com/BioinfoMachineLearning/GCPNet](https://github.com/BioinfoMachineLearning/GCPNet)
- **固定 commit：** `172733b6898ed58359a1eab3fb9c36967e328a43`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 47

## 仓库摘要

该冻结仓库是 GCPNet 的静态代码与资产包，覆盖 AR/CPD/EQ/LBA/NMS/PSR/RS 等任务的模型、数据模块、训练/推理/评测入口、示例数据和预训练权重；代码许可为 MIT，但数据与 checkpoint 未见独立许可，且未执行任何代码或测试，因此仅能做静态可复用性盘点，不能证明复现。

## 可复用模块与资源

### checkpoints

- `checkpoints/CPD/model_epoch_735_shortppl_8_22_singlechainppl_8_60_allppl_6_06_shortrecov_33_33_singlechainrecov_32_86_allrecov_40_32.ckpt`
  - 能力：cpd_pretrained_checkpoint
  - 用途：CPD 任务的预训练权重。
  - 复用状态：unknown；类型：model_weight
- `checkpoints/EQ/model_1_epoch_53_per_res_pearson_0_7443.ckpt`
  - 能力：eq_pretrained_checkpoint_1
  - 用途：EQ 任务 checkpoint 1。
  - 复用状态：unknown；类型：model_weight
- `checkpoints/EQ/model_2_epoch_25_per_res_pearson_0_7426.ckpt`
  - 能力：eq_pretrained_checkpoint_2
  - 用途：EQ 任务 checkpoint 2。
  - 复用状态：unknown；类型：model_weight
- `checkpoints/EQ/model_3_epoch_14_per_res_pearson_0_7133.ckpt`
  - 能力：eq_pretrained_checkpoint_3
  - 用途：EQ 任务 checkpoint 3。
  - 复用状态：unknown；类型：model_weight
- `checkpoints/LBA/model_1_epoch_205_rmse_1_352_pearson_0_612_spearman_0_609.ckpt`
  - 能力：lba_pretrained_checkpoint_1
  - 用途：LBA 任务 checkpoint 1。
  - 复用状态：unknown；类型：model_weight
- `checkpoints/LBA/model_2_epoch_188_rmse_1_349_pearson_0_607_spearman_0_613.ckpt`
  - 能力：lba_pretrained_checkpoint_2
  - 用途：LBA 任务 checkpoint 2。
  - 复用状态：unknown；类型：model_weight
- `checkpoints/LBA/model_3_epoch_186_rmse_1_355_pearson_0_604_spearman_0_598.ckpt`
  - 能力：lba_pretrained_checkpoint_3
  - 用途：LBA 任务 checkpoint 3。
  - 复用状态：unknown；类型：model_weight
- `checkpoints/NMS/NMS_Dynamic/model_epoch_9825_mse_0_0173.ckpt`
  - 能力：nms_pretrained_checkpoint_dynamic
  - 用途：NMS Dynamic 权重。
  - 复用状态：unknown；类型：model_weight
- `checkpoints/NMS/NMS_Small/model_epoch_9977_mse_0_0070.ckpt`
  - 能力：nms_pretrained_checkpoint_small
  - 用途：NMS Small 权重。
  - 复用状态：unknown；类型：model_weight
- `checkpoints/NMS/NMS_Small_20Body/model_epoch_10087_mse_0_0071.ckpt`
  - 能力：nms_pretrained_checkpoint_small_20body
  - 用途：NMS Small 20Body 权重。
  - 复用状态：unknown；类型：model_weight
- `checkpoints/NMS/NMS_Static/model_epoch_5159_mse_0_0073.ckpt`
  - 能力：nms_pretrained_checkpoint_static
  - 用途：NMS Static 权重。
  - 复用状态：unknown；类型：model_weight
- `checkpoints/PSR/model_epoch_115_localpearson_0_616_localspearman_0_532_localkendall_0_385_globalpearson_0_871_globalspearman_0_869_globalkendall_0_676.ckpt`
  - 能力：psr_pretrained_checkpoint
  - 用途：PSR 任务权重。
  - 复用状态：unknown；类型：model_weight
- `checkpoints/RS/model_1_epoch_54_accuracy_0_9873.ckpt`
  - 能力：rs_pretrained_checkpoint_1
  - 用途：RS 任务 checkpoint 1。
  - 复用状态：unknown；类型：model_weight
- `checkpoints/RS/model_2_epoch_98_accuracy_0_9882.ckpt`
  - 能力：rs_pretrained_checkpoint_2
  - 用途：RS 任务 checkpoint 2。
  - 复用状态：unknown；类型：model_weight
- `checkpoints/RS/model_3_epoch_70_accuracy_0_9868.ckpt`
  - 能力：rs_pretrained_checkpoint_3
  - 用途：RS 任务 checkpoint 3。
  - 复用状态：unknown；类型：model_weight

### datasets

- `data/AR/examples/decoy_model/2CZOA.pdb`
  - 能力：ar_example_decoy_structure
  - 用途：AR 示例中的 decoy 输入结构。
  - 复用状态：unknown；类型：unknown
- `data/AR/examples/true_model/2CZOA.pdb`
  - 能力：ar_example_reference_structure
  - 用途：AR 示例中的 reference/true 模型。
  - 复用状态：unknown；类型：unknown
- `data/AR/splits/test_ar.lst`
  - 能力：ar_split_manifest
  - 用途：AR 测试集 split 列表；同目录还存在 train1-10 与 valid1-10 等划分文件。
  - 复用状态：unknown；类型：unknown
- `data/EQ/examples/decoy_model/6W6VE.pdb`
  - 能力：eq_example_decoy_structure
  - 用途：EQ 示例中的 decoy 输入结构。
  - 复用状态：unknown；类型：unknown
- `data/EQ/examples/true_model/6W6VE.pdb`
  - 能力：eq_example_reference_structure
  - 用途：EQ 示例中的 true 模型。
  - 复用状态：unknown；类型：unknown
- `data/EQ/examples/decoy_model/6W77K.pdb`
  - 能力：eq_example_decoy_structure_second_case
  - 用途：EQ 第二个示例中的 decoy 输入结构。
  - 复用状态：unknown；类型：unknown
- `data/EQ/examples/true_model/6W77K.pdb`
  - 能力：eq_example_reference_structure_second_case
  - 用途：EQ 第二个示例中的 true 模型。
  - 复用状态：unknown；类型：unknown
- `data/EQ/splits/train.lst`
  - 能力：eq_split_manifest
  - 用途：EQ 训练集 split 列表；同目录还有 valid.lst 与 test.lst。
  - 复用状态：unknown；类型：unknown

### evaluation

- `src/eval.py`
  - 能力：evaluation_entrypoint
  - 用途：统一评测入口，汇总模型在不同数据集上的指标。
  - 复用状态：ready_for_review；类型：code_entry
- `configs/eval.yaml`
  - 能力：evaluation_config
  - 用途：评测流程的 Hydra 配置入口。
  - 复用状态：ready_for_review；类型：config
- `tests/test_eval.py`
  - 能力：evaluation_test
  - 用途：对评测逻辑的静态测试覆盖。
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `src/predict.py`
  - 能力：prediction_entrypoint
  - 用途：统一的预测入口，可加载训练好的 checkpoint 对新结构执行推理。
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/generate_ar_grid_search_runs.py`
  - 能力：ar_grid_search_run_generator
  - 用途：为 AR 批量生成 grid search 运行参数。
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/generate_cpd_grid_search_runs.py`
  - 能力：cpd_grid_search_run_generator
  - 用途：为 CPD 批量生成 grid search 运行参数。
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/generate_eq_grid_search_runs.py`
  - 能力：eq_grid_search_run_generator
  - 用途：为 EQ 批量生成 grid search 运行参数。
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/generate_lba_grid_search_runs.py`
  - 能力：lba_grid_search_run_generator
  - 用途：为 LBA 批量生成 grid search 运行参数。
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/generate_nms_grid_search_runs.py`
  - 能力：nms_grid_search_run_generator
  - 用途：为 NMS 批量生成 grid search 运行参数。
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/generate_psr_grid_search_runs.py`
  - 能力：psr_grid_search_run_generator
  - 用途：为 PSR 批量生成 grid search 运行参数。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/models/components/gcpnet.py`
  - 能力：core_gcpnet_model
  - 用途：实现 GCPNet 主干与几何感知消息传递/交互逻辑，是各任务模块共享的核心网络组件。
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/gcpnet_ar_module.py`
  - 能力：ar_task_module
  - 用途：封装 AR 任务的前向、损失与指标组织逻辑。
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/gcpnet_cpd_module.py`
  - 能力：cpd_task_module
  - 用途：封装 CPD 任务的训练/验证/推理接口。
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/gcpnet_eq_module.py`
  - 能力：eq_task_module
  - 用途：封装 EQ 任务的结构预测/回归式评测逻辑。
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/gcpnet_lba_module.py`
  - 能力：lba_task_module
  - 用途：封装 LBA 任务的 binding affinity 预测流程。
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/gcpnet_nms_module.py`
  - 能力：nms_task_module
  - 用途：封装 NMS 任务的预测与评测逻辑。
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/gcpnet_psr_module.py`
  - 能力：psr_task_module
  - 用途：封装 PSR 任务的局部/全局 score 预测与指标计算。
  - 复用状态：ready_for_review；类型：code_entry
- `src/models/gcpnet_rs_module.py`
  - 能力：rs_task_module
  - 用途：封装 RS 任务的分类式预测与精度评估。
  - 复用状态：ready_for_review；类型：code_entry
- `src/datamodules/components/protein_graph_dataset.py`
  - 能力：protein_graph_dataset_support
  - 用途：提供蛋白图数据封装与样本读取支持，可被多个任务的数据模块复用。
  - 复用状态：ready_for_review；类型：code_entry

### training

- `src/train.py`
  - 能力：training_entrypoint
  - 用途：Hydra/Lightning 风格的训练入口，负责组装模型、数据模块、回调与 trainer。
  - 复用状态：ready_for_review；类型：code_entry
- `configs/train.yaml`
  - 能力：training_recipe
  - 用途：训练总配置入口，汇总数据、模型、日志与运行参数。
  - 复用状态：ready_for_review；类型：config
- `configs/trainer/default.yaml`
  - 能力：trainer_defaults
  - 用途：定义 trainer 默认设置，可与 cpu/gpu/ddp/mps 配置组合。
  - 复用状态：ready_for_review；类型：config
- `configs/callbacks/model_checkpoint.yaml`
  - 能力：checkpoint_callback
  - 用途：训练时的 checkpoint 保存策略。
  - 复用状态：ready_for_review；类型：config
- `configs/callbacks/early_stopping.yaml`
  - 能力：early_stopping_callback
  - 用途：训练早停策略配置。
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做静态盘点，未执行代码、未安装依赖、未运行测试。
- 仓库中存在数据与权重，但其单独授权与分发边界未被静态证明。
- `configs/datamodule/atom3d_lba.yaml`、`configs/datamodule/atom3d_psr.yaml`、`configs/datamodule/cath_cpd.yaml`、`configs/datamodule/rs.yaml` 指向外部数据源；原始语料未随本冻结件一并验证。

## 仍未知

- `src/utils/amber/*` 的第三方来源/改写历史未由静态清单证实。
- 各 checkpoint 的训练数据、导出脚本和最终评测链路未执行验证。
- NMS 的合成数据生成链路存在 `src/datamodules/components/nms/generate_dataset.py` 与 `synthetic_sim.py`，但未运行，无法确认生成内容与 checkpoint 的对应关系。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
