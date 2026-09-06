# AIRI-Institute/GENA_LM

- **仓库：** [https://github.com/AIRI-Institute/GENA_LM](https://github.com/AIRI-Institute/GENA_LM)
- **固定 commit：** `ed71502f71538ea1e28485381ac94fcae7211818`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 29

## 仓库摘要

仓库主体是 DNA language model 工具链：包含 genome corpus/tokenizer 构建、BERT/RMT 主干、Enformer/modernGENA 下游微调与评测脚本；冻结快照未见 checkpoint 或独立 inference 入口，代码为 MIT，但数据与模型相关产物的许可边界仍需逐项核查。

## 可复用模块与资源

### datasets

- `data/athaliana/athaliana_holdouts/GCF_000001735_4.testholdout.bed`
  - 能力：arabidopsis_holdout
  - 用途：A. thaliana holdout split 与统计信息，用于基因组建模基准
  - 复用状态：partial；类型：unknown
- `data/fly/fly_holdouts/D_MELANOGASTER.testholdout.bed`
  - 能力：fly_holdout
  - 用途：D. melanogaster holdout split 与统计信息
  - 复用状态：partial；类型：unknown
- `data/yeasts/yeast_holdouts/sacCer3.testholdout.bed`
  - 能力：yeast_holdout
  - 用途：S. cerevisiae holdout split、统计与上游 assembly 链接
  - 复用状态：partial；类型：unknown
- `data/full_ensembl_genomes_metadata.cvs`
  - 能力：genome_metadata
  - 用途：Ensembl genome 元数据表，用于语料/样本构建与物种映射
  - 复用状态：unknown；类型：unknown
- `downstream_tasks/promoter_prediction/hg38_promoters_len_300_dataset.csv`
  - 能力：promoter_dataset
  - 用途：human promoter prediction 基准数据集
  - 复用状态：partial；类型：unknown
- `downstream_tasks/DeepSea/test.dataset.csv.gz`
  - 能力：deepsea_test_split
  - 用途：DeepSea 测试集/基准分割
  - 复用状态：partial；类型：unknown
- `downstream_tasks/DeepSTARR/test_Sequences.fa`
  - 能力：deepstarr_test_split
  - 用途：DeepSTARR 测试序列与 activity 标签
  - 复用状态：partial；类型：unknown
- `downstream_tasks/APARENT/AparentDataset_test_data.csv`
  - 能力：aparent_test_split
  - 用途：APARENT 测试数据
  - 复用状态：partial；类型：unknown
- `downstream_tasks/SpliceAI/test_Dataset_data.csv`
  - 能力：spliceai_test_split
  - 用途：SpliceAI 测试数据
  - 复用状态：partial；类型：unknown

### evaluation

- `downstream_tasks/enformer/evaluate_enformer.sh`
  - 能力：enformer_evaluation
  - 用途：标准 Enformer 评测/推理 launcher
  - 复用状态：ready_for_review；类型：code_entry
- `downstream_tasks/enformer/evaluate_enformer_augs.sh`
  - 能力：enformer_augmented_evaluation
  - 用途：带数据增强的 Enformer 评测 launcher
  - 复用状态：ready_for_review；类型：code_entry
- `downstream_tasks/enformer/evaluate_enformer_rmt_sparse.sh`
  - 能力：enformer_sparse_rmt_evaluation
  - 用途：sparse/RMT 评测 launcher
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/gena_lm/modeling_bert.py`
  - 能力：dna_backbone
  - 用途：BERT-style DNA language model 主干，用于预训练与迁移微调
  - 复用状态：ready_for_review；类型：code_entry
- `src/gena_lm/modeling_rmt.py`
  - 能力：long_context_dna_model
  - 用途：RMT/长上下文记忆式 DNA 建模实现
  - 复用状态：ready_for_review；类型：code_entry
- `src/gena_lm/genome_tools/create_corpus.py`
  - 能力：corpus_builder
  - 用途：构建 genome corpus；与多 genome/allele 语料生成流程配套
  - 复用状态：ready_for_review；类型：code_entry
- `src/gena_lm/tokenizers/tokenize_genomes.py`
  - 能力：genome_tokenization
  - 用途：将基因组序列切分/编码为模型输入 token
  - 复用状态：ready_for_review；类型：code_entry
- `data/download_data.sh`
  - 能力：data_download_pipeline
  - 用途：下载并整理训练/评测相关数据的总入口脚本
  - 复用状态：ready_for_review；类型：code_entry
- `data/configs/L12-H768-A12-V32k-preln.json`
  - 能力：config_recipe
  - 用途：预训练/微调的 backbone 配置模板；可复用为实验 recipe 起点
  - 复用状态：ready_for_review；类型：config
- `downstream_tasks/enformer/enformer_model.py`
  - 能力：downstream_model
  - 用途：Enformer-style 下游模型实现，用于长序列回归/预测
  - 复用状态：ready_for_review；类型：code_entry
- `examples/modernGENA/token_regression/model.py`
  - 能力：token_regression_model
  - 用途：ModernGENA token regression 头/模型实现
  - 复用状态：ready_for_review；类型：code_entry
- `data/tokenizers/human/BPE_32k/tokenizer.json`
  - 能力：tokenizer_bundle
  - 用途：预构建 human BPE tokenizer 产物，可直接供下游脚本加载
  - 复用状态：partial；类型：tokenizer
- `examples/modernGENA/sequence_classification/configs/config.yaml`
  - 能力：example_training_config
  - 用途：ModernGENA sequence classification 微调配置
  - 复用状态：ready_for_review；类型：config

### training

- `examples/modernGENA/sequence_classification/train.py`
  - 能力：sequence_classification_finetuning
  - 用途：ModernGENA 序列分类微调入口
  - 复用状态：ready_for_review；类型：code_entry
- `examples/modernGENA/token_regression/train.py`
  - 能力：token_regression_finetuning
  - 用途：ModernGENA token regression 微调入口
  - 复用状态：ready_for_review；类型：code_entry
- `downstream_tasks/promoter_prediction/run_promoter_finetuning.py`
  - 能力：promoter_finetuning
  - 用途：promoter_prediction 训练入口与其变体 launcher
  - 复用状态：ready_for_review；类型：code_entry
- `downstream_tasks/DeepSea/run_deepsea_finetuning.py`
  - 能力：deepsea_finetuning
  - 用途：DeepSea 训练入口
  - 复用状态：ready_for_review；类型：code_entry
- `downstream_tasks/APARENT/run_APARENT_finetuning.py`
  - 能力：aparent_finetuning
  - 用途：APARENT 训练入口
  - 复用状态：ready_for_review；类型：code_entry
- `downstream_tasks/SpliceAI/run_spliceai_finetuning.py`
  - 能力：spliceai_finetuning
  - 用途：SpliceAI 训练入口及其 RMT/sparse 变体
  - 复用状态：ready_for_review；类型：code_entry
- `downstream_tasks/enformer/run_enformer_finetuning.py`
  - 能力：enformer_finetuning
  - 用途：Enformer 训练入口及其 sparse/RMT 变体
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审计，未执行仓库代码。
- 依赖未安装，tests 未运行。
- submodules 未初始化。
- 超过 5MiB 的 blob 可能仅为 promisor object。
- 路径存在不等于可复现或可重现训练结果。

## 仍未知

- 未见任何 checkpoint 文件，无法评估权重可复用性。
- 未见独立 inference 入口；现有脚本主要是训练/评测 launcher。
- `data/full_ensembl_genomes_metadata.cvs` 与 `data/yeasts/ENA_PRJEB59413_assmebly_links.tsv` 等外部来源元数据的上游许可未在冻结库存中闭合。
- tokenizer 与若干 CSV/TSV/BED/FA 产物看起来是项目构建物，但生成链路与分发边界未被静态证明。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
