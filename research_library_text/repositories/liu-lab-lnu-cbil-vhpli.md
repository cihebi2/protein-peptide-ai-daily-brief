# liu-lab-lnu/cbil-vhpli

- **仓库：** [https://github.com/liu-lab-lnu/cbil-vhpli](https://github.com/liu-lab-lnu/cbil-vhpli)
- **固定 commit：** `6e0e34b8d3baa555ecbe46dfa75116ef7b3ccdea`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 34

## 仓库摘要

仓库静态清单显示这是一个用于 viral-host protein-lncRNA interaction 预测的项目，包含两份训练脚本、多个数据文件与 10 个模型权重，但未发现独立推理、评估、配置或许可证文件。

## 可复用模块与资源

### checkpoints

- `models/CNN_pretrained.h5`
  - 能力：CNN pretrained checkpoint
  - 用途：CNN 基线的预训练权重
  - 复用状态：blocked；类型：model_weight
- `models/CNN_finetune.h5`
  - 能力：CNN fine-tuned checkpoint
  - 用途：CNN 基线的微调权重
  - 复用状态：blocked；类型：model_weight
- `models/RNN_pretrained.h5`
  - 能力：RNN pretrained checkpoint
  - 用途：RNN 基线的预训练权重
  - 复用状态：blocked；类型：model_weight
- `models/RNN_finetune.h5`
  - 能力：RNN fine-tuned checkpoint
  - 用途：RNN 基线的微调权重
  - 复用状态：blocked；类型：model_weight
- `models/LSTM_pretrained.h5`
  - 能力：LSTM pretrained checkpoint
  - 用途：LSTM 基线的预训练权重
  - 复用状态：blocked；类型：model_weight
- `models/LSTM_finetune.h5`
  - 能力：LSTM fine-tuned checkpoint
  - 用途：LSTM 基线的微调权重
  - 复用状态：blocked；类型：model_weight
- `models/BiLSTM_pretrained.h5`
  - 能力：BiLSTM pretrained checkpoint
  - 用途：BiLSTM 基线的预训练权重
  - 复用状态：blocked；类型：model_weight
- `models/BiLSTM_finetune.h5`
  - 能力：BiLSTM fine-tuned checkpoint
  - 用途：BiLSTM 基线的微调权重
  - 复用状态：blocked；类型：model_weight
- `models/CBIL–VHPLI_pretrained.h5`
  - 能力：CBIL–VHPLI pretrained checkpoint
  - 用途：CBIL–VHPLI 主模型的预训练权重
  - 复用状态：blocked；类型：model_weight
- `models/CBIL–VHPLI_finetune.h5`
  - 能力：CBIL–VHPLI fine-tuned checkpoint
  - 用途：CBIL–VHPLI 主模型的微调权重
  - 复用状态：blocked；类型：model_weight

### datasets

- `data.zip`
  - 能力：bundled dataset archive
  - 用途：仓库打包的数据归档，可能包含下列训练/评估数据文件
  - 复用状态：blocked；类型：unknown
- `data/RPI1807/RPI1807.csv`
  - 能力：RPI1807 benchmark labels
  - 用途：RPI1807 数据集的标签/样本清单
  - 复用状态：blocked；类型：unknown
- `data/RPI1807/RPI1807_NegativePairs.csv`
  - 能力：RPI1807 negative pairs
  - 用途：RPI1807 的负样本对
  - 复用状态：blocked；类型：unknown
- `data/RPI1807/RPI1807_PositivePairs.csv`
  - 能力：RPI1807 positive pairs
  - 用途：RPI1807 的正样本对
  - 复用状态：blocked；类型：unknown
- `data/RPI1807/RPI1807_RNA_seq.fa`
  - 能力：RPI1807 RNA sequences
  - 用途：RPI1807 的 RNA 序列
  - 复用状态：blocked；类型：unknown
- `data/RPI1807/RPI1807_protein_seq.fa`
  - 能力：RPI1807 protein sequences
  - 用途：RPI1807 的蛋白序列
  - 复用状态：blocked；类型：unknown
- `data/RPI18072/pretrain_data.csv`
  - 能力：RPI18072 pretraining table
  - 用途：预训练数据表
  - 复用状态：blocked；类型：unknown
- `data/RPI18072/lncRNAProteinInteraction.xlsx`
  - 能力：RPI18072 interaction workbook
  - 用途：lncRNA-protein interaction 记录表
  - 复用状态：blocked；类型：unknown
- `data/RPI18072/lncRNASeq.fasta.txt`
  - 能力：RPI18072 lncRNA sequences
  - 用途：RPI18072 的 lncRNA 序列
  - 复用状态：blocked；类型：unknown
- `data/RPI18072/proteinSeq.fasta.txt`
  - 能力：RPI18072 protein sequences
  - 用途：RPI18072 的蛋白序列
  - 复用状态：blocked；类型：unknown
- `data/RPI2241/RPI2241.csv`
  - 能力：RPI2241 benchmark labels
  - 用途：RPI2241 数据集标签/样本表
  - 复用状态：blocked；类型：unknown
- `data/RPI2241/RPI2241_all.txt`
  - 能力：RPI2241 auxiliary table
  - 用途：RPI2241 的汇总/辅助文本表
  - 复用状态：blocked；类型：unknown
- `data/RPI2241/RPI2241_protein.fa`
  - 能力：RPI2241 protein sequences
  - 用途：RPI2241 的蛋白序列
  - 复用状态：blocked；类型：unknown
- `data/RPI2241/RPI2241_rna.fa`
  - 能力：RPI2241 RNA sequences
  - 用途：RPI2241 的 RNA 序列
  - 复用状态：blocked；类型：unknown
- `data/RPI488/RPI488.csv`
  - 能力：RPI488 benchmark labels
  - 用途：RPI488 数据集标签/样本表
  - 复用状态：blocked；类型：unknown
- `data/RPI488/lncRNA-protein-488.txt`
  - 能力：RPI488 pair list
  - 用途：RPI488 的配对文本清单
  - 复用状态：blocked；类型：unknown
- `data/RPI488/RPI488_RNA.fa`
  - 能力：RPI488 RNA sequences
  - 用途：RPI488 的 RNA 序列
  - 复用状态：blocked；类型：unknown
- `data/RPI488/RPI488_protein.fa`
  - 能力：RPI488 protein sequences
  - 用途：RPI488 的蛋白序列
  - 复用状态：blocked；类型：unknown
- `data/vhRPI286/lncRNAProteinInteraction.csv`
  - 能力：vhRPI286 interaction table
  - 用途：vhRPI286 的 interaction 标签表
  - 复用状态：blocked；类型：unknown
- `data/vhRPI286/unique_protein_sequencesOutput.fasta`
  - 能力：vhRPI286 protein sequences
  - 用途：vhRPI286 的去重蛋白序列
  - 复用状态：blocked；类型：unknown
- `data/vhRPI286/unique_rna_sequences.fasta`
  - 能力：vhRPI286 RNA sequences
  - 用途：vhRPI286 的去重 RNA 序列
  - 复用状态：blocked；类型：unknown
- `data/vhRPI286/vhRPI286.csv`
  - 能力：vhRPI286 benchmark labels
  - 用途：vhRPI286 数据集标签/样本表
  - 复用状态：blocked；类型：unknown

### training

- `CBIL–VHPLI_pretrain.py`
  - 能力：pretraining entrypoint
  - 用途：主模型预训练入口
  - 复用状态：blocked；类型：code_entry
- `CBIL–VHPLI_finetune.py`
  - 能力：fine-tuning entrypoint
  - 用途：主模型微调入口
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态盘点，未运行任何代码或测试。
- 依赖未安装，模型权重与训练脚本未被实际执行。
- 未发现独立 inference、evaluation、config 或 model-architecture 文件。
- 数据文件的上游来源与许可边界无法仅凭清单确认。

## 仍未知

- 各数据文件是否为原始数据、派生整理还是第三方复制，无法仅凭静态清单确认。
- 10 个 .h5 权重的训练轮次、指标和生成流程未知。
- CBIL–VHPLI_pretrain.py 与 CBIL–VHPLI_finetune.py 的实际输入输出与运行条件未验证。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
