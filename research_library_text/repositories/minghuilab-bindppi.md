# minghuilab/BindPPI

- **仓库：** [https://github.com/minghuilab/BindPPI](https://github.com/minghuilab/BindPPI)
- **固定 commit：** `8ac1e793d4fb4fe4156f8954cbf0afbee9e5d8a7`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 10

## 仓库摘要

冻结清单显示该仓库主要是数据与示例结果包：`Datasets/` 下有 4 个文本集和说明文档，`example_1akj`/`example_1ava`/`MLP5120_example` 仅见输入、清洗和预测产物；未见训练、评测、检查点或许可证文件，直接复用边界未闭合。

## 可复用模块与资源

### datasets

- `Datasets/README.md`
  - 能力：dataset documentation
  - 用途：说明 `Datasets/` 目录中的捆绑数据组织方式
  - 复用状态：unknown；类型：unknown
- `Datasets/S108.txt`
  - 能力：benchmark text dataset
  - 用途：捆绑的文本数据集文件；具体标签和划分无法仅凭静态清单确认
  - 复用状态：blocked；类型：unknown
- `Datasets/S192.txt`
  - 能力：benchmark text dataset
  - 用途：捆绑的文本数据集文件；具体标签和划分无法仅凭静态清单确认
  - 复用状态：blocked；类型：unknown
- `Datasets/S365.txt`
  - 能力：benchmark text dataset
  - 用途：捆绑的文本数据集文件；具体标签和划分无法仅凭静态清单确认
  - 复用状态：blocked；类型：unknown
- `Datasets/S802.txt`
  - 能力：benchmark text dataset
  - 用途：捆绑的文本数据集文件；具体标签和划分无法仅凭静态清单确认
  - 复用状态：blocked；类型：unknown

### inference

- `example_1akj/1AKJ.pdb`
  - 能力：protein structure input sample
  - 用途：1AKJ 结构输入示例；与 `example_1akj` 下的预处理/预测文件配套
  - 复用状态：unknown；类型：unknown
- `example_1akj/example_1akj.input`
  - 能力：preprocessed inference bundle
  - 用途：输入清洗与预测结果链路；对应 `.input.cleaned`、`.json`、`.AvgEns`、`.RF13`
  - 复用状态：blocked；类型：unknown
- `example_1ava/1AVA.pdb`
  - 能力：protein structure input sample
  - 用途：1AVA 结构输入示例；与 `example_1ava` 下的预处理/预测文件配套
  - 复用状态：unknown；类型：unknown
- `example_1ava/example_1ava.input`
  - 能力：preprocessed inference bundle
  - 用途：输入清洗与预测结果链路；对应 `.input.cleaned`、`.json`、`.AvgEns`、`.RF13`
  - 复用状态：blocked；类型：unknown
- `MLP5120_example/MLP5120_prediction.txt`
  - 能力：sequence inference example
  - 用途：序列示例的预测输出；对应输入见 `sample_input_sequence.json`
  - 复用状态：blocked；类型：unknown

## 使用限制

- 静态清单仅显示文件存在，不证明可运行性或复现性。
- 仓库未见训练入口、评测脚本或模型检查点，方法实现不可验证。
- `example_1akj`、`example_1ava` 中的 `.AvgEns` / `.RF13` 产物来源与生成流程未能仅凭清单确认。
- 未见许可证文件，代码与数据的再分发边界未闭合。

## 仍未知

- `Datasets/S108.txt`、`S192.txt`、`S365.txt`、`S802.txt` 的具体标签、划分和来源未读到。
- `1AKJ.pdb` 与 `1AVA.pdb` 是否为仓库自生成还是外部结构文件，静态清单无法确认。
- 冻结快照是否遗漏了未初始化子模块或大文件中的方法代码，无法从当前清单排除。
- `MLP5120_example` 是否对应完整模型实现还是仅为示例输出包，无法确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
