# rschmirler/data-repo_plm-finetune-eval

- **仓库：** [https://github.com/rschmirler/data-repo_plm-finetune-eval](https://github.com/rschmirler/data-repo_plm-finetune-eval)
- **固定 commit：** `1f1529814077b4613d5f1fa1bb76778337c81263`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** mixed
- **资产记录数：** 24

## 仓库摘要

仓库主要是蛋白 pLM fine-tuning 相关的 notebook、示例数据与结果表，适合做静态复用审查，但未见独立源码、模型权重或可验证 checkpoint。

## 可复用模块与资源

### datasets

- `notebooks/embedding/example_data/GB1_raw/train.pkl`
  - 能力：example_raw_dataset
  - 用途：GB1 示例原始数据；与 valid/test 组成演示数据集
  - 复用状态：partial；类型：unknown
- `notebooks/embedding/example_data/GB1_embedded/train_ESM2_8M.pkl`
  - 能力：example_embedded_dataset
  - 用途：GB1 示例 embedding 数据；对应预计算特征缓存
  - 复用状态：partial；类型：unknown
- `training data.zip`
  - 能力：training_data_archive
  - 用途：训练数据压缩包；未展开，内部样本与许可未确认
  - 复用状态：partial；类型：unknown
- `source_data_main/Table 2_Task specific datasets.xlsx`
  - 能力：dataset_catalog
  - 用途：任务数据集清单与元数据，不是原始数据本体
  - 复用状态：ready_for_review；类型：unknown

### evaluation

- `source_data_main/Figure 1_Fine-tuning improved for most pLMs and tasks.csv`
  - 能力：main_figure_source_data
  - 用途：主文 Figure 1-2 的性能比较与 PEFT 对照源数据
  - 复用状态：ready_for_review；类型：unknown
- `source_data_main/Figure 3a_SecStr_averages.csv`
  - 能力：task_specific_evaluation_source_data
  - 用途：secondary structure 与 disorder 评估源数据
  - 复用状态：ready_for_review；类型：unknown
- `source_data_main/Figure 4_Simple methods limited for mutational effects_averages.csv`
  - 能力：resource_and_mutation_evaluation_source_data
  - 用途：mutational effects 与训练资源开销评估源数据
  - 复用状态：ready_for_review；类型：unknown
- `source_data_SOM/Table S1_Individual training runs - pre-trained embeddings.csv`
  - 能力：supplementary_tables
  - 用途：补充材料中的逐次训练、聚合结果和资源分析表（S1-S17）
  - 复用状态：ready_for_review；类型：unknown

### inference

- `notebooks/embedding/Embedding_Generation_GPU.ipynb`
  - 能力：embedding_generation_inference
  - 用途：protein embedding 生成/推理步骤
  - 复用状态：ready_for_review；类型：unknown

### reusable_assets

- `README.md`
  - 能力：repo_overview
  - 用途：仓库总览、目录索引与复现实验入口说明
  - 复用状态：ready_for_review；类型：unknown
- `notebooks/embedding/README.md`
  - 能力：embedding_docs
  - 用途：embedding 目录说明、输入输出与运行提示
  - 复用状态：ready_for_review；类型：unknown
- `notebooks/finetune/README.md`
  - 能力：finetune_docs
  - 用途：fine-tune 目录说明、运行约束与任务入口
  - 复用状态：ready_for_review；类型：unknown
- `notebooks/embedding/Embedding_Generation_GPU.ipynb`
  - 能力：embedding_generation_method
  - 用途：GPU 上生成 protein embedding 的方法 notebook
  - 复用状态：ready_for_review；类型：unknown
- `notebooks/embedding/Embedding_Predictor_Training.ipynb`
  - 能力：embedding_predictor_training_method
  - 用途：基于 embedding 训练预测器的 notebook
  - 复用状态：ready_for_review；类型：unknown
- `notebooks/finetune/Finetuning_per_protein.ipynb`
  - 能力：protein_finetuning_method
  - 用途：按 protein 级别 fine-tuning 的 notebook
  - 复用状态：ready_for_review；类型：unknown
- `notebooks/finetune/Finetuning_per_residue_classification.ipynb`
  - 能力：residue_classification_finetuning_method
  - 用途：按 residue classification 任务 fine-tuning 的 notebook
  - 复用状态：ready_for_review；类型：unknown
- `notebooks/finetune/Finetuning_per_residue_regression.ipynb`
  - 能力：residue_regression_finetuning_method
  - 用途：按 residue regression 任务 fine-tuning 的 notebook
  - 复用状态：ready_for_review；类型：unknown
- `notebooks/finetune/finetune.yml`
  - 能力：training_config_recipe
  - 用途：fine-tuning 超参数与运行配置
  - 复用状态：ready_for_review；类型：config

### training

- `notebooks/embedding/Embedding_Predictor_Training.ipynb`
  - 能力：embedding_predictor_training
  - 用途：embedding-based predictor 训练流程
  - 复用状态：ready_for_review；类型：unknown
- `notebooks/finetune/Finetuning_per_protein.ipynb`
  - 能力：protein_finetuning
  - 用途：protein 级 fine-tuning 训练流程
  - 复用状态：ready_for_review；类型：unknown
- `notebooks/finetune/Finetuning_per_residue_classification.ipynb`
  - 能力：residue_classification_finetuning
  - 用途：residue classification 训练流程
  - 复用状态：ready_for_review；类型：unknown
- `notebooks/finetune/Finetuning_per_residue_regression.ipynb`
  - 能力：residue_regression_finetuning
  - 用途：residue regression 训练流程
  - 复用状态：ready_for_review；类型：unknown
- `notebooks/finetune/finetune.yml`
  - 能力：training_configuration
  - 用途：训练超参数、批量大小与实验配置
  - 复用状态：ready_for_review；类型：config
- `training_logs.zip`
  - 能力：training_logs_archive
  - 用途：训练日志与运行记录归档；仅从文件名推断用途
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态盘点，未执行 notebook、未安装依赖，也未验证 zip/pkl/xlsx 的内部内容。
- 未发现独立模型权重或 checkpoint 文件；training_logs.zip 只能按文件名推断为日志归档。
- source_data_* 多为结果表/图表源数据，不能仅凭文件名区分原始数据与派生结果。
- 示例 GB1 数据与 training data.zip 的外部来源和授权未在静态层面确认。

## 仍未知

- training data.zip 与 training_logs.zip 的内部文件结构。
- GB1_raw / GB1_embedded 是否为外部基准数据还是项目重打包数据。
- LICENSE.txt 与 MIT-LICENSE.txt 分别约束哪些子目录与资产。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
