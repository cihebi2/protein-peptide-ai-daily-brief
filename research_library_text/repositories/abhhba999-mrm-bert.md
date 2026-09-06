# abhhba999/MRM-BERT

- **仓库：** [https://github.com/abhhba999/MRM-BERT](https://github.com/abhhba999/MRM-BERT)
- **固定 commit：** `a0269a461c740a41aaaffc36926b70e65218b038`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 18

## 仓库摘要

该冻结仓库主要是 DNABERT/HuggingFace 代码镜像加上 m6Am 数据、训练/评估脚本和结果文件；未见 checkpoint 与 LICENSE，当前只能做静态复用性盘点。

## 可复用模块与资源

### datasets

- `dataset/CD-fasta/m6Am.fasta`
  - 能力：m6Am FASTA 原始序列
  - 用途：m6Am 样本序列集合
  - 复用状态：unknown；类型：unknown
- `dataset/bert/classic/m6Am/train.tsv`
  - 能力：m6Am 训练/验证 TSV 与缓存
  - 用途：训练集与开发集切分，以及已缓存的特征文件
  - 复用状态：unknown；类型：unknown
- `dataset/test/m6Am/positive.txt`
  - 能力：测试集正负样本
  - 用途：m6Am 二分类测试正例/负例文本
  - 复用状态：unknown；类型：unknown
- `dataset/dataset_of_MRM-BERT.zip`
  - 能力：数据打包归档
  - 用途：整包数据归档/分发
  - 复用状态：unknown；类型：unknown

### evaluation

- `DNABERT/examples/transformers/data/metrics/squad_metrics.py`
  - 能力：指标实现
  - 用途：通用指标计算模块（SQuAD 风格）
  - 复用状态：blocked；类型：code_entry
- `results/tables/m6Am.csv`
  - 能力：结果表
  - 用途：m6Am 结果汇总表
  - 复用状态：unknown；类型：unknown
- `results/tables/img/roc_curve_m6Am.pdf`
  - 能力：ROC 图
  - 用途：m6Am ROC 曲线图
  - 复用状态：unknown；类型：unknown

### inference

- `DNABERT/SNP/SNP.py`
  - 能力：SNP/变异序列推断
  - 用途：从文件名看，用于 SNP 或变异序列打分/预测
  - 复用状态：blocked；类型：code_entry
- `DNABERT/SNP/mutate_seqs.py`
  - 能力：变异序列生成
  - 用途：从文件名看，用于生成突变序列供后续推断
  - 复用状态：blocked；类型：code_entry
- `DNABERT/examples/compute_result.py`
  - 能力：结果汇总/预测输出
  - 用途：从文件名看，用于计算或汇总预测结果
  - 复用状态：blocked；类型：code_entry
- `DNABERT/examples/scripts/run_mut.sh`
  - 能力：推断脚本包装
  - 用途：命令行包装突变/推断流程
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `DNABERT/examples/transformers/modeling_encoder_decoder.py`
  - 能力：模型架构/编码器-解码器工具
  - 用途：通用 Transformer 编码器-解码器实现与辅助封装
  - 复用状态：blocked；类型：code_entry
- `DNABERT/examples/data_process_template/process_finetune_data.py`
  - 能力：数据处理/processor/metrics
  - 用途：预训练/微调数据转换，以及 GLUE/SQuAD/XNLI 风格 processor 与指标实现
  - 复用状态：blocked；类型：code_entry
- `DNABERT/examples/transformers/dnabert-config/bert-config-3/config.json`
  - 能力：DNABERT tokenizer/config/vocab
  - 用途：k-mer tokenizer 配置与词表，覆盖 bert-config-3/4/5/6
  - 复用状态：blocked；类型：config

### training

- `DNABERT/examples/run_pretrain.py`
  - 能力：预训练入口
  - 用途：从文件名看，用于启动 DNABERT 预训练流程
  - 复用状态：blocked；类型：code_entry
- `DNABERT/examples/run_finetune.py`
  - 能力：微调入口
  - 用途：从文件名看，用于启动分类/微调流程
  - 复用状态：blocked；类型：code_entry
- `DNABERT/examples/transformers/commands/train.py`
  - 能力：通用训练命令
  - 用途：通用 Transformers 训练命令入口
  - 复用状态：blocked；类型：code_entry
- `train_eval.ipynb`
  - 能力：训练/评估 notebook
  - 用途：交互式训练与评估流程编排
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- 仓库未见 checkpoint 文件，无法核实是否存在外部权重发布。
- 大量 DNABERT/transformers 代码看起来是第三方镜像或复用件，是否有本地改动未验证。
- 未展开压缩包和缓存文件，无法证明其可重建性或数据生成链路。

## 仍未知

- train_eval.ipynb、run_pretrain.py、run_finetune.py 的实际参数与输出未核验。
- dataset_of_MRM-BERT.zip 的内部内容未展开。
- cached_train_m6Am_101_dnaprom 与 cached_dev_m6Am_101_dnaprom 是否可由原始数据重建未核验。
- SNP.py、mutate_seqs.py、compute_result.py 的具体流程仅能按文件名推断。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
