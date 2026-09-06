# BioSystemsUM/DeepMol

- **仓库：** [https://github.com/BioSystemsUM/DeepMol](https://github.com/BioSystemsUM/DeepMol)
- **固定 commit：** `6aeeb4047e15219c981b56f217167dc04abb8ca8`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** BSD-3-Clause
- **资产记录数：** 41

## 仓库摘要

DeepMol 是一个面向化学信息学的 Python 框架；静态清单显示其包含分子标准化、featurization、tokenizer、模型封装、pipeline、优化与评估模块，并附带测试数据与 3 个 `.pt` 权重，但未见可验证的训练入口或运行结果，数据/权重的独立许可与来源仍不明确。

## 可复用模块与资源

### checkpoints

- `src/deepmol/compound_featurization/neural_npfp/ae_cv0.pt`
  - 能力：特征生成权重
  - 用途：神经 fingerprint 的 autoencoder 权重
  - 复用状态：blocked；类型：model_weight
- `src/deepmol/compound_featurization/neural_npfp/aux_cv0.pt`
  - 能力：特征生成权重
  - 用途：神经 fingerprint 的辅助权重
  - 复用状态：blocked；类型：model_weight
- `src/deepmol/compound_featurization/neural_npfp/baseline_cv0.pt`
  - 能力：基线权重
  - 用途：baseline 模型权重
  - 复用状态：blocked；类型：model_weight

### datasets

- `tests/data/A2780.sdf`
  - 能力：测试夹具数据
  - 用途：3D 分子测试样例
  - 复用状态：blocked；类型：unknown
- `tests/data/PC-3.csv`
  - 能力：测试夹具数据
  - 用途：细胞系相关 CSV 样例
  - 复用状态：blocked；类型：unknown
- `tests/data/balanced_mini_dataset.csv`
  - 能力：测试夹具数据
  - 用途：小型平衡分类样例
  - 复用状态：blocked；类型：unknown
- `tests/data/dataset_last_version2.csv`
  - 能力：测试夹具数据
  - 用途：CSV 处理样例
  - 复用状态：blocked；类型：unknown
- `tests/data/dataset_sweet_3D_to_test.sdf`
  - 能力：测试夹具数据
  - 用途：3D SDF 测试样例
  - 复用状态：blocked；类型：unknown
- `tests/data/dataset_sweet_3d_balanced.sdf`
  - 能力：测试夹具数据
  - 用途：3D 平衡 SDF 样例
  - 复用状态：blocked；类型：unknown
- `tests/data/datset_wFooDB.csv`
  - 能力：测试夹具数据
  - 用途：FooDB 相关 CSV 样例
  - 复用状态：blocked；类型：unknown
- `tests/data/invalid_smiles_dataset.csv`
  - 能力：测试夹具数据
  - 用途：无效 SMILES 检测样例
  - 复用状态：blocked；类型：unknown
- `tests/data/multilabel_classification_dataset.csv`
  - 能力：测试夹具数据
  - 用途：多标签分类样例
  - 复用状态：blocked；类型：unknown
- `tests/data/np_dataset_small_sample.csv`
  - 能力：测试夹具数据
  - 用途：NP 相关小样本 CSV
  - 复用状态：blocked；类型：unknown
- `tests/data/preprocessed_dataset.csv`
  - 能力：测试夹具数据
  - 用途：预处理后样例数据
  - 复用状态：blocked；类型：unknown
- `tests/data/preprocessed_dataset_wfoodb.csv`
  - 能力：测试夹具数据
  - 用途：含 FooDB 的预处理样例
  - 复用状态：blocked；类型：unknown
- `tests/data/results_test.sdf`
  - 能力：测试夹具数据
  - 用途：结果导出验证样例
  - 复用状态：blocked；类型：unknown
- `tests/data/small_train_dataset.csv`
  - 能力：测试夹具数据
  - 用途：小型训练样例
  - 复用状态：blocked；类型：unknown
- `tests/data/test.sdf`
  - 能力：测试夹具数据
  - 用途：基础 SDF 样例
  - 复用状态：blocked；类型：unknown
- `tests/data/test_to_convert_to_sdf.csv`
  - 能力：测试夹具数据
  - 用途：CSV 转 SDF 样例
  - 复用状态：blocked；类型：unknown
- `tests/data/tox21.csv`
  - 能力：测试夹具数据
  - 用途：Tox21 样例数据
  - 复用状态：blocked；类型：unknown
- `tests/data/tox21_small.csv`
  - 能力：测试夹具数据
  - 用途：Tox21 小样本
  - 复用状态：blocked；类型：unknown
- `tests/data/tox21_small_.csv`
  - 能力：测试夹具数据
  - 用途：Tox21 变体样例
  - 复用状态：blocked；类型：unknown
- `tests/data/train_dataset.csv`
  - 能力：测试夹具数据
  - 用途：训练样例数据
  - 复用状态：blocked；类型：unknown
- `src/deepmol/compound_featurization/nc_mfp/databases/All_Optimized_Scaffold_List.txt`
  - 能力：NC-MFP 资源库
  - 用途：支架列表资源
  - 复用状态：blocked；类型：unknown
- `src/deepmol/compound_featurization/nc_mfp/databases/ncdb/final_label.pickle`
  - 能力：NC-MFP 资源库
  - 用途：标签映射资源
  - 复用状态：blocked；类型：unknown
- `src/deepmol/compound_featurization/nc_mfp/databases/ncdb/fragment_dic.pickle`
  - 能力：NC-MFP 资源库
  - 用途：片段字典资源
  - 复用状态：blocked；类型：unknown

### evaluation

- `src/deepmol/metrics/metrics.py`
  - 能力：指标计算
  - 用途：统一封装回归/分类评估指标
  - 复用状态：ready_for_review；类型：code_entry
- `src/deepmol/metrics/metrics_functions.py`
  - 能力：指标函数实现
  - 用途：底层 metric 计算函数
  - 复用状态：ready_for_review；类型：code_entry
- `src/deepmol/evaluator/evaluator.py`
  - 能力：评估器
  - 用途：封装模型评估与结果汇总
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `src/deepmol/compound_featurization/nc_mfp/generate_database.py`
  - 能力：NC-MFP 数据库生成
  - 用途：批量生成推理/检索所需的特征数据库
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `src/deepmol/compound_featurization/rdkit_descriptors.py`
  - 能力：分子描述符生成
  - 用途：为 QSAR/QSPR 类任务提供手工特征
  - 复用状态：ready_for_review；类型：code_entry
- `src/deepmol/compound_featurization/rdkit_fingerprints.py`
  - 能力：分子指纹生成
  - 用途：生成常见分子 fingerprint 特征
  - 复用状态：ready_for_review；类型：code_entry
- `src/deepmol/tokenizers/atom_level_smiles_tokenizer.py`
  - 能力：SMILES/原子级分词
  - 用途：为序列模型构造输入 token
  - 复用状态：ready_for_review；类型：tokenizer
- `src/deepmol/standardizer/molecular_standardizer.py`
  - 能力：分子标准化
  - 用途：对分子做标准化与清洗
  - 复用状态：ready_for_review；类型：code_entry
- `src/deepmol/datasets/datasets.py`
  - 能力：数据集封装
  - 用途：统一加载与包装化学数据集
  - 复用状态：ready_for_review；类型：code_entry
- `src/deepmol/models/models.py`
  - 能力：模型抽象层
  - 用途：封装 sklearn/Keras/DeepChem 风格模型接口
  - 复用状态：ready_for_review；类型：code_entry
- `src/deepmol/pipeline/pipeline.py`
  - 能力：pipeline 组合
  - 用途：串联 featurizer、splitter、model 与评估流程
  - 复用状态：ready_for_review；类型：code_entry
- `src/deepmol/feature_importance/shap_values.py`
  - 能力：模型解释
  - 用途：生成特征重要性与 SHAP 解释
  - 复用状态：ready_for_review；类型：code_entry

### training

- `src/deepmol/models/atmol/model_gat_pre.py`
  - 能力：GAT 预训练/下游训练
  - 用途：图神经网络预训练模型定义
  - 复用状态：partial；类型：code_entry
- `src/deepmol/models/atmol/main_clr_downstream.py`
  - 能力：对比学习下游训练
  - 用途：下游任务训练/微调流程入口候选
  - 复用状态：partial；类型：code_entry
- `src/deepmol/parameter_optimization/hyperparameter_optimization.py`
  - 能力：超参数优化
  - 用途：训练过程的参数搜索编排
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅基于冻结清单与路径存在性做静态审查，未读取源码内容。
- 依赖未安装、代码未执行、测试未运行，因此不能证明可复现性。
- 未发现明确 training entrypoint；训练相关文件更像辅助模块或候选入口。
- 测试数据、资源数据库与权重文件的来源、再许可与分发限制未被验证。

## 仍未知

- `tests/data/*` 中的数据是否完全由项目自制，静态清单无法确认。
- `.pt` 与 `.pkl` 权重/资源是否对应正式训练产物，来源与训练语料未知。
- `src/deepmol/compound_featurization/nc_mfp/databases/*` 的外部依赖与版权状态未知。
- 是否存在未列出的下载器、远程模型或运行时外部资源，静态 inventory 无法排除。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
