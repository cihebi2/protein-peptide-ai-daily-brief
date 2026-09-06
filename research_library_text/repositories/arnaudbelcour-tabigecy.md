# ArnaudBelcour/tabigecy

- **仓库：** [https://github.com/ArnaudBelcour/tabigecy](https://github.com/ArnaudBelcour/tabigecy)
- **固定 commit：** `e45c85328425a07a3d39b45a44d042d7f6826110`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 14

## 仓库摘要

该仓库是一个静态冻结的 Nextflow 分析流程仓库，包含主工作流、配置、教程/测试输入与若干说明图；未见训练入口或 checkpoint。代码许可明确为 GPL-3.0，但 bundled 数据与图片未见独立授权，数据边界需另行核实。

## 可复用模块与资源

### datasets

- `tutorials/input/tutorial_example_abundance.csv`
  - 能力：tutorial example input data
  - 用途：教程示例的 abundance 输入表
  - 复用状态：ready_for_review；类型：unknown
- `tutorials/input/tutorial_example_affiliations.tsv`
  - 能力：tutorial example input data
  - 用途：教程示例的 taxonomic affiliations 输入表
  - 复用状态：ready_for_review；类型：unknown
- `tutorials/input/group_sample.tsv`
  - 能力：tutorial example input data
  - 用途：教程示例的分组表
  - 复用状态：ready_for_review；类型：unknown
- `test/esmecata_test_database.zip`
  - 能力：bundled test database
  - 用途：测试用数据库/参考内容压缩包
  - 复用状态：partial；类型：unknown

### evaluation

- `test/test_abundance_file.tsv`
  - 能力：test fixture
  - 用途：测试输入表，用于验证流程处理 abundance 数据
  - 复用状态：ready_for_review；类型：unknown
- `test/test_taxonomic_affiliations.tsv`
  - 能力：test fixture
  - 用途：测试输入表，用于验证流程处理 taxonomic affiliations 数据
  - 复用状态：ready_for_review；类型：unknown
- `test/group_file.tsv`
  - 能力：test fixture
  - 用途：测试分组表，用于流程验证
  - 复用状态：ready_for_review；类型：unknown
- `test/template_background.png`
  - 能力：visual test fixture
  - 用途：测试背景模板图像，用于图形/模板相关验证
  - 复用状态：partial；类型：unknown
- `test/bigecyhmm_test_custom_db/carbon_cycle_od.tsv`
  - 能力：custom-db test fixture
  - 用途：自定义数据库测试中的结果或对照表
  - 复用状态：partial；类型：unknown

### inference

- `tabigecy.nf`
  - 能力：pipeline entrypoint
  - 用途：主 Nextflow 工作流，承载分析/推理流程
  - 复用状态：ready_for_review；类型：unknown

### reusable_assets

- `pictures/workflow_bigecyhmm.svg`
  - 能力：workflow documentation / diagram
  - 用途：说明主流程结构，便于理解和复用工作流图示
  - 复用状态：ready_for_review；类型：unknown
- `pictures/doi_tabigecy.svg`
  - 能力：workflow documentation / diagram
  - 用途：说明项目/论文相关流程或主题图示
  - 复用状态：ready_for_review；类型：unknown
- `nextflow.config`
  - 能力：pipeline runtime configuration
  - 用途：定义 Nextflow 运行参数与默认配置
  - 复用状态：partial；类型：config
- `.github/workflows/mirror_to_gitlab.yml`
  - 能力：CI automation
  - 用途：仓库镜像同步自动化，不属于核心分析逻辑
  - 复用状态：partial；类型：config

## 使用限制

- 仅做静态清单审查，未安装依赖、未运行 Nextflow、未执行测试。
- 路径存在不等于可复现或可运行；冻结清单无法证明实际输出。
- bundled 数据/数据库 ZIP 的来源与再授权条件未在清单中确认。

## 仍未知

- 未检出独立 training entrypoint/module，因此无法确认是否存在训练流程。
- 未检出 checkpoint 文件，因此无法确认是否支持模型恢复或权重分发。
- `test/esmecata_test_database.zip` 的内容与授权边界不明。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
