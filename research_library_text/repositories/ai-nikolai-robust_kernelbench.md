# ai-nikolai/robust_kernelbench

- **仓库：** [https://github.com/ai-nikolai/robust_kernelbench](https://github.com/ai-nikolai/robust_kernelbench)
- **固定 commit：** `1497dbb57939c327b16e3e44425b39781af7dcf1`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 14

## 仓库摘要

仓库主要围绕 `kb_prompts` 中的 CoT/few-shot kernel prompt 族、作业生成脚本、评测脚本和测试脚本，形成一个用于生成与验证 LLM kernel 方案的静态工具集；未发现 tracked 数据集、训练入口或 checkpoint，当前可见许可证边界仅为 GPL-3.0 代码。

## 可复用模块与资源

### evaluation

- `robust_kernelbench/evaluate_all.py`
  - 能力：批量评测
  - 用途：批量评估生成结果
  - 复用状态：partial；类型：code_entry
- `robust_kernelbench/evaluate_single.py`
  - 能力：单样本评测
  - 用途：单条结果的评估入口
  - 复用状态：partial；类型：code_entry
- `robust_kernelbench/test_inference_test_time_scaling.py`
  - 能力：推理流程测试
  - 用途：验证 test-time scaling 推理链路
  - 复用状态：partial；类型：code_entry
- `tests/test_generation_extraction.py`
  - 能力：生成结果抽取测试
  - 用途：验证输出抽取逻辑
  - 复用状态：partial；类型：code_entry
- `tests/test.cu`
  - 能力：CUDA/编译测试
  - 用途：CUDA 测试内核与编译检查
  - 复用状态：partial；类型：unknown
- `tests/test.sh`
  - 能力：测试编排脚本
  - 用途：串联测试执行流程
  - 复用状态：partial；类型：code_entry

### inference

- `scripts/archive/generate_slurm_job.sh`
  - 能力：作业生成脚本
  - 用途：生成 SLURM 推理作业
  - 复用状态：partial；类型：code_entry
- `scripts/archive/generate_tsp_job.sh`
  - 能力：作业生成脚本
  - 用途：生成 TSP 推理作业
  - 复用状态：partial；类型：code_entry
- `robust_kernelbench/run_inference_test_time_scaling.py`
  - 能力：test-time scaling 推理入口
  - 用途：驱动 test-time scaling 推理流程
  - 复用状态：partial；类型：code_entry
- `robust_kernelbench/run_inference_test_time_scaling_v2.py`
  - 能力：test-time scaling 推理入口
  - 用途：test-time scaling 推理流程的新版入口
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `robust_kernelbench/kb_prompts/prompts.toml`
  - 能力：kernel prompt 模板配置
  - 用途：组织不同 kernel 任务的提示配置与版本入口
  - 复用状态：ready_for_review；类型：config
- `robust_kernelbench/kb_prompts/hardware/gpu_specs.py`
  - 能力：硬件感知 prompt 参数
  - 用途：提供 GPU 规格信息以支持硬件相关提示构造
  - 复用状态：ready_for_review；类型：code_entry
- `robust_kernelbench/utils/utils_inference.py`
  - 能力：推理辅助函数
  - 用途：封装推理流程中的通用逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `robust_kernelbench/utils/utils_evaluate_common.py`
  - 能力：评测公共函数
  - 用途：封装批量/单样本评测共用逻辑
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清点，未执行仓库代码。
- 依赖未安装，无法验证运行时行为。
- 测试未运行，不能据此证明可复现。
- 存在大文件与外部资源不可见风险。
- 路径存在只能证明文件被跟踪，不能证明其已成功运行或产出结果。

## 仍未知

- README.md 的完整内容未读取。
- 是否存在未跟踪的数据集或 checkpoint 未知。
- 部分脚本可能依赖集群、GPU 或外部推理环境。
- `requirements*.txt` 中第三方依赖的最终许可边界未逐项核验。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
