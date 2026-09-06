# microsoft/peft_proteomics

- **仓库：** [https://github.com/microsoft/peft_proteomics](https://github.com/microsoft/peft_proteomics)
- **固定 commit：** `1042a6337c1bdac5c24c6c94a9e06f4a211be84e`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 19

## 仓库摘要

这是论文《Democratizing protein language models with parameter-efficient fine-tuning》的代码仓库静态快照，主要覆盖 PPI 与 symmetry 两条参数高效微调/LoRA 流水线，包含模型、数据加载、训练启动、基线网格搜索、测试评估与可视化资产；冻结清单中未见 bundled dataset 或 checkpoint，且仅做静态审查，未运行代码。

## 可复用模块与资源

### datasets

- `data/README.md`
  - 能力：外部数据说明与准备
  - 用途：说明数据获取/放置/重整方式；冻结快照未见实际数据文件
  - 复用状态：unknown；类型：unknown

### evaluation

- `figures/ppi_ft_lora_valid_aupr.png`
  - 能力：PPI 验证指标与损失曲线
  - 用途：展示 validation AUPR / loss 等评估结果
  - 复用状态：partial；类型：unknown
- `figures/symm_ft_lora_valid_aupr.png`
  - 能力：symmetry 验证指标与损失曲线
  - 用途：展示 symmetry validation AUPR / loss 等评估结果
  - 复用状态：partial；类型：unknown
- `ppi/results/ppi_rank_valid_aupr.png`
  - 能力：对照实验与 rank 结果
  - 用途：展示 rank / baseline 相关验证对比
  - 复用状态：partial；类型：unknown
- `figures/ft_valid_recall_fluctuation.png`
  - 能力：指标波动与注意力可视化
  - 用途：展示 recall / specificity 波动和 attention map 结果
  - 复用状态：partial；类型：unknown

### inference

- `ppi/test.py`
  - 能力：PPI 推理/测试入口
  - 用途：对持出集或测试集执行预测并导出结果
  - 复用状态：partial；类型：code_entry
- `symmetry/test.py`
  - 能力：symmetry 推理/测试入口
  - 用途：对 symmetry 数据执行预测并检查输出
  - 复用状态：partial；类型：code_entry
- `ppi/view_and_evaluate.ipynb`
  - 能力：交互式结果检查
  - 用途：人工查看预测结果、曲线与示例输出
  - 复用状态：partial；类型：unknown

### reusable_assets

- `ppi/modeling.py`
  - 能力：PPI / symmetry 模型定义与参数高效微调核心模块
  - 用途：承载两条任务线的模型结构与微调逻辑，适合作为代码复用起点
  - 复用状态：ready_for_review；类型：code_entry
- `ppi/data.py`
  - 能力：PPI / symmetry 数据加载与整理模块
  - 用途：读取、清洗和切分外部任务数据；仓库本身未打包原始数据
  - 复用状态：partial；类型：code_entry
- `ppi/config/sample_config.yaml`
  - 能力：实验配置模板
  - 用途：提供 PPI 与 symmetry 任务的超参数/运行配置范式
  - 复用状态：ready_for_review；类型：config
- `run_job_ppi.sh`
  - 能力：任务启动脚本
  - 用途：批量启动 PPI / symmetry 训练或评测流程
  - 复用状态：ready_for_review；类型：code_entry
- `ppi/plotting.py`
  - 能力：可视化与结果分析工具
  - 用途：绘图、曲线汇总与 attention 可视化支持
  - 复用状态：partial；类型：code_entry
- `ppi/mlp_grid_search_cv.py`
  - 能力：MLP 基线与 cross-validation 搜索
  - 用途：基线训练、参数搜索与对照实验
  - 复用状态：ready_for_review；类型：code_entry

### training

- `ppi/main.py`
  - 能力：PPI 训练入口
  - 用途：PPI 参数高效微调/训练主流程
  - 复用状态：ready_for_review；类型：code_entry
- `symmetry/main.py`
  - 能力：symmetry 训练入口
  - 用途：symmetry 参数高效微调/训练主流程
  - 复用状态：ready_for_review；类型：code_entry
- `run_job_ppi.sh`
  - 能力：批处理启动与环境封装
  - 用途：通过 shell 脚本批量调用训练/实验流程并依赖 env.yml
  - 复用状态：ready_for_review；类型：code_entry
- `ppi/mlp_grid_search_cv.py`
  - 能力：baseline 训练与搜索
  - 用途：MLP 基线、cross-validation 与超参搜索
  - 复用状态：ready_for_review；类型：code_entry
- `ppi/config/sample_config.yaml`
  - 能力：训练配置
  - 用途：定义训练超参数与数据/模型配置
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做静态审查，未执行代码或测试。
- 仓库未见 bundled dataset 与 checkpoint，外部数据/权重许可未闭环。
- README / notebook 可能依赖运行时环境或外部下载，未逐一验证。
- 静态路径存在不代表对应流程真实可复现。

## 仍未知

- 外部数据集的具体来源、格式和许可。
- 是否存在未跟踪的模型权重或中间产物。
- 训练与评估的实际数值是否可由当前快照复现。
- Notebook 与 shell 脚本的运行顺序和环境假设。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
