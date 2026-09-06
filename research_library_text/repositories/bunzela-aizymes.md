# bunzela/AIzymes

- **仓库：** [https://github.com/bunzela/AIzymes](https://github.com/bunzela/AIzymes)
- **固定 commit：** `52176ffab5d00b54f76141de8721949a28fe674c`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 20

## 仓库摘要

仓库是一个面向 enzyme design 的模块化平台，含 Rosetta、ProteinMPNN、AlphaFold3、Chai1、ESMfold 等设计/验证脚本，以及输入结构、约束文件、MD 结果和最终筛选表；静态审查未见训练入口或 checkpoint，代码许可为 MIT，但数据与结果文件的独立许可边界未被确认。

## 可复用模块与资源

### datasets

- `input_files/1ohp.pdb`
  - 能力：protein target input
  - 用途：设计目标蛋白结构输入
  - 复用状态：partial；类型：unknown
- `input_files/K3_xray.pdb`
  - 能力：additional protein target input
  - 用途：另一组蛋白结构输入/对照目标
  - 复用状态：partial；类型：unknown
- `input_files/5TS.params`
  - 能力：ligand and constraint bundle
  - 用途：小分子参数、配体拓扑与 Rosetta 约束的组合输入
  - 复用状态：partial；类型：unknown
- `input_files/Oxidized_HisHisLigated_b-heme.frcmod`
  - 能力：heme force-field resources
  - 用途：辅因子/金属中心参数与力场资源
  - 复用状态：partial；类型：unknown
- `input_files/HEM_enzdes.cst`
  - 能力：constraint file
  - 用途：Rosetta 酶设计约束输入
  - 复用状态：partial；类型：unknown

### evaluation

- `archive/001_Redesign_KSI_resi99/MD_analysis/MD_analysis.ipynb`
  - 能力：post hoc MD analysis
  - 用途：轨迹/结构稳定性等后验分析
  - 复用状态：partial；类型：unknown
- `archive/001_Redesign_KSI_resi99/MD_analysis/all_scores.csv`
  - 能力：candidate scoring table
  - 用途：候选综合打分与排序汇总
  - 复用状态：partial；类型：unknown
- `archive/001_Redesign_KSI_resi99/MD_analysis/MD_results.csv`
  - 能力：MD result tables
  - 用途：MD 指标结果汇总
  - 复用状态：partial；类型：unknown
- `archive/001_Redesign_KSI_resi99/MD_analysis/final_selection/selection_criteria.txt`
  - 能力：selection criteria
  - 用途：最终候选筛选规则文本
  - 复用状态：ready_for_review；类型：unknown
- `archive/001_Redesign_KSI_resi99/MD_analysis/final_selection/KSI_99_7058_ins-KSI_99_7427_ins-KSI_99_8610_ins-KSI_99_8941_ins-KSI_99_9867_ins-alignment.pdf`
  - 能力：structure alignment figure
  - 用途：最终候选结构对比图
  - 复用状态：partial；类型：unknown

### inference

- `src/docs/generate_documentation.ipynb`
  - 能力：documentation-generation notebook
  - 用途：交互式示例/文档生成线索；静态上可视作运行入口之一
  - 复用状态：partial；类型：unknown
- `example_notebooks/Example_KSI.ipynb`
  - 能力：example workflow notebook
  - 用途：KSI 设计流程的示例式调用与结果展示
  - 复用状态：partial；类型：unknown

### reusable_assets

- `src/aizymes/main_design_001.py`
  - 能力：design orchestration
  - 用途：主流程编排，串联设计、打分与筛选步骤
  - 复用状态：ready_for_review；类型：code_entry
- `src/aizymes/design_RosettaDesign_001.py`
  - 能力：Rosetta design
  - 用途：基于 Rosetta 的设计候选生成
  - 复用状态：ready_for_review；类型：code_entry
- `src/aizymes/design_RosettaRelax_001.py`
  - 能力：Rosetta relax
  - 用途：Rosetta 松弛/结构优化步骤
  - 复用状态：ready_for_review；类型：code_entry
- `src/aizymes/design_MPNN_001.py`
  - 能力：sequence redesign
  - 用途：ProteinMPNN 序列重设计接口
  - 复用状态：partial；类型：code_entry
- `src/aizymes/design_AlphaFold3_001.py`
  - 能力：structure prediction wrapper
  - 用途：AlphaFold3 结构预测/验证调用封装
  - 复用状态：partial；类型：code_entry
- `src/aizymes/scoring_efields_001.py`
  - 能力：scoring
  - 用途：电场/物理量评分模块
  - 复用状态：ready_for_review；类型：code_entry
- `src/aizymes/setup_system_001.py`
  - 能力：system setup
  - 用途：分子系统准备与输入构建
  - 复用状态：ready_for_review；类型：code_entry
- `environment.yml`
  - 能力：runtime environment
  - 用途：Python 依赖与环境固定
  - 复用状态：partial；类型：config

## 使用限制

- 仅做静态审查，未执行仓库代码、未安装依赖、未运行测试。
- 冻结清单中大量数据/结果文件的来源与再分发许可不明。
- 未发现可识别的训练入口或模型 checkpoint，不能证明可复现实验训练。
- 外部工具/模型包装是否依赖额外权重、授权或网络服务，静态上无法确认。

## 仍未知

- `input_files/` 中若干 PDB、参数和约束文件的原始来源未确认。
- `archive/` 下的 MD/selection 结果是项目生成物还是外部导入物，静态上无法区分。
- 未见 `.pt`、`.pth`、`.ckpt` 等模型 checkpoint。
- `environment.yml` 仅能说明依赖声明，不能证明环境可直接解析成功。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
