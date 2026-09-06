# ali-ghulam/StackAHTPs

- **仓库：** [https://github.com/ali-ghulam/StackAHTPs](https://github.com/ali-ghulam/StackAHTPs)
- **固定 commit：** `c9c6cb5917579d35d197bb2412090bcda0893370`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 6

## 仓库摘要

该仓库在冻结清单中几乎只有数据与结果归档：4个CSV特征表、2个ZIP压缩包和README，没有源码、训练入口、推理入口、评估脚本或checkpoint。方法层面只能从仓库/论文命名推断为 heterogeneous features + stacked learning，静态证据不足以证明实现或复现；LICENSE 也未发现，复用边界未核实。

## 可复用模块与资源

### datasets

- `DPC_benchmark.csv`
  - 能力：feature_table
  - 用途：DPC 特征表（benchmark 版本），看起来是抗高血压肽分类所用的数据/特征输入
  - 复用状态：blocked；类型：unknown
- `DPC_independent.csv`
  - 能力：feature_table
  - 用途：DPC 特征表（independent 版本），看起来是独立测试/外部验证用输入
  - 复用状态：blocked；类型：unknown
- `PseAAC_benchmark.csv`
  - 能力：feature_table
  - 用途：PseAAC 特征表（benchmark 版本），看起来是抗高血压肽分类所用的数据/特征输入
  - 复用状态：blocked；类型：unknown
- `PseAAC_independent.csv`
  - 能力：feature_table
  - 用途：PseAAC 特征表（independent 版本），看起来是独立测试/外部验证用输入
  - 复用状态：blocked；类型：unknown

### evaluation

- `score.zip`
  - 能力：evaluation_artifact_archive
  - 用途：疑似保存实验分数/结果汇总，可能对应论文评测产物，但不是评测代码
  - 复用状态：unknown；类型：unknown

### reusable_assets

- `revised-figures.zip`
  - 能力：paper_figure_archive
  - 用途：疑似保存修订图稿/论文插图，可作为论文展示材料参考
  - 复用状态：unknown；类型：unknown

## 使用限制

- 冻结清单不含任何源码文件，因此无法静态确认方法实现、训练流程、推理流程或评测流程。
- 仓库未发现 LICENSE，直接复用前必须单独核验代码、数据与结果归档的许可边界。
- ZIP 压缩包内容未展开检查，不能据文件名断定其中是否包含模型权重、图稿或额外数据。

## 仍未知

- `revised-figures.zip` 和 `score.zip` 的内部结构与真实用途未知。
- 四个 CSV 更像特征表/划分表，但无法仅凭文件名确认是原始数据、派生特征还是最终实验输入。
- 仓库是否还依赖未跟踪的大文件、外部下载资源或未初始化子模块，静态清单无法证明。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
