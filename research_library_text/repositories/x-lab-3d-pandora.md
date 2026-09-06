# X-lab-3D/PANDORA

- **仓库：** [https://github.com/X-lab-3D/PANDORA](https://github.com/X-lab-3D/PANDORA)
- **固定 commit：** `618bbb573645bd428697666475a2e47a2e418d01`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 13

## 仓库摘要

这是一个以 peptide-MHC 建模、数据库管理和命令行封装为主的 PANDORA 仓库。冻结快照中可见模型、推理辅助、测试夹具与 CI，但未见独立训练入口或 checkpoint；所有判断均基于静态路径存在，不代表已复现。

## 可复用模块与资源

### datasets

- `test/test_data/PANDORA_database.pkl`
  - 能力：test_fixture_database
  - 用途：测试用序列化数据库夹具，用于回归验证数据库读取与建模流程。
  - 复用状态：partial；类型：unknown
- `test/test_data/PDBs/IMGT_retrieved/IMGT3DFlatFiles/IMGT-1A1O.pdb.gz`
  - 能力：structure_fixture
  - 用途：IMGT 获取的结构测试输入之一，覆盖 pMHC 相关结构。
  - 复用状态：partial；类型：unknown
- `test/test_data/PDBs/pMHCI/1A1O.pdb`
  - 能力：structure_fixture
  - 用途：pMHCI 结构测试输入。
  - 复用状态：partial；类型：unknown
- `test/test_data/PDBs/pMHCII/2NNA.pdb`
  - 能力：structure_fixture
  - 用途：pMHCII 结构测试输入。
  - 复用状态：partial；类型：unknown
- `test/test_data/test_MHCI_wrapper_data.tsv`
  - 能力：wrapper_test_input
  - 用途：MHCI wrapper 的表格化测试输入。
  - 复用状态：partial；类型：unknown

### evaluation

- `test/test_pandora.py`
  - 能力：regression_tests
  - 用途：验证核心建模与接口行为的回归测试。
  - 复用状态：partial；类型：code_entry

### inference

- `PANDORA/Database/Generate_reverse_templates.py`
  - 能力：template_generation_inference
  - 用途：生成 reverse templates，支撑建模前/中间推理步骤。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `PANDORA/PMHC/Model.py`
  - 能力：model_architecture
  - 用途：定义 pMHC 建模核心模型结构。
  - 复用状态：ready_for_review；类型：code_entry
- `PANDORA/Pandora/Pandora.py`
  - 能力：pipeline_orchestration
  - 用途：编排核心建模流程与推理步骤。
  - 复用状态：ready_for_review；类型：code_entry
- `PANDORA/Database/Database.py`
  - 能力：database_schema
  - 用途：管理模板/结构数据库及访问逻辑。
  - 复用状态：ready_for_review；类型：code_entry
- `PANDORA/Database/Generate_reverse_templates.py`
  - 能力：reverse_template_generation
  - 用途：生成 reverse templates；静态库存将其归入推理相关脚本。
  - 复用状态：ready_for_review；类型：code_entry
- `PANDORA/cmd_pandora.py`
  - 能力：command_line_interface
  - 用途：命令行入口。
  - 复用状态：ready_for_review；类型：code_entry
- `PANDORA/Wrapper/Wrapper.py`
  - 能力：wrapper_api
  - 用途：对外封装调用接口。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码、依赖安装或测试，不能证明可复现。
- 未发现独立 training 入口或 checkpoint 文件，训练流程与权重来源不可确认。
- `test/test_data/` 中的结构与序列化夹具存在外部来源/授权不清晰的问题。
- 路径存在不等于真实可用性；大文件与 promisor blobs 也未被解析验证。

## 仍未知

- `PANDORA_database.pkl` 的生成链路、具体内容和再分发许可未能从静态清单确认。
- IMGT/PDB 结构夹具与 `pMHCI`/`pMHCII` 测试文件的完整上游来源与许可边界未明确。
- 仓库是否还依赖未纳入冻结清单的外部数据或私有模型权重，无法仅凭静态库存确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
