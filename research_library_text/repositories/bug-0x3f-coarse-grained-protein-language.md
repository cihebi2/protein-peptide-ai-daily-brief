# bug-0x3f/coarse-grained-protein-language

- **仓库：** [https://github.com/bug-0x3f/coarse-grained-protein-language](https://github.com/bug-0x3f/coarse-grained-protein-language)
- **固定 commit：** `76a813436d0ea78409645d4d9726f3f6301c876b`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 21

## 仓库摘要

该仓库是一个围绕结构感知 coarse-grained protein language modeling 的研究代码库，包含预训练、Doc2Vec、词表训练、EC/GO/RNA-binding 下游分类、DSSP/HHM/PSSM 特征提取与若干 bundled 资源；冻结清单未见明确 LICENSE，也未见真正的模型权重文件。

## 可复用模块与资源

### checkpoints

- `pretrain/language_model/Bert-based/weights/PLMs/SCG_Layer6/config.json`
  - 能力：SCG_Layer6_checkpoint_metadata
  - 用途：SCG_Layer6 的配置与 tokenizer/词表元数据；冻结清单中未见实际模型参数文件（例如 .bin/.pt/.ckpt）。
  - 复用状态：blocked；类型：config

### datasets

- `datasets/EC/nrPDB-EC_annot.tsv`
  - 能力：EC_classification_dataset
  - 用途：EC 功能预测的数据注释与训练/验证/测试划分。
  - 复用状态：blocked；类型：unknown
- `datasets/GO/nrPDB-GO_annot.tsv`
  - 能力：GO_classification_dataset
  - 用途：GO 功能预测的数据注释与训练/验证/测试划分。
  - 复用状态：blocked；类型：unknown
- `datasets/RNA-binding/labels.txt`
  - 能力：RNA_binding_dataset
  - 用途：RNA-binding 预测任务的数据标签与划分。
  - 复用状态：blocked；类型：unknown
- `datasets/pretrain_proteins.txt`
  - 能力：pretraining_corpus
  - 用途：蛋白预训练语料/序列集合。
  - 复用状态：blocked；类型：unknown

### evaluation

- `pretrain/language_model/Bert-based/utils/metrics.py`
  - 能力：metrics_helpers
  - 用途：分类/回归评估指标实现。
  - 复用状态：blocked；类型：code_entry
- `downstream/EC/test.py`
  - 能力：task_test_scripts
  - 用途：三个下游任务的测试/评估入口。
  - 复用状态：blocked；类型：code_entry

### inference

- `preprocess/generate_dssp.py`
  - 能力：structure_feature_generation
  - 用途：基于结构文件生成 DSSP 相关特征；更接近离线特征生成而非在线推理。
  - 复用状态：blocked；类型：code_entry
- `pretrain/language_model/Doc2Vec/generate_corpus.py`
  - 能力：corpus_generation
  - 用途：为 Doc2Vec 训练/使用生成语料文本。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `pretrain/language_model/Bert-based/model/abstract_model.py`
  - 能力：model_architecture
  - 用途：定义 protein LM、ESM 包装层与 vocabulary 相关网络接口，是方法主体代码。
  - 复用状态：blocked；类型：code_entry
- `pretrain/language_model/Bert-based/dataset/lmdb_dataset.py`
  - 能力：dataset_interface
  - 用途：封装 LMDB、ESM LM 与 mutation zero-shot 数据读取/组批逻辑。
  - 复用状态：blocked；类型：code_entry
- `preprocess/generate_dssp.py`
  - 能力：feature_preprocessing
  - 用途：生成 DSSP、HHM、PSSM 与结构切分等蛋白特征，服务于预训练和下游任务。
  - 复用状态：blocked；类型：code_entry
- `pretrain/language_model/Bert-based/utils/metrics.py`
  - 能力：training_support_and_metrics
  - 用途：训练/评估辅助、模型加载、学习率调度与指标计算。
  - 复用状态：blocked；类型：code_entry
- `pretrain/language_model/Doc2Vec/generate_corpus.py`
  - 能力：doc2vec_pipeline
  - 用途：构建 Doc2Vec 语料并提取蛋白特征。
  - 复用状态：blocked；类型：code_entry
- `lib/dssp`
  - 能力：bundled_third_party_tooling
  - 用途：为序列/结构特征提取提供 bundled 外部矩阵或二进制依赖；其许可与来源未在冻结清单中明确。
  - 复用状态：blocked；类型：unknown

### training

- `downstream/EC/train.py`
  - 能力：EC_training_entrypoint
  - 用途：EC 下游训练入口。
  - 复用状态：blocked；类型：code_entry
- `downstream/GO/train.py`
  - 能力：GO_training_entrypoint
  - 用途：GO 下游训练入口。
  - 复用状态：blocked；类型：code_entry
- `downstream/RNA_binding/train.py`
  - 能力：RNA_binding_training_entrypoint
  - 用途：RNA-binding 下游训练入口。
  - 复用状态：blocked；类型：code_entry
- `pretrain/language_model/Bert-based/scripts/training.py`
  - 能力：Bert_based_pretraining_entrypoint
  - 用途：Bert-based protein LM 预训练入口。
  - 复用状态：blocked；类型：code_entry
- `pretrain/language_model/Doc2Vec/train.py`
  - 能力：Doc2Vec_training_entrypoint
  - 用途：Doc2Vec 模型训练入口。
  - 复用状态：blocked；类型：code_entry
- `pretrain/vocabulary/training.py`
  - 能力：vocabulary_training_entrypoint
  - 用途：词表/句子构建训练入口。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码、测试或训练。
- 未安装依赖，无法验证环境可复现性。
- 子模块未初始化，可能缺失外部依赖或资产。
- 大文件可能是 promisor-only，且无法确认所有权重是否完整。
- 路径存在不等于可复现或可运行。

## 仍未知

- `pretrain/language_model/Bert-based/weights/PLMs/SCG_Layer6/` 是否还存在未跟踪的真实权重文件。
- `datasets/*` 的外部来源、脱敏程度与许可是否明确。
- `lib/blosum62`、`lib/dssp`、`lib/psiblast` 的第三方来源和许可证。
- `README.md` 是否包含未被许可证文件覆盖的额外使用限制。
- 下游 `test.py` 的评估口径是否与论文或 README 完全一致。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
