# hurlab/ppi-gpt-bert

- **仓库：** [https://github.com/hurlab/ppi-gpt-bert](https://github.com/hurlab/ppi-gpt-bert)
- **固定 commit：** `50e96bdb10beef83151dfa33063d3ceffb24489c`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 27

## 仓库摘要

仓库包含PPI文本识别的GPT/BERT实验笔记本、提示词、预处理数据与评测产物；未见独立checkpoint或模型权重。

## 可复用模块与资源

### datasets

- `Datasets/csv_output/merged-train.csv`
  - 能力：merged training split
  - 用途：合并后的训练集，用于整体 PPI 文本分类实验。
  - 复用状态：partial；类型：unknown
- `Datasets/csv_output/merged-test.csv`
  - 能力：merged test split
  - 用途：合并后的测试集，用于整体评测。
  - 复用状态：partial；类型：unknown
- `Datasets/csv_output/AIMed-train.csv`
  - 能力：AIMed train split
  - 用途：AIMed 的训练划分。
  - 复用状态：partial；类型：unknown
- `Datasets/csv_output/AIMed-test.csv`
  - 能力：AIMed test split
  - 用途：AIMed 的测试划分。
  - 复用状态：partial；类型：unknown
- `Datasets/csv_output/BioInfer-train.csv`
  - 能力：BioInfer train split
  - 用途：BioInfer 的训练划分。
  - 复用状态：partial；类型：unknown
- `Datasets/csv_output/BioInfer-test.csv`
  - 能力：BioInfer test split
  - 用途：BioInfer 的测试划分。
  - 复用状态：partial；类型：unknown
- `Datasets/csv_output/HPRD50-train.csv`
  - 能力：HPRD50 train split
  - 用途：HPRD50 的训练划分。
  - 复用状态：partial；类型：unknown
- `Datasets/csv_output/HPRD50-test.csv`
  - 能力：HPRD50 test split
  - 用途：HPRD50 的测试划分。
  - 复用状态：partial；类型：unknown
- `Datasets/csv_output/IEPA-train.csv`
  - 能力：IEPA train split
  - 用途：IEPA 的训练划分。
  - 复用状态：partial；类型：unknown
- `Datasets/csv_output/IEPA-test.csv`
  - 能力：IEPA test split
  - 用途：IEPA 的测试划分。
  - 复用状态：partial；类型：unknown
- `Datasets/csv_output/LLL-train.csv`
  - 能力：LLL train split
  - 用途：LLL 的训练划分。
  - 复用状态：partial；类型：unknown
- `Datasets/csv_output/LLL-test.csv`
  - 能力：LLL test split
  - 用途：LLL 的测试划分。
  - 复用状态：partial；类型：unknown
- `Datasets/PROTEIN_DATA/HPRD50/N_fold/N_fold_csv/fold1.csv`
  - 能力：HPRD50 N-fold CSV exemplar
  - 用途：HPRD50 的 N-fold 预处理分割样例。
  - 复用状态：partial；类型：unknown
- `Datasets/PROTEIN_DATA/IEPA/N_fold/N_fold_csv/fold1.csv`
  - 能力：IEPA N-fold CSV exemplar
  - 用途：IEPA 的 N-fold 预处理分割样例。
  - 复用状态：partial；类型：unknown
- `Datasets/PROTEIN_DATA/LLL/N_fold/N_fold_csv/fold1.csv`
  - 能力：LLL N-fold CSV exemplar
  - 用途：LLL 的 N-fold 预处理分割样例。
  - 复用状态：partial；类型：unknown

### evaluation

- `GPT_PPI_Original_Sentence_Evaluation.ipynb`
  - 能力：GPT original-sentence evaluation notebook
  - 用途：对 GPT 原始句子实验做后处理和评测。
  - 复用状态：partial；类型：unknown
- `10fold_PROTEIN_Postprocessing_and_evaluation.ipynb`
  - 能力：PROTEIN 10-fold evaluation notebook
  - 用途：10-fold PROTEIN 结果的后处理与评测。
  - 复用状态：partial；类型：unknown
- `N_fold_PROTEIN_Postprocessing_and_evaluation.ipynb`
  - 能力：N-fold evaluation notebook
  - 用途：N-fold PROTEIN 结果的后处理与评测。
  - 复用状态：partial；类型：unknown
- `PROTEIN_OneSentence_Postprocessing_and_evaluation.ipynb`
  - 能力：One-sentence evaluation notebook
  - 用途：单句设置下的后处理与评测。
  - 复用状态：partial；类型：unknown

### inference

- `GPT_PPI_Original_Sentence.ipynb`
  - 能力：GPT inference notebook
  - 用途：原始句子上的 GPT 推断流程。
  - 复用状态：partial；类型：unknown
- `GPT_PPI_PROTEIN_1Sentence.ipynb`
  - 能力：GPT one-sentence inference notebook
  - 用途：单句设定下的 GPT 推断流程。
  - 复用状态：partial；类型：unknown
- `GPT_PPI_PROTEIN_Nfold.ipynb`
  - 能力：GPT N-fold inference notebook
  - 用途：N-fold 数据上的 GPT 推断流程。
  - 复用状态：partial；类型：unknown

### reusable_assets

- `BERT_For_PPI.ipynb`
  - 能力：BERT baseline notebook
  - 用途：BERT 基线实验入口，可能包含文本分类/微调与记录流程。
  - 复用状态：partial；类型：unknown
- `GPT_PPI_Original_Sentence.ipynb`
  - 能力：GPT prompting notebook
  - 用途：原始句子上的 GPT 提示推断/实验入口。
  - 复用状态：partial；类型：unknown
- `Prompts/Final_Prompts/P60_S3_BASE-PROTEIN.txt`
  - 能力：Prompt template
  - 用途：通用的 PPI 提示词模板，可作为复现实验的配置基底。
  - 复用状态：ready_for_review；类型：unknown
- `Prompts/Final_Prompts/P60_S3_WD_HPRD50.txt`
  - 能力：Dataset-specific prompt template
  - 用途：面向 HPRD50 的带词典/数据集定制提示配置。
  - 复用状态：ready_for_review；类型：unknown

### training

- `BERT_For_PPI.ipynb`
  - 能力：BERT training notebook
  - 用途：可能包含 BERT 训练/微调与实验记录；静态仅能确认笔记本存在。
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态审查，未运行 notebook、未安装依赖、未验证输出。
- tracked 文件存在不等于训练完成、推断成功或复现成立。
- 未见 tracked checkpoint / model weight，无法把任何权重当作可直接复用产物。
- 数据来源与授权边界不完整，尤其是 AIMed/BioInfer/HPRD50/IEPA/LLL 的上游许可未被静态确认。

## 仍未知

- 各 notebook 是否包含完整可执行参数、随机种子和环境锁定，静态无法确认。
- `plots/*.svg` 是否由当前笔记本可完全重建，静态无法确认。
- `csv_output` 与论文最终表格是否一一对应，静态无法确认。
- 部分数据文件可能是派生整理版还是原始语料切片，静态无法区分。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
