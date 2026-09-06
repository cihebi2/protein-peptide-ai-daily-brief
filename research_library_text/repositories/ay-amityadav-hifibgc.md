# ay-amityadav/HiFiBGC

- **仓库：** [https://github.com/ay-amityadav/HiFiBGC](https://github.com/ay-amityadav/HiFiBGC)
- **固定 commit：** `ac223af337cf62589849f2f6662e01c9d7c6e3dd`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 16

## 仓库摘要

静态清单显示该仓库主要实现 HiFiBGC 的 Snakemake/CLI 工作流：包含配置、多个 conda 环境、结果汇总与可视化脚本、CI，以及 1 个小型 FASTQ 测试样例；未见训练入口、模型权重、评测基准数据或可直接复现论文结果的执行证据。仓库根目录未发现标准 LICENSE，只有 `hifibgc.LICENSE` 文件名可见。

## 可复用模块与资源

### datasets

- `hifibgc/test_data/test_data_sampled.fastq`
  - 能力：smoke-test input fixture
  - 用途：小型 FASTQ 示例输入，用于测试或演示流程
  - 复用状态：blocked；类型：unknown

### evaluation

- `hifibgc/workflow/scripts/prepare_input_for_upsetplot.py`
  - 能力：comparison plot preparation
  - 用途：整理比较结果以便做 UpSet 评估图
  - 复用状态：unknown；类型：code_entry
- `hifibgc/workflow/scripts/upsetplot.R`
  - 能力：visual evaluation
  - 用途：生成 UpSet 图形用于结果对比/评估
  - 复用状态：unknown；类型：code_entry
- `.github/workflows/hifibgc.yml`
  - 能力：test automation
  - 用途：CI 可作为静态测试/冒烟检查入口
  - 复用状态：unknown；类型：config

### inference

- `hifibgc/workflow/hifibgc.smk`
  - 能力：pipeline inference
  - 用途：运行 HiFiBGC 主流程以产生检测结果
  - 复用状态：unknown；类型：unknown
- `hifibgc/workflow/scripts/generate_final_outputs.py`
  - 能力：result post-processing
  - 用途：将中间结果整理为最终输出
  - 复用状态：unknown；类型：code_entry
- `hifibgc/workflow/scripts/prepare_input_for_bigscape.py`
  - 能力：downstream analysis preparation
  - 用途：为后续 BigScape 分析准备输入
  - 复用状态：unknown；类型：code_entry

### reusable_assets

- `hifibgc/config/config.yaml`
  - 能力：pipeline configuration
  - 用途：控制工作流参数与默认配置
  - 复用状态：unknown；类型：config
- `setup.py`
  - 能力：dependencies and packaging
  - 用途：声明 Python 打包与依赖
  - 复用状态：unknown；类型：code_entry
- `hifibgc/workflow/envs/antismash_v7.yml`
  - 能力：runtime environment specs
  - 用途：Snakemake 运行环境之一；同目录还有 bigscape/canu/flye/hifiasm_meta/mapping/r_complexupset 等环境定义
  - 复用状态：unknown；类型：config
- `hifibgc/workflow/hifibgc.smk`
  - 能力：workflow orchestration
  - 用途：主 Snakemake 管线，承载检测与后处理步骤
  - 复用状态：unknown；类型：unknown
- `hifibgc/workflow/scripts/generate_final_outputs.py`
  - 能力：final output generation
  - 用途：汇总并生成最终输出文件
  - 复用状态：unknown；类型：code_entry
- `hifibgc/workflow/scripts/prepare_input_for_bigscape.py`
  - 能力：downstream preprocessing
  - 用途：为 BigScape 生成输入，属于下游分析准备
  - 复用状态：unknown；类型：code_entry
- `hifibgc/workflow/scripts/prepare_input_for_upsetplot.py`
  - 能力：evaluation input preparation
  - 用途：为 UpSet 可视化/对比分析整理输入
  - 复用状态：unknown；类型：code_entry
- `hifibgc/workflow/scripts/upsetplot.R`
  - 能力：evaluation visualization
  - 用途：生成 UpSet 结果图或对比图
  - 复用状态：unknown；类型：code_entry
- `.github/workflows/hifibgc.yml`
  - 能力：CI and smoke testing
  - 用途：自动化测试/持续集成入口
  - 复用状态：unknown；类型：config

## 使用限制

- 仅做静态清单审查；未执行代码、未安装依赖、未运行测试。
- 路径存在不等于功能可用；Snakemake workflow 是否能成功跑通未被验证。
- 仓库未见训练入口、训练模块或 checkpoint 文件，无法支持训练复现判断。
- 根目录未发现标准 LICENSE，代码与数据的可直接重用权限未被静态确认。

## 仍未知

- `hifibgc.LICENSE` 的具体条款与适用范围未知。
- `hifibgc/test_data/test_data_sampled.fastq` 的真实来源、脱敏状态与许可未知。
- workflow 运行时是否下载外部数据库/工具，以及这些外部资源的许可边界未知。
- `generate_final_outputs.py`、`prepare_input_for_bigscape.py` 等脚本是否仅后处理还是包含核心算法，无法仅凭路径确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
