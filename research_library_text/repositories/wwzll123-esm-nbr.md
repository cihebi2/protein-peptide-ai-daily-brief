# wwzll123/esm-nbr

- **仓库：** [https://github.com/wwzll123/esm-nbr](https://github.com/wwzll123/esm-nbr)
- **固定 commit：** `66d1c0887f89f80a88301ea7a086dc69426b8612`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 14

## 仓库摘要

仓库静态清单显示其以训练/测试数据、说明文档和补充材料为主；未识别出训练、推理、评估代码或 checkpoint，也未发现 LICENSE 文件。

## 可复用模块与资源

### datasets

- `dataset/DNA573_Tr.fasta`
  - 能力：training split data
  - 用途：按文件名判断为训练集，用于 DNA 相关残基预测数据划分
  - 复用状态：blocked；类型：unknown
- `dataset/DNA-573_Train.txt`
  - 能力：training split data
  - 用途：按文件名判断为训练集文本版本，用于 DNA 相关残基预测数据划分
  - 复用状态：blocked；类型：unknown
- `dataset/RNA495_Tr.fasta`
  - 能力：training split data
  - 用途：按文件名判断为训练集，用于 RNA 相关残基预测数据划分
  - 复用状态：blocked；类型：unknown
- `dataset/RNA-495_Train.txt`
  - 能力：training split data
  - 用途：按文件名判断为训练集文本版本，用于 RNA 相关残基预测数据划分
  - 复用状态：blocked；类型：unknown
- `dataset/YK17-Tr.txt`
  - 能力：training split data
  - 用途：按文件名中的 Tr 判断为训练集；实际内容未核验
  - 复用状态：blocked；类型：unknown
- `dataset/DNA129_Test.fasta`
  - 能力：evaluation split data
  - 用途：按文件名判断为测试集，用于 DNA 相关残基预测评估
  - 复用状态：blocked；类型：unknown
- `dataset/DNA-129_Test.txt`
  - 能力：evaluation split data
  - 用途：按文件名判断为测试集文本版本，用于 DNA 相关残基预测评估
  - 复用状态：blocked；类型：unknown
- `dataset/RNA117_Tst.fasta`
  - 能力：evaluation split data
  - 用途：按文件名判断为测试集，用于 RNA 相关残基预测评估
  - 复用状态：blocked；类型：unknown
- `dataset/RNA-117_Test.txt`
  - 能力：evaluation split data
  - 用途：按文件名判断为测试集文本版本，用于 RNA 相关残基预测评估
  - 复用状态：blocked；类型：unknown
- `dataset/YK17-Tst.txt`
  - 能力：evaluation split data
  - 用途：按文件名中的 Tst 判断为测试集；实际内容未核验
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `README.md`
  - 能力：repository overview / method notes
  - 用途：仓库总览与可能的使用说明；正文未读，仅确认存在
  - 复用状态：unknown；类型：unknown
- `dataset/README.md`
  - 能力：dataset documentation
  - 用途：数据组织、格式与划分说明；正文未读，仅确认存在
  - 复用状态：unknown；类型：unknown
- `ESM-NBR-standalone.zip`
  - 能力：standalone method bundle
  - 用途：独立打包资源，可能包含源码、脚本或模型相关文件；未解包核验
  - 复用状态：unknown；类型：unknown
- `suppl-ESM-NBR(12.1).pdf`
  - 能力：supplementary methods / experiments
  - 用途：补充材料，可能包含方法和实验细节；未读正文
  - 复用状态：unknown；类型：unknown

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- 未解包 ESM-NBR-standalone.zip，不能确认其中是否含源码、脚本、模型权重或第三方依赖。
- 未读取 README.md / dataset/README.md / suppl-ESM-NBR(12.1).pdf 正文，方法细节仅能根据文件名与仓库结构推断。
- path presence is not reproduction evidence; 不能把训练/测试文件的存在等同于已验证的数据管线。
- 仓库未发现 LICENSE，代码与数据的可重用边界需要外部核验。

## 仍未知

- ESM-NBR-standalone.zip 的内部内容与许可未知。
- dataset/*.txt 与 *.fasta 是否为同一数据的不同格式或不同版本未知。
- 补充 PDF 是否包含可复用的实验设置、参数或算法描述未知。
- 是否存在未跟踪的大文件、远端资源或 LFS 指向的内容未知。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
