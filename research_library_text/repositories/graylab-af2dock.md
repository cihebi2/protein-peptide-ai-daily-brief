# graylab/af2dock

- **仓库：** [https://github.com/graylab/af2dock](https://github.com/graylab/af2dock)
- **固定 commit：** `dde6a4f7f14fb93ccc79101203348d41571f8f9e`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 17

## 仓库摘要

静态审查显示 AF2Dock 主要提供蛋白-蛋白对接的模型、训练、推断和测试代码，并附带示例输入与若干辅助数据；仓库内未见可追踪的 checkpoint 权重。

## 可复用模块与资源

### datasets

- `data/example_input/ab_8tbq_1.csv`
  - 能力：example docking input bundle
  - 用途：示例推断输入，配套结构文件演示单个复合物案例
  - 复用状态：partial；类型：unknown
- `data/pinder_entity_seq_cluster.pkl`
  - 能力：entity sequence cluster cache
  - 用途：疑似用于按实体序列聚类的数据划分或预处理缓存
  - 复用状态：unknown；类型：unknown
- `data/train_samples_to_exclude.txt`
  - 能力：training exclusion list
  - 用途：训练样本过滤/排除清单
  - 复用状态：partial；类型：unknown

### evaluation

- `scripts/test_pinder.py`
  - 能力：PINDER evaluation test harness
  - 用途：对接评估与回归测试
  - 复用状态：partial；类型：code_entry
- `scripts/test_pinder_afm.py`
  - 能力：AFM PINDER evaluation test harness
  - 用途：AFM 变体的评估与回归测试
  - 复用状态：partial；类型：code_entry
- `notebooks/compute_success_rate.ipynb`
  - 能力：success-rate analysis notebook
  - 用途：离线成功率统计与结果汇总
  - 复用状态：partial；类型：unknown

### inference

- `predict.py`
  - 能力：main prediction CLI
  - 用途：通用推断入口
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/predict_afm.py`
  - 能力：AFM-specific prediction CLI
  - 用途：特定推断流程或模式切换
  - 复用状态：ready_for_review；类型：code_entry
- `AF2Dock/utils/inference_utils.py`
  - 能力：inference helpers
  - 用途：推断前后处理与结果整理
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `AF2Dock/model/model.py`
  - 能力：protein-protein docking model architecture
  - 用途：核心流匹配/共折叠模型与结构组件实现
  - 复用状态：ready_for_review；类型：code_entry
- `AF2Dock/data/datamodule.py`
  - 能力：data loading and preprocessing
  - 用途：训练/推断数据组装、batch 组织与输入预处理
  - 复用状态：ready_for_review；类型：code_entry
- `train.py`
  - 能力：training pipeline
  - 用途：训练入口与训练流程编排
  - 复用状态：ready_for_review；类型：code_entry
- `predict.py`
  - 能力：inference pipeline
  - 用途：通用推断入口与结果输出
  - 复用状态：ready_for_review；类型：code_entry
- `AF2Dock/utils/dockq.py`
  - 能力：structure scoring utility
  - 用途：DockQ 结构比较与对接结果评分
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/download_weights.py`
  - 能力：checkpoint acquisition script
  - 用途：下载外部权重；仓库内未见 tracked checkpoint 文件
  - 复用状态：partial；类型：code_entry

### training

- `train.py`
  - 能力：training entrypoint
  - 用途：启动训练与参数汇总
  - 复用状态：ready_for_review；类型：code_entry
- `AF2Dock/utils/train_utils.py`
  - 能力：training utilities
  - 用途：训练循环、优化与辅助逻辑
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清点，未执行代码、训练或测试。
- 依赖未安装，无法验证运行时行为。
- 仓库内未发现 tracked checkpoint；权重获取更可能依赖外部下载。
- 数据与辅助文件的生成来源、许可和可再分发边界未被充分证明。
- 存在 large blob / promisor-only 风险，文件 presence 不等于完整可复现。

## 仍未知

- scripts/download_weights.py 实际会下载哪一组权重，以及对应许可证。
- data/pinder_entity_seq_cluster.pkl 的生成流程与上游来源。
- data/train_samples_to_exclude.txt 的构建规则和是否对应论文固定划分。
- notebooks 是否仅作分析草稿，还是用于最终 success rate 统计。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
