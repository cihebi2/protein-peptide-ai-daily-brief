# abdullah30/Chloroplast-Genome-Analysis-Suite-CGAS

- **仓库：** [https://github.com/abdullah30/Chloroplast-Genome-Analysis-Suite-CGAS](https://github.com/abdullah30/Chloroplast-Genome-Analysis-Suite-CGAS)
- **固定 commit：** `52b82e60f281514ea91fb0ac3e02346a25d02eea`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 10

## 仓库摘要

该仓库是 CGAS 的 Python chloroplast genome analysis pipeline：静态可见 14 个分模块实现、CLI、安装/依赖清单和若干 FASTA/GenBank 示例数据；未见训练入口、checkpoint 或模型权重。MIT 许可文件存在，但 `test_files` 中数据的来源与独立许可未能从清单确认。

## 可复用模块与资源

### datasets

- `test_files/fasta_files/Erigeron compositus.fasta`
  - 能力：sample FASTA genome inputs
  - 用途：代表性 FASTA 示例/测试输入；同目录还有多份 `.fasta` 文件
  - 复用状态：partial；类型：unknown
- `test_files/gb_files/Erigeron compositus.gb`
  - 能力：sample GenBank genome inputs
  - 用途：代表性 GenBank 示例/测试输入；同目录还有多份 `.gb` 文件
  - 复用状态：partial；类型：unknown
- `test_files/annotations/reference/Buxus_sinica.gb`
  - 能力：reference annotation example
  - 用途：注释/对照用参考 GenBank 文件
  - 复用状态：partial；类型：unknown
- `test_files/annotations/targets/SRR18086674_1.fasta`
  - 能力：target read inputs for annotation tests
  - 用途：成对 target FASTA 测试输入之一，用于注释相关验证
  - 复用状态：partial；类型：unknown
- `test_files/normalization/Erigeron compositus.gb`
  - 能力：normalization example inputs
  - 用途：归一化/标准化步骤的示例输入集合
  - 复用状态：partial；类型：unknown

### evaluation

- `test_files/TEST_README.md`
  - 能力：manual validation instructions
  - 用途：说明测试文件布局与验证用输入；未见自动化 CI/测试框架
  - 复用状态：partial；类型：unknown

### inference

- `cgas/cli.py`
  - 能力：analysis pipeline execution
  - 用途：命令行解析与流水线调度；静态上未见模型推理框架
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `cgas/cgas_module1.py`
  - 能力：chloroplast genome analysis pipeline core
  - 用途：代表 `cgas/cgas_module1.py`–`cgas/cgas_module14.py` 的分阶段分析实现，可复用其流程拆分与序列/注释处理逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `setup.py`
  - 能力：packaging and dependency specification
  - 用途：安装与依赖声明，便于复用该工具链的打包边界
  - 复用状态：ready_for_review；类型：code_entry
- `README.md`
  - 能力：usage and installation documentation
  - 用途：安装、快速开始与模块说明，可帮助复用运行流程
  - 复用状态：ready_for_review；类型：unknown

## 使用限制

- 仅做静态盘点，未运行代码、未安装依赖、未执行测试。
- 未发现训练入口、模型权重或 checkpoint，因此不存在可验证的训练/恢复流程。
- `test_files` 中 FASTA/GenBank/targets 数据的外部来源、再许可与可再分发条件未确认。
- 历史脚本目录 `Documents/Old scripts` 与主包并存，是否为弃用实现或与现行代码重复无法仅凭静态清单确认。

## 仍未知

- `test_files` 内样本是否为项目自制、第三方整理或直接引入的公共数据未确认。
- `cgas/cgas_module*.py` 各阶段与 `README`/文档中的功能对应关系未运行验证。
- `Documents/Old scripts/cgas_module13.py` 和 `cgas/cgas_module13.py` 等历史/现行实现差异未知。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
