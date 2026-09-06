# MolecularAI/REINVENT4

- **仓库：** [https://github.com/MolecularAI/REINVENT4](https://github.com/MolecularAI/REINVENT4)
- **固定 commit：** `43094673bf0babf858814df458e42c90d7f0cf94`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 16

## 仓库摘要

REINVENT4 提供 SMILES/RNN/Transformer 为核心的分子生成框架，并扩展到 LIBINVENT、LINKINVENT、Mol2Mol、PepINVENT、RL/TL、打分变换和外部工具插件；静态清单未见可执行 checkpoint，训练与复现只能确认编排与配置，不能证明实际跑通。

## 可复用模块与资源

### datasets

- `reinvent/chemistry/library_design/reaction_definitions/data/reaction_definitions.csv`
  - 能力：反应定义表
  - 用途：库设计与反应规则的静态定义
  - 复用状态：partial；类型：unknown
- `contrib/tutorials/NaviDiv/examples/app/sample_molecules.csv`
  - 能力：示例分子集
  - 用途：NaviDiv 示例应用的输入样本
  - 复用状态：partial；类型：unknown
- `notebooks/data/tnks2.csv`
  - 能力：Notebook 示例数据
  - 用途：Notebook 演示与教程输入
  - 复用状态：partial；类型：unknown
- `reinvent_plugins/components/SAScore/fpscores.pkl.gz`
  - 能力：SA score 指纹表
  - 用途：SAScore 计算所需的查表资源
  - 复用状态：blocked；类型：unknown
- `contrib/reinvent_plugins/components/NIBRSubstructureFilters/catalog.pkl`
  - 能力：NIBR 子结构过滤目录
  - 用途：NIBR 过滤器的目录/查表资源
  - 复用状态：blocked；类型：unknown
- `contrib/reinvent_plugins/components/Lilly/pains_scores.csv`
  - 能力：Lilly PAINS 资源
  - 用途：Lilly/PAINS 相关过滤或打分资源
  - 复用状态：blocked；类型：unknown

### evaluation

- `reinvent/runmodes/utils/evaluate.py`
  - 能力：score / evaluation 管线
  - 用途：计算分数、汇总结果并输出评估信息
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `reinvent/models/model_factory/sample_batch.py`
  - 能力：批量采样 / 推理
  - 用途：批量生成候选分子/肽/连接子，并走采样执行器
  - 复用状态：ready_for_review；类型：code_entry
- `contrib/tutorials/NaviDiv/examples/app/run_demo.py`
  - 能力：教程级推理演示
  - 用途：演示端到端推理、应用启动或路线生成示例
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `reinvent/models/reinvent/models/rnn.py`
  - 能力：核心生成模型与 paired seq2seq 结构
  - 用途：实现 SMILES、linker、molecule-to-molecule 和 peptide 的条件生成骨架
  - 复用状态：ready_for_review；类型：code_entry
- `reinvent/datapipeline/preprocess.py`
  - 能力：化学预处理、标准化与反应过滤
  - 用途：输入清洗、SMILES/token 处理、标准化、反应与片段筛选
  - 复用状态：ready_for_review；类型：code_entry
- `reinvent/scoring/compute_scores.py`
  - 能力：奖励/打分变换与 RL 记忆
  - 用途：计算 score、做 reward shaping、diversity filter、intrinsic penalty 和记忆缓存
  - 复用状态：ready_for_review；类型：code_entry
- `reinvent_plugins/components/OpenEye/comp_rocs.py`
  - 能力：外部工具插件适配
  - 用途：把 docking、外部预测、自动合成路线等系统接入 REINVENT 工作流
  - 复用状态：partial；类型：code_entry

### training

- `reinvent/runmodes/TL/run_transfer_learning.py`
  - 能力：transfer learning 训练编排
  - 用途：基于配置驱动的 TL 调优流程；静态上仅能确认编排，不证明实际训练已运行
  - 复用状态：partial；类型：code_entry
- `reinvent/runmodes/RL/run_staged_learning.py`
  - 能力：staged RL 训练编排
  - 用途：分阶段 reinforcement learning / fine-tuning 的流程编排；静态上仅能确认配置与入口线索
  - 复用状态：partial；类型：code_entry
- `reinvent/runmodes/create_model/reinvent.toml`
  - 能力：模型初始化/创建配置
  - 用途：定义 prior/model 创建参数；更像 recipe 而非已验证训练产物
  - 复用状态：partial；类型：config

## 使用限制

- 仅做静态清单审查，未执行仓库代码、未跑测试、未验证任何产物可复现性。
- dependencies 未安装，外部工具链（例如 OpenEye、DockStream、Chemprop、Icolos、MAIZE、SynthSense 等）运行与许可状态未核实。
- 大量 `.sdf` / `.pkl` / `.map` / dock 相关大文件可能是教程产物或外部生成资源，静态 presence 不代表来源、完整性或可再分发权利。
- 冻结 inventory 中未识别出任何 checkpoint；训练入口更多表现为配置/编排文件，不能据此声称已完成训练。
- 部分第三方 lookup 数据（如 SAScore、NIBR、Lilly 相关资源）缺少单独许可证据，直接复用存在边界不明风险。

## 仍未知

- `contrib/tutorials/maize/` 中的大量 docking pose、map、log 文件的生成链路与上游许可未在冻结清单中明确。
- `reinvent_plugins/components/OpenEye/*`、`comp_dockstream.py`、`comp_chemprop.py`、`comp_icolos.py`、`comp_maize.py`、`comp_synthsense.py` 均依赖外部生态；其可运行性与许可证需要额外确认。
- `reinvent_plugins/components/SAScore/fpscores.pkl.gz`、`contrib/reinvent_plugins/components/NIBRSubstructureFilters/catalog.pkl`、`contrib/reinvent_plugins/components/Lilly/pains_scores.csv` 的上游来源与可再分发条件未被本次静态审查解析。
- 仓库虽含多套 TL/RL/采样配置，但没有冻结 checkpoint，无法从静态清单判断实际训练结果或性能。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
