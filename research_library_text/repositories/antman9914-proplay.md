# antman9914/proplay

- **仓库：** [https://github.com/antman9914/proplay](https://github.com/antman9914/proplay)
- **固定 commit：** `77b3a3c2f0762919e744a0ede782c5a00dbb3b13`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 13

## 仓库摘要

仓库是 ProPlay 的研究代码，包含多基准 agent/推理/评测管线与数据划分脚本，但未见 LICENSE、训练入口或 checkpoint。

## 可复用模块与资源

### datasets

- `data/plancraft/gen_splits.py`
  - 能力：Plancraft 划分生成脚本
  - 用途：生成/整理 Plancraft 划分；仓库未见原始数据文件
  - 复用状态：blocked；类型：code_entry
- `data/sciworld/gen_online_splits.py`
  - 能力：SciWorld 在线划分生成脚本
  - 用途：生成 SciWorld 在线划分
  - 复用状态：blocked；类型：code_entry
- `data/taubench/load_data.py`
  - 能力：TAU-bench 数据加载脚本
  - 用途：加载 TAU-bench 数据；未见随仓库分发的原始数据
  - 复用状态：blocked；类型：code_entry

### evaluation

- `benchmarks/plancraft/preplay.py`
  - 能力：Plancraft 评测/预播放流程
  - 用途：执行 benchmark 级预播放与评测逻辑
  - 复用状态：blocked；类型：code_entry
- `benchmarks/sciworld/preplay.py`
  - 能力：SciWorld 评测/预播放流程
  - 用途：执行 benchmark 级预播放与评测逻辑
  - 复用状态：blocked；类型：code_entry
- `benchmarks/taubench/preplay.py`
  - 能力：TAU-bench 评测/预播放流程
  - 用途：执行 benchmark 级预播放与评测逻辑
  - 复用状态：blocked；类型：code_entry

### inference

- `benchmarks/plancraft/pipeline.py`
  - 能力：Plancraft 推理管线
  - 用途：串接 agent/router/graph/induction 以执行 Plancraft 推理流程
  - 复用状态：blocked；类型：code_entry
- `benchmarks/sciworld/pipeline.py`
  - 能力：SciWorld 推理管线
  - 用途：串接 agent/router/graph/induction 以执行 SciWorld 推理流程
  - 复用状态：blocked；类型：code_entry
- `benchmarks/taubench/pipeline.py`
  - 能力：TAU-bench 推理管线
  - 用途：串接 agent/router/graph/induction 以执行 TAU-bench 推理流程
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `proplay/env.py`
  - 能力：核心环境抽象
  - 用途：定义共享环境接口与状态封装，供各 benchmark 复用
  - 复用状态：blocked；类型：code_entry
- `proplay/graph.py`
  - 能力：工作流/图结构工具
  - 用途：支持 agent 流程图构建与调度
  - 复用状态：blocked；类型：code_entry
- `proplay/llm.py`
  - 能力：LLM 调用封装
  - 用途：统一模型请求、响应适配与调用入口
  - 复用状态：blocked；类型：code_entry
- `prompts/plancraft/preplay_instruction.txt`
  - 能力：Prompt 模板
  - 用途：预播放式提示模板；同类模板还见 sciworld/taubench 目录
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态清单审查，未执行代码或测试。
- 未发现 LICENSE，直接复用代码存在授权阻断。
- 仓库未见训练入口或 checkpoint 文件。
- 未见原始数据集文件；数据脚本是否依赖外部下载无法确认。

## 仍未知

- `data/*` 脚本是否会在线下载或要求本地外部数据源，当前无法确认。
- 依赖项的具体许可证与兼容性未核验。
- `benchmarks/*` 的实际运行行为与结果未验证。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
