# hongxinxiang/imageplb

- **仓库：** [https://github.com/hongxinxiang/imageplb](https://github.com/hongxinxiang/imageplb)
- **固定 commit：** `6c33cd6430715ac4b0d378ca5424193c368b14ab`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 16

## 仓库摘要

仓库是 ImagePLB 的核心研究实现，覆盖 PDBbind 数据加载、EGNN/融合/预测模型、预训练与 PDBbind/LEP 微调、以及指标评估；未发现 tracked 的 bundled 数据、checkpoint 或独立推理入口，代码许可证为 MIT。

## 可复用模块与资源

### evaluation

- `utils/metrics.py`
  - 能力：evaluation_metrics
  - 用途：评估指标与结果统计
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `dataloader/pdbbind_dataset.py`
  - 能力：data_loader
  - 用途：PDBbind 样本读取与数据集封装
  - 复用状态：ready_for_review；类型：code_entry
- `dataloader/data_utils.py`
  - 能力：data_loader
  - 用途：数据预处理与批处理辅助
  - 复用状态：ready_for_review；类型：code_entry
- `dataloader/dataset.py`
  - 能力：data_loader
  - 用途：通用数据集抽象
  - 复用状态：ready_for_review；类型：code_entry
- `model/egnn_pytorch.py`
  - 能力：model_architecture
  - 用途：EGNN backbone for protein-ligand 表征学习
  - 复用状态：partial；类型：code_entry
- `model/fusion_model.py`
  - 能力：model_architecture
  - 用途：特征融合主干
  - 复用状态：ready_for_review；类型：code_entry
- `model/predictor.py`
  - 能力：model_architecture
  - 用途：binding prediction head
  - 复用状态：ready_for_review；类型：code_entry
- `model/model_utils.py`
  - 能力：model_architecture
  - 用途：模型构建与辅助工具
  - 复用状态：ready_for_review；类型：code_entry
- `model/base/attention_utils.py`
  - 能力：model_architecture
  - 用途：attention 相关模块
  - 复用状态：ready_for_review；类型：code_entry
- `model/base/base_utils.py`
  - 能力：model_architecture
  - 用途：基础张量/结构辅助函数
  - 复用状态：ready_for_review；类型：code_entry
- `model/base/predictor.py`
  - 能力：model_architecture
  - 用途：基础 predictor 组件
  - 复用状态：ready_for_review；类型：code_entry

### training

- `pretrain/pretrain_ImagePLB.py`
  - 能力：training_entrypoint
  - 用途：ImagePLB 预训练流程
  - 复用状态：ready_for_review；类型：code_entry
- `pretrain/pretrain_utils.py`
  - 能力：training_module
  - 用途：预训练辅助函数与流程支持
  - 复用状态：ready_for_review；类型：code_entry
- `finetune/pdbbind.py`
  - 能力：training_entrypoint
  - 用途：PDBbind 下游微调
  - 复用状态：ready_for_review；类型：code_entry
- `finetune/lep.py`
  - 能力：training_entrypoint
  - 用途：LEP 下游微调
  - 复用状态：ready_for_review；类型：code_entry
- `finetune/finetune_utils.py`
  - 能力：training_module
  - 用途：微调辅助函数
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单审查，未运行代码、测试或训练。
- tracked 路径中未发现 bundled 数据集、checkpoint 或独立 inference 入口。
- 外部下载数据与权重的实际许可、版本和可获得性无法仅凭清单确认。
- `model/egnn_pytorch.py` 的来源是否为项目自研或 vendored third-party 仅凭静态信息无法判定。

## 仍未知

- 是否存在未跟踪的配置文件、数据下载脚本或模型权重，当前清单无法确认。
- `utils/metrics.py` 的具体指标实现与论文报告的对应关系未被执行验证。
- 下游任务 `PDBbind` 与 `LEP` 使用的数据版本和划分策略未从静态清单中确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
