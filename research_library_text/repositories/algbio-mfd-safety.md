# algbio/mfd-safety

- **仓库：** [https://github.com/algbio/mfd-safety](https://github.com/algbio/mfd-safety)
- **固定 commit：** `f435623bc9b7f34f331a55188213ec5f0eef3ba2`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 6

## 仓库摘要

仓库是一个轻量级 Python 实现与示例集，确认到 GPL-3.0 代码许可；未见训练入口、模型 checkpoint 或可证明的正式评测流程。

## 可复用模块与资源

### datasets

- `example_inputs/example.graph`
  - 能力：example_graph_inputs
  - 用途：示例图输入与图结构样例。
  - 复用状态：unknown；类型：unknown
- `example_inputs/example.safe`
  - 能力：example_label_and_count_files
  - 用途：示例安全标注与计数辅助文件。
  - 复用状态：unknown；类型：unknown

### evaluation

- `example_inputs/Group/example.test`
  - 能力：example_test_fixture
  - 用途：示例测试/验证文件；静态存在不足以证明有正式 benchmark。
  - 复用状态：partial；类型：unknown

### inference

- `src/mfd_safety.py`
  - 能力：inference_driver
  - 用途：推断/求解入口候选；从文件名看应是安全检查主程序，但未执行验证。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/mfd_safety.py`
  - 能力：core_algorithm_source
  - 用途：唯一的 Python 源文件；应承载 flow decomposition safety 检查与主流程实现。
  - 复用状态：ready_for_review；类型：code_entry
- `conda_environment.yml`
  - 能力：dependency_environment_recipe
  - 用途：Conda 环境定义；可用于重建依赖集合，但未见安装或运行验证。
  - 复用状态：partial；类型：config

## 使用限制

- 仅做静态审计，未执行代码、未安装依赖、未运行测试。
- 仓库中未发现训练入口、模型权重或 checkpoint。
- 示例数据/测试文件缺少独立许可声明，数据复用边界不清。
- 路径存在不等于可复现或已验证的功能实现。

## 仍未知

- `src/mfd_safety.py` 的具体函数行为与 CLI 接口未通过执行验证。
- README 仅有路径元数据，未能据此核实更详细的方法说明。
- `example_inputs/*` 是否为正式数据集或仅为演示样例，无法从静态清单判定。
- 依赖环境是否可直接重建未知。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
