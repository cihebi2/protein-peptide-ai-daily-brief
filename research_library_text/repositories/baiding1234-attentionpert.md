# BaiDing1234/AttentionPert

- **仓库：** [https://github.com/BaiDing1234/AttentionPert](https://github.com/BaiDing1234/AttentionPert)
- **固定 commit：** `8746d1a7f29c06784321340da19c8a8f42fa4eaf`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 12

## 仓库摘要

仓库主要提供 AttentionPert 的模型实现、数据处理、推理与结果分析脚本；未见 bundled data、训练入口、checkpoint 或 LICENSE，因此只能做静态盘点，不能证明可复现或可直接复用。

## 可复用模块与资源

### evaluation

- `result_process/NA_analysis.py`
  - 能力：result_analysis
  - 用途：缺失值/NA 场景的结果分析。
  - 复用状态：blocked；类型：code_entry
- `result_process/ablation_plot.py`
  - 能力：result_analysis
  - 用途：消融对比图生成。
  - 复用状态：blocked；类型：code_entry
- `result_process/detail_analysis.py`
  - 能力：result_analysis
  - 用途：细粒度结果分析。
  - 复用状态：blocked；类型：code_entry
- `result_process/pert_gene_cluster.py`
  - 能力：result_analysis
  - 用途：扰动-基因聚类分析。
  - 复用状态：blocked；类型：code_entry
- `result_process/k562_pod_psd.py`
  - 能力：result_analysis
  - 用途：K562 场景的结果处理/作图。
  - 复用状态：blocked；类型：code_entry
- `result_process/norman_pod_psd.py`
  - 能力：result_analysis
  - 用途：Norman 场景的结果处理/作图。
  - 复用状态：blocked；类型：code_entry
- `result_process/rpe1_pod_psd.py`
  - 能力：result_analysis
  - 用途：RPE1 场景的结果处理/作图。
  - 复用状态：blocked；类型：code_entry

### inference

- `attnpert/inference.py`
  - 能力：inference
  - 用途：加载模型并生成预测/推断结果。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `attnpert/model.py`
  - 能力：model_architecture
  - 用途：定义 AttentionPert 的核心模型结构与前向计算。
  - 复用状态：blocked；类型：code_entry
- `attnpert/data_utils.py`
  - 能力：data_loader
  - 用途：数据读取、样本组织与预处理辅助。
  - 复用状态：blocked；类型：code_entry
- `attnpert/pertdata.py`
  - 能力：data_model
  - 用途：扰动数据对象与数据集封装。
  - 复用状态：blocked；类型：code_entry
- `attnpert/utils.py`
  - 能力：utility_helpers
  - 用途：通用辅助函数。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查；未执行代码、测试或依赖安装。
- 仓库未见 LICENSE，代码直接复用受限。
- 未见 bundled data 与 checkpoint，无法确认完整训练/推理链路。
- `run_attnpert.py` 的具体角色（训练、推理或实验编排）未被静态清单确认。
- 依赖文件 `environment.yml` 存在，但未验证可安装性与版本兼容性。

## 仍未知

- 数据集来源、切分方式与预处理细节未确认。
- 训练超参数、优化器、epoch 与是否支持再训练未确认。
- 推理是否依赖外部 checkpoint 或下载权重未确认。
- `result_process` 脚本的具体输入输出格式与指标定义未确认。
- 是否包含未显式识别的 vendored third-party 代码或资源未确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
