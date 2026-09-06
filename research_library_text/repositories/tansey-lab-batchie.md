# tansey-lab/batchie

- **仓库：** [https://github.com/tansey-lab/batchie](https://github.com/tansey-lab/batchie)
- **固定 commit：** `fb2e649aaeeed93f214a0fa5b973e5cb45489e96`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 28

## 仓库摘要

该仓库实现了面向组合药物筛选的 Bayesian active learning 平台，包含稀疏组合模型、评分/选板策略、训练与评估 CLI 以及 Nextflow 工作流；代码为 MIT，但测试数据与 HDF5 快照的独立许可和生成来源未被静态确认。

## 可复用模块与资源

### checkpoints

- `nextflow/tests/data/distance_matrix.h5`
  - 能力：距离矩阵快照
  - 用途：距离矩阵状态快照，供测试或模拟。
  - 复用状态：partial；类型：model_weight
- `nextflow/tests/data/masked_screen.h5`
  - 能力：遮罩后的 screen 快照
  - 用途：mask 处理后的 screen 数据快照。
  - 复用状态：partial；类型：model_weight
- `nextflow/tests/data/model_evaluation.h5`
  - 能力：模型评估状态快照
  - 用途：评估结果或中间状态快照。
  - 复用状态：partial；类型：model_weight
- `nextflow/tests/data/scores.h5`
  - 能力：候选分数快照
  - 用途：候选 scoring 结果快照。
  - 复用状态：partial；类型：model_weight
- `nextflow/tests/data/thetas.h5`
  - 能力：theta 参数快照
  - 用途：模型参数/theta 的状态快照。
  - 复用状态：partial；类型：model_weight
- `nextflow/tests/data/unmasked_screen.h5`
  - 能力：未遮罩 screen 快照
  - 用途：未 mask 的 screen 数据快照。
  - 复用状态：partial；类型：model_weight

### datasets

- `nextflow/tests/data/batch_selection.json`
  - 能力：batch 选择测试夹具
  - 用途：记录下一轮 batch 选择状态，用于测试和模拟。
  - 复用状态：partial；类型：config
- `nextflow/tests/data/simulation_tracker.json`
  - 能力：模拟追踪器夹具
  - 用途：追踪 retrospective simulation 的进度与状态。
  - 复用状态：partial；类型：config

### evaluation

- `src/batchie/cli/evaluate_model.py`
  - 能力：模型评估 CLI
  - 用途：对训练后模型和屏幕结果做评估。
  - 复用状态：ready_for_review；类型：code_entry
- `nextflow/modules/nf-core/batchie/evaluate_model/main.nf`
  - 能力：Nextflow 评估模块
  - 用途：将评估步骤封装为可复用模块。
  - 复用状态：ready_for_review；类型：unknown

### inference

- `src/batchie/cli/select_next_plate.py`
  - 能力：选板推理 CLI
  - 用途：根据模型评分选择下一块/下一批 plate。
  - 复用状态：ready_for_review；类型：code_entry
- `nextflow/subworkflows/nf-core/batchie/select_next_batch_plate/main.nf`
  - 能力：选板子工作流
  - 用途：串联 score 与 selection，输出下一批候选。
  - 复用状态：ready_for_review；类型：unknown

### reusable_assets

- `src/batchie/models/main.py`
  - 能力：核心模型编排
  - 用途：组织模型工厂与公共接口，连接组合建模实现。
  - 复用状态：ready_for_review；类型：code_entry
- `src/batchie/models/sparse_combo.py`
  - 能力：稀疏组合模型
  - 用途：表示稀疏组合药物响应/协同结构。
  - 复用状态：ready_for_review；类型：code_entry
- `src/batchie/models/sparse_combo_interaction.py`
  - 能力：交互扩展模型
  - 用途：在稀疏组合框架中加入交互项。
  - 复用状态：ready_for_review；类型：code_entry
- `src/batchie/models/grid_combo.py`
  - 能力：网格组合模型
  - 用途：以网格方式处理组合响应。
  - 复用状态：ready_for_review；类型：code_entry
- `src/batchie/scoring/main.py`
  - 能力：评分主流程
  - 用途：汇总 scoring 与 acquisition 逻辑，生成候选排序。
  - 复用状态：ready_for_review；类型：code_entry
- `src/batchie/scoring/gaussian_dbal.py`
  - 能力：Gaussian DBAL 评分
  - 用途：计算主动学习 acquisition score。
  - 复用状态：ready_for_review；类型：code_entry
- `src/batchie/policies/k_per_sample.py`
  - 能力：采样/选板策略
  - 用途：控制每个 sample 的 batch 选择数量。
  - 复用状态：ready_for_review；类型：code_entry
- `src/batchie/sampling.py`
  - 能力：采样辅助
  - 用途：生成候选样本并执行抽样相关辅助操作。
  - 复用状态：ready_for_review；类型：code_entry
- `src/batchie/synergy.py`
  - 能力：协同效应计算
  - 用途：计算 synergy 指标和派生量。
  - 复用状态：ready_for_review；类型：code_entry
- `src/batchie/data.py`
  - 能力：数据加载与整形
  - 用途：读取 screen 数据并构造训练/评估输入。
  - 复用状态：ready_for_review；类型：code_entry
- `nextflow/workflows/nf-core/batchie/prospective/main.nf`
  - 能力：前瞻式工作流
  - 用途：封装 prospective active learning 流程。
  - 复用状态：ready_for_review；类型：unknown
- `nextflow/workflows/nf-core/batchie/retrospective_simulation/main.nf`
  - 能力：回顾式模拟工作流
  - 用途：封装 retrospective simulation 流程。
  - 复用状态：ready_for_review；类型：unknown
- `nextflow/workflows/nf-core/batchie/next_batch_plate/main.nf`
  - 能力：下一批 plate 工作流
  - 用途：把评分、选择与输出串成可复用流程。
  - 复用状态：ready_for_review；类型：unknown
- `nextflow/config/base.config`
  - 能力：基础配置模板
  - 用途：提供默认参数与运行配置边界。
  - 复用状态：ready_for_review；类型：config

### training

- `src/batchie/cli/train_model.py`
  - 能力：训练入口 CLI
  - 用途：解析训练参数并启动模型训练。
  - 复用状态：ready_for_review；类型：code_entry
- `nextflow/modules/nf-core/batchie/train_model/main.nf`
  - 能力：Nextflow 训练模块
  - 用途：将训练步骤包装为可复用的 Nextflow 任务。
  - 复用状态：ready_for_review；类型：unknown

## 使用限制

- 仅做静态审查，未安装依赖、未执行代码、未运行测试。
- 仓库中的 HDF5 资产只看到路径级存在，未证明其可直接作为可复用 checkpoint。
- JSON/HDF5 夹具的生成来源与独立许可未核验。
- Nextflow 工作流与模块存在，但端到端可复现性未验证。

## 仍未知

- 是否还有未拉取完整的 promisor/LFS 大文件。
- HDF5 文件究竟是训练 checkpoint、测试快照还是派生中间结果，未通过运行核验。
- JSON fixture 是真实实验数据、模拟数据还是手工构造，未确认。
- perf/ 下实现是否仅用于基准测试或包含替代算法，未执行核验。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
