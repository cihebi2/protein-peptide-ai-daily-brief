# cryoEM-CNIO/BinderFlow

- **仓库：** [https://github.com/cryoEM-CNIO/BinderFlow](https://github.com/cryoEM-CNIO/BinderFlow)
- **固定 commit：** `d08147adf5a9843410c95da098016f3193393b69`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 26

## 仓库摘要

该仓库是 BinderFlow 的静态流程实现：以 protein binder design 为主，包含调度脚本、结构/序列处理与评分辅助、BFmonitor 监控组件和三个示例输入集；未发现训练入口、checkpoint 或可验证的评测产物。

## 可复用模块与资源

### datasets

- `Examples/Initial_binder_generation/input/PDL1_trimmed.pdb`
  - 能力：初始 binder 生成示例输入
  - 用途：受体结构示例输入
  - 复用状态：unknown；类型：unknown
- `Examples/Initial_binder_generation/input_initial_generation.json`
  - 能力：初始 binder 生成示例配置
  - 用途：示例流程参数与任务定义
  - 复用状态：unknown；类型：config
- `Examples/Partial_diffusion/input/candidate_1.pdb`
  - 能力：partial diffusion 示例输入
  - 用途：候选结构示例输入
  - 复用状态：unknown；类型：unknown
- `Examples/Partial_diffusion/input_partial_diff.json`
  - 能力：partial diffusion 示例配置
  - 用途：partial diffusion 的示例参数
  - 复用状态：unknown；类型：config
- `Examples/Sequence_diversity/input/candidate_1.pdb`
  - 能力：sequence diversity 示例输入
  - 用途：序列多样性示例中的候选结构输入
  - 复用状态：unknown；类型：unknown
- `Examples/Sequence_diversity/input_sequence_diversity.json`
  - 能力：sequence diversity 示例配置
  - 用途：sequence diversity 的示例参数
  - 复用状态：unknown；类型：config

### evaluation

- `binderflow/master_scripts/scoring.sh`
  - 能力：评分阶段
  - 用途：对候选结果打分或筛选
  - 复用状态：partial；类型：code_entry
- `binderflow/scripts/scoring_tools.py`
  - 能力：评分辅助工具
  - 用途：支持评分计算、结果整理或排序
  - 复用状态：partial；类型：code_entry

### inference

- `binderflow.sh`
  - 能力：主流程入口
  - 用途：作为 BinderFlow 的总入口脚本
  - 复用状态：partial；类型：code_entry
- `binderflow/master_scripts/aligning_filtering.sh`
  - 能力：对齐与过滤阶段
  - 用途：组织对齐和过滤步骤
  - 复用状态：partial；类型：code_entry
- `binderflow/master_scripts/rfd.sh`
  - 能力：结构生成阶段
  - 用途：调度生成/扩散类步骤
  - 复用状态：partial；类型：code_entry
- `binderflow/master_scripts/pmpnn.sh`
  - 能力：序列设计阶段
  - 用途：调度序列设计步骤
  - 复用状态：partial；类型：code_entry
- `binderflow/master_scripts/ending.sh`
  - 能力：收尾阶段
  - 用途：完成流程收尾与结果整理
  - 复用状态：partial；类型：code_entry
- `binderflow/slurm_submit/submit_master.sh`
  - 能力：批量提交入口
  - 用途：通过 Slurm 提交主流程任务
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `bfmonitor.py`
  - 能力：流程监控入口
  - 用途：启动或组织 BinderFlow 监控逻辑
  - 复用状态：partial；类型：code_entry
- `BFmonitor/utils/generic_utils.py`
  - 能力：通用辅助函数
  - 用途：提供通用工具函数
  - 复用状态：partial；类型：code_entry
- `BFmonitor/utils/plotting_utils.py`
  - 能力：结果可视化辅助
  - 用途：绘图与结果展示辅助
  - 复用状态：partial；类型：code_entry
- `BFmonitor/utils/hits_utils.py`
  - 能力：命中汇总与统计
  - 用途：整理、统计和分析候选命中结果
  - 复用状态：partial；类型：code_entry
- `binderflow/scripts/input_json_reader.py`
  - 能力：输入 JSON 解析
  - 用途：读取运行配置或示例输入 JSON
  - 复用状态：partial；类型：code_entry
- `binderflow/scripts/json_variable_generation.py`
  - 能力：参数变量生成
  - 用途：把配置转换为运行时变量
  - 复用状态：partial；类型：code_entry
- `binderflow/scripts/biopython_align.py`
  - 能力：结构/序列比对辅助
  - 用途：进行比对相关辅助处理
  - 复用状态：partial；类型：code_entry
- `binderflow/scripts/superimpose.py`
  - 能力：结构叠合辅助
  - 用途：执行结构 superimpose 辅助步骤
  - 复用状态：partial；类型：code_entry
- `binderflow/scripts/fixing_residues.py`
  - 能力：残基修正
  - 用途：修正或补全残基相关信息
  - 复用状态：partial；类型：code_entry
- `binderflow/scripts/split_fasta.py`
  - 能力：FASTA 拆分
  - 用途：拆分序列文件以供后续步骤使用
  - 复用状态：partial；类型：code_entry
- `config.sh`
  - 能力：环境配置
  - 用途：提供运行环境变量或默认配置
  - 复用状态：partial；类型：config
- `install_binderflow.sh`
  - 能力：安装部署脚本
  - 用途：自动化安装或部署 BinderFlow
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清单审查，未安装依赖、未运行代码、未执行测试
- 仓库存在 .pyc、png 等生成物，但未将其视为可复用源资产
- 示例 PDB/JSON 仅见路径与文件名，来源、授权和是否可再分发未核验
- 部分脚本职责仅可根据路径名推断，未读取文件内容确认

## 仍未知

- Examples/* 示例数据的来源、授权边界与是否覆盖到 repo 总许可不明确
- binderflow.sh 与 master_scripts 是否依赖外部二进制/下载模型未核验
- BFmonitor 与各 helper 脚本的内部实现细节未读取，功能边界仍有不确定性

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
