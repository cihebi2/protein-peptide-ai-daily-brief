# technion-cs-nlp/BiologicalTokenizers

- **仓库：** [https://github.com/technion-cs-nlp/BiologicalTokenizers](https://github.com/technion-cs-nlp/BiologicalTokenizers)
- **固定 commit：** `ac830b531a50bf3af091dfe94a95397ef7e8ea76`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 14

## 仓库摘要

仓库主要提供 biological sequence tokenizer 的训练脚本、7 组基准数据切分，以及大量已导出的 tokenizer.json 产物；未见独立的 inference 或 evaluation 入口，也未见神经网络权重 checkpoint。

## 可复用模块与资源

### checkpoints

- `BFD_Tokenizers/1000/BPE/100/tokenizer.json`
  - 能力：BFD tokenizer artifact family (1000)
  - 用途：BPE/UNI/WPC tokenizer 导出物，覆盖多种 vocab size（100–51200）。
  - 复用状态：partial；类型：tokenizer
- `BFD_Tokenizers/10000/BPE/100/tokenizer.json`
  - 能力：BFD tokenizer artifact family (10000)
  - 用途：BPE/UNI/WPC tokenizer 导出物，覆盖多种 vocab size（100–51200）。
  - 复用状态：partial；类型：tokenizer
- `BFD_Tokenizers/100000/BPE/100/tokenizer.json`
  - 能力：BFD tokenizer artifact family (100000)
  - 用途：BPE/UNI/WPC tokenizer 导出物，覆盖多种 vocab size（100–51200）。
  - 复用状态：partial；类型：tokenizer
- `BFD_Tokenizers/1000000/BPE/100/tokenizer.json`
  - 能力：BFD tokenizer artifact family (1000000)
  - 用途：BPE/UNI/WPC tokenizer 导出物，覆盖多种 vocab size（100–51200）。
  - 复用状态：partial；类型：tokenizer
- `BFD_Tokenizers/10000000/BPE/100/tokenizer.json`
  - 能力：BFD tokenizer artifact family (10000000)
  - 用途：BPE/UNI/WPC tokenizer 导出物，覆盖多种 vocab size（100–51200）。
  - 复用状态：partial；类型：tokenizer

### datasets

- `data/SuperFamily/train.csv`
  - 能力：SuperFamily benchmark split
  - 用途：train/valid/test 切分，用于序列级基准实验。
  - 复用状态：blocked；类型：unknown
- `data/effectors/train.csv`
  - 能力：effectors benchmark split
  - 用途：train/valid/test 切分，用于序列级基准实验。
  - 复用状态：blocked；类型：unknown
- `data/fluorescence/train.csv`
  - 能力：fluorescence benchmark split
  - 用途：train/valid/test 切分，用于序列级基准实验。
  - 复用状态：blocked；类型：unknown
- `data/fold_classes/train.csv`
  - 能力：fold_classes benchmark split
  - 用途：train/valid/test 切分，用于序列级基准实验。
  - 复用状态：blocked；类型：unknown
- `data/neuropeptide/train.csv`
  - 能力：neuropeptide benchmark split
  - 用途：train/valid/test 切分，用于序列级基准实验。
  - 复用状态：blocked；类型：unknown
- `data/remote_homology/train.csv`
  - 能力：remote_homology benchmark split
  - 用途：train/valid/test 切分，用于序列级基准实验。
  - 复用状态：blocked；类型：unknown
- `data/stability/train.csv`
  - 能力：stability benchmark split
  - 用途：train/valid/test 切分，用于序列级基准实验。
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `BFD_Tokenizers/1000/BPE/100/tokenizer.json`
  - 能力：tokenizer artifact bundle
  - 用途：一组可直接复用的 biological sequence tokenizer 产物，适合作为下游预处理或实验复核的输入。
  - 复用状态：partial；类型：tokenizer

### training

- `train_tokenizer_bert.py`
  - 能力：tokenizer training entrypoint
  - 用途：训练 BPE/UNI/WPC 等 tokenizer，并导出 tokenizer.json 产物。
  - 复用状态：ready_for_review；类型：tokenizer

## 使用限制

- 仅做静态清点，未执行仓库代码、未安装依赖、未运行测试。
- 未见独立的数据许可证或数据来源说明，CSV 集合的直接复用边界不清。
- 未验证 tokenizer.json 是否与脚本/论文中的结果一致，也未验证其生成过程。
- 未发现专门的 inference / evaluation 入口，无法据静态证据判断完整实验流程。

## 仍未知

- data/*.csv 的真实来源可能是项目自建切分，也可能来自外部基准；冻结清单不足以判定。
- tokenizer.json 更像训练产物/导出物而非神经网络 checkpoint，其法律边界未单独标注。
- 仓库未给出清晰的模型/数据/产物分层许可文件。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
