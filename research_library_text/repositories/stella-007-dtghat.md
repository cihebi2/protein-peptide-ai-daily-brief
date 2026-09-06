# stella-007/dtghat

- **仓库：** [https://github.com/stella-007/dtghat](https://github.com/stella-007/dtghat)
- **固定 commit：** `058b285ee3f0d90579f815e804f71eb636e0462b`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 7

## 仓库摘要

冻结清单只显示 DTGHAT 的模型定义与 3 个训练入口；未见 bundled data、evaluation、inference、checkpoint 或 LICENSE，故只能确认静态存在，不能证明复现或直接复用。

## 可复用模块与资源

### reusable_assets

- `src/model.py`
  - 能力：model architecture
  - 用途：DTGHAT 核心主模型定义
  - 复用状态：blocked；类型：code_entry
- `5CV/model.py`
  - 能力：model architecture
  - 用途：5CV 版本的主模型定义
  - 复用状态：blocked；类型：code_entry
- `ablation/attributes_feature/model.py`
  - 能力：model architecture
  - 用途：attributes_feature 消融模型定义
  - 复用状态：blocked；类型：code_entry
- `ablation/network_feature/model.py`
  - 能力：model architecture
  - 用途：network_feature 消融模型定义
  - 复用状态：blocked；类型：code_entry

### training

- `5CV/train.py`
  - 能力：training entrypoint
  - 用途：5-fold cross-validation 训练入口
  - 复用状态：blocked；类型：code_entry
- `ablation/attributes_feature/train.py`
  - 能力：training entrypoint
  - 用途：attributes_feature 消融训练入口
  - 复用状态：blocked；类型：code_entry
- `ablation/network_feature/train.py`
  - 能力：training entrypoint
  - 用途：network_feature 消融训练入口
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅基于冻结清单做静态审查，未执行仓库代码。
- 未见 bundled data、data_loader、evaluation、inference 或 checkpoint 资产，无法验证端到端复现。
- 仓库为浅克隆且存在 promisor-only 大文件限制，不能排除未展开的大权重/数据。
- 未见 LICENSE，代码复用边界不明，不能直接复用。
- `src/DTI_train.py` 与 `src/drug_embedding.py` 存在于 tracked_paths，但未被冻结 inventory 归类，具体角色未明。

## 仍未知

- 训练数据来源、下载方式与划分策略未见。
- `5CV` 的具体交叉验证协议、指标和阈值未见。
- `src/DTI_train.py` 更像训练或辅助脚本，但冻结证据不足以确定。
- `src/drug_embedding.py` 可能是特征/嵌入辅助模块，但功能未确认。
- 是否存在未展开的外部权重或大数据文件未知。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
