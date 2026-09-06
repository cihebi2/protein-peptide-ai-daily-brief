# AnacletoLAB/miRInter-Trans

- **仓库：** [https://github.com/AnacletoLAB/miRInter-Trans](https://github.com/AnacletoLAB/miRInter-Trans)
- **固定 commit：** `ebe453bfee375fbffa4828f8904954d2d37e4a33`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 18

## 仓库摘要

该仓库是 MiRInter-Trans 的静态代码与数据发布，包含 RNA-FM/transformer 相关建模、Notebook 驱动训练、推理与若干评估产物；未见可执行训练入口或已发布模型权重，复用时需分离代码、数据与第三方子树许可边界。

## 可复用模块与资源

### checkpoints

- `RNA-FM/redevelop/model/weights_load.py`
  - 能力：checkpoint_io
  - 用途：模型 state_dict 加载接口；冻结清单未见实际 .pth/.pt/.ckpt 文件。
  - 复用状态：partial；类型：code_entry
- `RNA-FM/redevelop/model/weights_init.py`
  - 能力：checkpoint_io
  - 用途：权重初始化接口；属于 checkpoint 相关支持代码而非已保存权重。
  - 复用状态：partial；类型：code_entry
- `RNA-FM/redevelop/utils/checkpoint.py`
  - 能力：checkpoint_io
  - 用途：checkpoint 保存/恢复封装。
  - 复用状态：partial；类型：code_entry
- `RNA-FM/fm/pretrained.py`
  - 能力：pretrained_weight_access
  - 用途：上游 RNA-FM 预训练权重的加载入口。
  - 复用状态：partial；类型：code_entry

### datasets

- `RNA-FM/redevelop/data/data_SPL/lncRNA_miRNA_interactions_with_folds.csv`
  - 能力：supervised_interaction_data
  - 用途：SPL 任务的 lncRNA-miRNA interactions with folds、序列表与 FASTA，适合监督训练与划分复现。
  - 复用状态：partial；类型：unknown
- `RNA-FM/redevelop/data/data_mirinter/RNA_sequences_uniq_mirna_lncrna.fasta`
  - 能力：sequence_universe_data
  - 用途：miRNA-lncRNA、miRNA-miRNA、miRNA-snoRNA 的去重 FASTA，适合跨任务或 denovo 候选对构造。
  - 复用状态：partial；类型：unknown
- `RNA-FM/redevelop/results/data_SPL/de_novo_lncRNA_miRNA_interactions_unique_fold.csv`
  - 能力：derived_dataset_cache
  - 用途：派生的 fold/字典/序列缓存，偏向中间结果与复用数据而非原始语料。
  - 复用状态：partial；类型：unknown

### evaluation

- `RNA-FM/redevelop/utils/painter/draw_roc.py`
  - 能力：metric_visualization
  - 用途：ROC 与 confusion matrix 绘图。
  - 复用状态：partial；类型：code_entry
- `data_SPL/results_staff/cv_training_results_UNIQUE_SPL.pkl`
  - 能力：stored_cv_results
  - 用途：交叉验证结果、平均结果与图包；更接近评估产物而非可执行评估程序。
  - 复用状态：partial；类型：unknown

### inference

- `RNA-FM/redevelop/engine/predictor.py`
  - 能力：batch_prediction_engine
  - 用途：批量推理、得分汇总与预测逻辑封装。
  - 复用状态：partial；类型：code_entry
- `RNA-FM/redevelop/launch/predict.py`
  - 能力：command_line_prediction
  - 用途：命令式推理入口与参数调度。
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `RNA-FM/redevelop/model/backbones.py`
  - 能力：model_architecture
  - 用途：miRNA 交互预测主干与 pairwise predictor 组合；包含 backbones、baseline、downstream_module 及多种成对融合头。
  - 复用状态：partial；类型：code_entry
- `RNA-FM/fm/model.py`
  - 能力：model_architecture
  - 用途：上游 RNA-FM 编码器与 Transformer 表示模块；更像第三方基础模型实现，而非本仓库特有贡献。
  - 复用状态：partial；类型：code_entry
- `RNA-FM/redevelop/data/batch_converter.py`
  - 能力：data_pipeline
  - 用途：序列读取、batch 组装、collate 与分类变换；支撑训练/推理前的数据装配。
  - 复用状态：partial；类型：code_entry
- `RNA-FM/redevelop/config/defaults.py`
  - 能力：config_recipe
  - 用途：默认实验/推理配置。
  - 复用状态：partial；类型：code_entry
- `RNA-FM/redevelop/launch/predict.py`
  - 能力：inference
  - 用途：命令式推理入口。
  - 复用状态：partial；类型：code_entry

### training

- `data_SPL/notebooks_training/training_from_folds_cv_SPL_train_test_aug_negatives_ALL.ipynb`
  - 能力：notebook_training
  - 用途：SPL 交叉验证、one-shot、aug/noaug、unique/reduced/positives-only/negatives-only 训练 Notebook 族。
  - 复用状态：partial；类型：unknown
- `data_mirrna_all/notebooks/training_from_folds_cv_mirna-lncrna-CROSSTRUE.ipynb`
  - 能力：notebook_training
  - 用途：miRNA-lncRNA、miRNA-miRNA、miRNA-snoRNA 的 CROSSTRUE 训练 Notebook。
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态审查，未执行仓库代码、未安装依赖、未运行测试。
- 冻结清单中没有可验证的 training_entrypoint；训练主要由 Notebook 承担。
- 未见明确的模型权重文件（.pth/.pt/.ckpt）；仅见加载/初始化工具与若干 p/pkl 缓存。
- 数据与序列缓存的来源、授权和可再分发性无法仅凭路径确认。
- RNA-FM/ 子树可视为 vendored 边界，不能直接当作本仓库的论文特有贡献。

## 仍未知

- data_SPL/results_staff/*.pkl 与 data_mirrna_all/*_dict_RNAFM.p 更像中间结果/特征缓存，无法仅凭路径确认是否等同于模型 checkpoint。
- Notebook 内的超参数、负样本构造、划分细节和具体评估指标未读入内容，不能做执行级复现判断。
- RNA-FM/LICENSE 与根 LICENSE 是否完全一致、以及第三方 JAR 的再分发条件均未核实。
- 仓库可能存在未展开的大文件或 promisor 对象，静态清单不能证明其完整可得。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
