# chatmed/prompt-to-pill

- **仓库：** [https://github.com/chatmed/prompt-to-pill](https://github.com/chatmed/prompt-to-pill)
- **固定 commit：** `817e177e892f67e0089071321c09e9e360afb4d7`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 23

## 仓库摘要

静态清单显示该仓库是一个多代理药物发现与临床模拟流水线，覆盖分子生成、优化、对接、ADMET、试验预测与评估；未见训练代码、模型权重或检查点，且未发现许可证文件。

## 可复用模块与资源

### datasets

- `diabetes_patients_final.xml`
  - 能力：clinical_input_dataset
  - 用途：可能用于患者匹配或临床模拟；仅凭文件名无法确认来源、规模与授权。
  - 复用状态：blocked；类型：unknown

### evaluation

- `evaluate_docking.py`
  - 能力：docking_evaluation
  - 用途：评估对接输出。
  - 复用状态：blocked；类型：code_entry

### inference

- `Prompt_to_pill.py`
  - 能力：pipeline_orchestrator
  - 用途：总入口，组织多代理推理与任务编排。
  - 复用状态：blocked；类型：code_entry
- `docking_mcp_server.py`
  - 能力：docking_service
  - 用途：对接推理/打分服务。
  - 复用状态：blocked；类型：code_entry
- `druggen_mcp_server.py`
  - 能力：molecule_generation
  - 用途：分子生成推理服务。
  - 复用状态：blocked；类型：code_entry
- `mol_opt_mcp_server.py`
  - 能力：molecule_optimization
  - 用途：分子优化推理服务。
  - 复用状态：blocked；类型：code_entry
- `admet_prediction_mcp_server.py`
  - 能力：ADMET_prediction
  - 用途：ADMET/性质推理服务。
  - 复用状态：blocked；类型：code_entry
- `name2smiles_mcp_server.py`
  - 能力：molecule_normalization
  - 用途：名称到SMILES 的转换与规范化推理服务。
  - 复用状态：blocked；类型：code_entry
- `patient_matching_mcp_server.py`
  - 能力：patient_matching
  - 用途：患者匹配推理服务。
  - 复用状态：blocked；类型：code_entry
- `trialgen_mcp_server.py`
  - 能力：trial_generation
  - 用途：试验生成推理服务。
  - 复用状态：blocked；类型：code_entry
- `trialpred_mcp_server.py`
  - 能力：trial_prediction
  - 用途：试验预测推理服务。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `Prompt_to_pill.py`
  - 能力：pipeline_orchestrator
  - 用途：主工作流入口，串联分子生成、对接、优化和临床模拟相关子模块。
  - 复用状态：blocked；类型：code_entry
- `docking_module.py`
  - 能力：docking
  - 用途：对接相关核心逻辑模块，支撑候选打分/筛选。
  - 复用状态：blocked；类型：code_entry
- `docking_mcp_server.py`
  - 能力：docking_service
  - 用途：对接服务封装，提供候选对接能力。
  - 复用状态：blocked；类型：code_entry
- `druggen_mcp_server.py`
  - 能力：molecule_generation
  - 用途：候选分子生成服务。
  - 复用状态：blocked；类型：code_entry
- `mol_opt_mcp_server.py`
  - 能力：molecule_optimization
  - 用途：分子优化服务，用于改进候选属性。
  - 复用状态：blocked；类型：code_entry
- `admet_prediction_mcp_server.py`
  - 能力：ADMET_prediction
  - 用途：ADMET/性质预测服务，支撑候选可开发性评估。
  - 复用状态：blocked；类型：code_entry
- `name2smiles_mcp_server.py`
  - 能力：molecule_normalization
  - 用途：名称到SMILES 的标准化/转换服务。
  - 复用状态：blocked；类型：code_entry
- `patient_matching_mcp_server.py`
  - 能力：patient_matching
  - 用途：患者匹配服务，支撑临床模拟与试验相关流程。
  - 复用状态：blocked；类型：code_entry
- `trialgen_mcp_server.py`
  - 能力：trial_generation
  - 用途：试验生成服务，面向临床模拟/试验设计。
  - 复用状态：blocked；类型：code_entry
- `trialpred_mcp_server.py`
  - 能力：trial_prediction
  - 用途：试验预测服务，辅助临床模拟决策。
  - 复用状态：blocked；类型：code_entry
- `evaluate_docking.py`
  - 能力：docking_evaluation
  - 用途：对接结果评估脚本，是仓库中唯一明确的评估入口。
  - 复用状态：blocked；类型：code_entry
- `diabetes_patients_final.xml`
  - 能力：clinical_input_dataset
  - 用途：看起来像糖尿病患者相关 XML 输入/数据文件；静态清单无法确认其是否为正式数据集或样例数据。
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态清单审查，未执行任何代码。
- 依赖未安装，无法验证运行时行为。
- 未运行测试，无法证明可复现性。
- 未见训练入口、训练模块或检查点文件。
- clone depth=1，且大于 5MiB 的 blob 可能未完全展开。

## 仍未知

- diabetes_patients_final.xml 是否为正式数据集、示例数据或临床模拟输入，静态证据不足。
- README.md 可能包含额外工作流说明，但未读取其正文。
- 是否存在被 promisor/LFS 隐藏的权重或数据，当前无法排除。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
