# aporollo-lab/SPPIDER-seq

- **仓库：** [https://github.com/aporollo-lab/SPPIDER-seq](https://github.com/aporollo-lab/SPPIDER-seq)
- **固定 commit：** `5f8c0b94d1c0c02e51e631b5e37fb970ceb99fb8`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 18

## 仓库摘要

该仓库是一个基于序列的蛋白-蛋白相互作用位点预测工具包，包含主推理脚本、若干序列处理/分析CLI、notebook 示例和成对 FASTA 示例输入；冻结清单未见训练入口、评测脚本或 checkpoint，代码许可可确认但数据与输出的独立许可未见。

## 可复用模块与资源

### datasets

- `examples/example1_input-partner.fasta`
  - 能力：example_input_pairs
  - 用途：示例 1 的 partner 输入序列
  - 复用状态：partial；类型：unknown
- `examples/example1_input-query.fasta`
  - 能力：example_input_pairs
  - 用途：示例 1 的 query 输入序列
  - 复用状态：partial；类型：unknown
- `examples/example2_input-partner.fasta`
  - 能力：example_input_pairs
  - 用途：示例 2 的 partner 输入序列
  - 复用状态：partial；类型：unknown
- `examples/example2_input-query.fasta`
  - 能力：example_input_pairs
  - 用途：示例 2 的 query 输入序列
  - 复用状态：partial；类型：unknown

### evaluation

- `examples/example1_output.zip`
  - 能力：sample_output_bundle
  - 用途：示例 1 的输出包，可作为结果格式参考
  - 复用状态：partial；类型：unknown
- `examples/example2_output.zip`
  - 能力：sample_output_bundle
  - 用途：示例 2 的输出包，可作为结果格式参考
  - 复用状态：partial；类型：unknown

### inference

- `cli/sppider_seq.py`
  - 能力：prediction_inference
  - 用途：序列到 PPI 位点预测的推理入口
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `cli/sppider_seq.py`
  - 能力：main_prediction_cli
  - 用途：主预测/推理入口，面向 SPPIDER-seq 结果生成
  - 复用状态：ready_for_review；类型：code_entry
- `cli/parse_sppider_seq.py`
  - 能力：result_parser
  - 用途：推理结果解析与后处理
  - 复用状态：ready_for_review；类型：code_entry
- `cli/alanine_scanning.py`
  - 能力：alanine_scanning_analysis
  - 用途：alanine scanning 分析工具
  - 复用状态：ready_for_review；类型：code_entry
- `cli/alanine_scanning2ppi_averages.py`
  - 能力：alanine_scanning_aggregation
  - 用途：alanine scanning 到 PPI average 的汇总/转换工具
  - 复用状态：ready_for_review；类型：code_entry
- `cli/amplify_sequence_signal.py`
  - 能力：sequence_signal_amplification
  - 用途：序列信号放大/处理工具
  - 复用状态：ready_for_review；类型：code_entry
- `cli/scramble_fasta.py`
  - 能力：fasta_scrambling
  - 用途：FASTA 序列打乱/扰动工具
  - 复用状态：ready_for_review；类型：code_entry
- `notebooks/sppider_seq.ipynb`
  - 能力：workflow_notebook_demo
  - 用途：主流程 notebook 示例
  - 复用状态：partial；类型：unknown
- `notebooks/alanine_scanning.ipynb`
  - 能力：workflow_notebook_demo
  - 用途：alanine scanning notebook 示例
  - 复用状态：partial；类型：unknown
- `notebooks/amplify_sequence_signal.ipynb`
  - 能力：workflow_notebook_demo
  - 用途：sequence signal amplification notebook 示例
  - 复用状态：partial；类型：unknown
- `notebooks/scramble_fasta.ipynb`
  - 能力：workflow_notebook_demo
  - 用途：FASTA scrambling notebook 示例
  - 复用状态：partial；类型：unknown
- `docs/figures/workflow.png`
  - 能力：workflow_diagram
  - 用途：流程图/文档插图
  - 复用状态：ready_for_review；类型：unknown

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试
- 未见 training_entrypoint、training_module、evaluation 脚本或 checkpoint 文件
- examples/example*_output.zip 只能证明有示例输出包，不能证明正式评测流程
- notebook 与 CLI 的具体实现内容未读入，功能判断主要依据文件名与清单

## 仍未知

- example FASTA 是否为合成数据、真实蛋白序列或受限数据不明
- example 输出包是否与 CLI 完全对应、是否覆盖全部模式不明
- 仓库是否存在未纳入清单的外部大文件/权重或未初始化子模块不明
- scripts/ notebooks 的内部算法细节与参数约束未核验

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
