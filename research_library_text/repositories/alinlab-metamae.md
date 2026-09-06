# alinlab/MetaMAE

- **仓库：** [https://github.com/alinlab/MetaMAE](https://github.com/alinlab/MetaMAE)
- **固定 commit：** `0de4c830868e667ce5d7289080d85787ba7244f6`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 2

## 仓库摘要

仓库看起来是 MetaMAE 的代码实现：包含多模态数据加载器、模型定义和预训练入口；静态清单里还出现了 `linear_evaluation.py` 的评估痕迹。未发现 bundled 数据、checkpoint 或独立推理管线；LICENSE 缺失使代码复用边界未闭合。

## 可复用模块与资源

### reusable_assets

- `models.py`
  - 能力：model_architecture
  - 用途：MetaMAE 主模型/编码器-解码器结构定义。
  - 复用状态：blocked；类型：code_entry

### training

- `pretrain.py`
  - 能力：training_entrypoint
  - 用途：预训练启动入口。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审查，未运行任何脚本。
- dependencies 未安装，无法验证导入与环境。
- repository code 未执行，路径存在不等于可复现。
- 未初始化 submodules，且 >5MiB 大对象可能仍是 promisor-only。
- 未发现可核验的 checkpoint、bundled 数据或推理产物。

## 仍未知

- `linear_evaluation.py` 的真实作用与评估指标未验证。
- 实际支持的模态组合、数据集名称和下载方式未确认。
- 模型结构细节、超参数和训练日程仅能从文件名推测。
- 是否存在未追踪的权重文件或外部下载资产未知。
- 代码、数据与模型各自的正式许可边界未能建立。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
