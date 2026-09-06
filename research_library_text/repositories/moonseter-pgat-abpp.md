# moonseter/PGAT-ABPp

- **仓库：** [https://github.com/moonseter/PGAT-ABPp](https://github.com/moonseter/PGAT-ABPp)
- **固定 commit：** `e3a1a38e784f5449c49c745372e0ea85b3e6ee04`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 14

## 仓库摘要

仓库包含PGAT-ABPp 的训练与推理代码、共享的图构建/模型模块、两个数据压缩包、训练/预测示例输入和一个 h5 权重；train/ 与 predict/ 下的 Model.py 与 GraphFromPDB.py 清单哈希相同，说明核心实现共享，但未见独立评测脚本、许可证文件或执行证据。

## 可复用模块与资源

### checkpoints

- `predict/pgat_abpp.h5`
  - 能力：已训练模型权重
  - 用途：供推理脚本直接加载的模型检查点
  - 复用状态：blocked；类型：model_weight

### datasets

- `dataset/main dataset.zip`
  - 能力：主训练数据包
  - 用途：主数据压缩包；内部标签、划分与来源未解包验证
  - 复用状态：blocked；类型：unknown
- `dataset/independent test dataset.zip`
  - 能力：独立测试数据包
  - 用途：从文件名推断为独立测试/评测输入；内部结构未验证
  - 复用状态：blocked；类型：unknown
- `train/example_data/data.csv`
  - 能力：训练示例数据
  - 用途：演示训练输入格式的 CSV、npy 与 PDB 示例；包含 abp/ 与 nonabp/ 子样本
  - 复用状态：blocked；类型：unknown
- `predict/example_data/data.csv`
  - 能力：推理示例数据
  - 用途：演示预测输入格式的 CSV、npy 与 PDB 示例；包含 files/ 子样本
  - 复用状态：blocked；类型：unknown

### evaluation

- `dataset/independent test dataset.zip`
  - 能力：独立测试评估输入
  - 用途：仓库内唯一可见的评测相关数据包；未见单独指标计算或结果复现脚本
  - 复用状态：blocked；类型：unknown

### inference

- `predict/Predict.py`
  - 能力：推理入口
  - 用途：加载权重并对输入样本输出预测结果
  - 复用状态：blocked；类型：code_entry
- `predict/Model.py`
  - 能力：推理侧核心模块
  - 用途：推理管线中的模型、图转换与 PDB 预处理
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `train/Model.py`
  - 能力：共享模型结构
  - 用途：定义 PGAT-ABPp 主网络；训练和推理共用同一实现
  - 复用状态：blocked；类型：code_entry
- `train/GraphFromPDB.py`
  - 能力：共享图构建/特征转换
  - 用途：把 PDB 输入转换为图表示，供训练与推理共用
  - 复用状态：blocked；类型：code_entry
- `train/PDBProcess.py`
  - 能力：PDB 处理模块
  - 用途：训练/推理阶段的 PDB 解析与预处理
  - 复用状态：blocked；类型：code_entry
- `predict/pgat_abpp.h5`
  - 能力：模型权重
  - 用途：推理时加载的已训练权重文件
  - 复用状态：blocked；类型：unknown

### training

- `train/Train.py`
  - 能力：训练入口
  - 用途：训练主脚本，串联数据处理、图构建与模型拟合
  - 复用状态：blocked；类型：code_entry
- `train/Model.py`
  - 能力：训练侧核心模块
  - 用途：训练管线中的模型、图转换与 PDB 预处理
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 静态清单分析，未执行仓库代码。
- 未安装依赖，未运行测试或训练/推理流程。
- 仓库未见许可文件，直接复用受限。
- 存在大体积 blob 的 promisor 风险，目录存在不等于内容完整或可复现。
- 路径存在不等于已经验证过训练、评测或 checkpoint 可用。

## 仍未知

- main dataset.zip 与 independent test dataset.zip 的真实来源、标签定义和内部划分未验证。
- h5 权重是否与当前代码接口完全匹配、以及训练时使用的超参数与评测协议未验证。
- README 之外是否存在隐含的外部数据/预处理依赖无法从静态清单确认。
- 未发现独立评估脚本，实际指标来源只能从仓库外文档进一步确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
