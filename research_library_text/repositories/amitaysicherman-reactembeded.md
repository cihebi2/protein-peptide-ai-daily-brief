# amitaysicherman/ReactEmbeded

- **仓库：** [https://github.com/amitaysicherman/ReactEmbeded](https://github.com/amitaysicherman/ReactEmbeded)
- **固定 commit：** `dc29c2df2ebdfca59ad7d140949b5ab3b1b579c0`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 19

## 仓库摘要

该仓库的静态清单主要显示 ReactEmbed 相关的对比学习建模、BioPAX/序列预处理，以及 eval_tasks 下游评测管线；未发现 tracked 数据集、checkpoint 或独立 inference 入口。仓库级 LICENSE 缺失，因此当前只能给出受限的静态复用判断。

## 可复用模块与资源

### evaluation

- `eval_tasks/tasks.py`
  - 能力：评测任务编排
  - 用途：组织下游任务、数据流和评测流程
  - 复用状态：blocked；类型：code_entry
- `eval_tasks/prep_task.py`
  - 能力：评测任务准备
  - 用途：生成或整理评测所需的样本、标签与切分
  - 复用状态：blocked；类型：code_entry
- `eval_tasks/trainer.py`
  - 能力：评测模型训练/验证
  - 用途：运行评测阶段的训练、验证与结果记录
  - 复用状态：blocked；类型：code_entry
- `eval_tasks/models.py`
  - 能力：评测模型定义
  - 用途：提供下游任务模型结构，配合评测流程使用
  - 复用状态：blocked；类型：code_entry
- `eval_tasks/dataset.py`
  - 能力：评测数据接口
  - 用途：为评测任务提供数据读取与批处理
  - 复用状态：blocked；类型：code_entry
- `eval_tasks/scores.py`
  - 能力：评测指标计算
  - 用途：汇总并计算评测分数
  - 复用状态：blocked；类型：code_entry

### inference

- `contrastive_learning/model.py`
  - 能力：embedding 前向推理
  - 用途：提供前向计算，可由外部脚本封装为推理；仓库内未见独立 inference 入口
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `common/path_manager.py`
  - 能力：共享路径与运行时辅助
  - 用途：管理工程内路径与运行目录，供训练/评测脚本复用
  - 复用状态：blocked；类型：code_entry
- `common/utils.py`
  - 能力：共享工具函数
  - 用途：提供通用辅助函数，供多个流程调用
  - 复用状态：blocked；类型：code_entry
- `preprocessing/biopax_parser.py`
  - 能力：BioPAX/通路网络预处理
  - 用途：解析反应网络或通路图输入，服务于表示学习前处理
  - 复用状态：blocked；类型：code_entry
- `preprocessing/seq_to_vec.py`
  - 能力：序列向量化预处理
  - 用途：将序列映射为向量特征，供后续建模使用
  - 复用状态：blocked；类型：code_entry
- `contrastive_learning/model.py`
  - 能力：蛋白-分子联合表征模型
  - 用途：定义对比学习/表示学习主体，可用于生成 embedding
  - 复用状态：blocked；类型：code_entry
- `contrastive_learning/dataset.py`
  - 能力：对比学习数据加载接口
  - 用途：读取和组织训练样本；未见 bundled 数据文件
  - 复用状态：blocked；类型：code_entry
- `contrastive_learning/trainer.py`
  - 能力：对比学习训练循环
  - 用途：实现模型训练、优化与日志流程
  - 复用状态：blocked；类型：code_entry
- `eval_tasks/dataset.py`
  - 能力：下游评测数据接口
  - 用途：读取评测任务数据；未见 bundled 数据文件
  - 复用状态：blocked；类型：code_entry
- `eval_tasks/models.py`
  - 能力：下游评测模型定义
  - 用途：定义评测任务所用模型或 head
  - 复用状态：blocked；类型：code_entry
- `eval_tasks/scores.py`
  - 能力：下游评测指标计算
  - 用途：计算任务分数与指标汇总
  - 复用状态：blocked；类型：code_entry

### training

- `contrastive_learning/trainer.py`
  - 能力：主训练流程
  - 用途：对 ReactEmbed 表征模块进行对比学习训练
  - 复用状态：blocked；类型：code_entry
- `contrastive_learning/dataset.py`
  - 能力：训练样本组织
  - 用途：为训练循环提供样本读取与批处理输入
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清点，未运行代码或测试。
- 依赖未安装，无法验证运行时行为、下载逻辑或数据来源。
- 未发现 tracked 数据集与 checkpoint，无法证明可复现的训练闭环。
- 未找到仓库级 LICENSE，直接复用受限。

## 仍未知

- `run_experiment.sh` 是否为实际训练入口，静态清单未将其归类为 training_entrypoint。
- `contrastive_learning/dataset.py` 与 `eval_tasks/dataset.py` 是否依赖外部下载或私有数据源，未执行前无法确认。
- `eval_tasks/*` 的具体评测协议、切分策略与指标参数无法仅凭路径级清单确认。
- 是否存在未跟踪的大文件 checkpoint 或外部权重，当前冻结清单无法排除。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
