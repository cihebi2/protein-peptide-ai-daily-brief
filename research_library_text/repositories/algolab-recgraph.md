# AlgoLab/RecGraph

- **仓库：** [https://github.com/AlgoLab/RecGraph](https://github.com/AlgoLab/RecGraph)
- **固定 commit：** `0d3cc0d974c2587becfd965c824869d32ac30a16`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 19

## 仓库摘要

该仓库是一个 Rust 实现的 RecGraph 序列-变异图比对工具，包含 recombination-aware/pathwise alignment、POA 变体、CLI、benchmark 和示例输入；未发现训练流程或 checkpoint，仅能静态确认 MIT 代码许可，数据许可与来源仍有不确定性。

## 可复用模块与资源

### datasets

- `example/reads.fa`
  - 能力：example reads input
  - 用途：示例读段输入，用于演示或最小复现。
  - 复用状态：partial；类型：unknown
- `example/graph.gfa`
  - 能力：example graph input
  - 用途：示例图输入，用于演示或最小复现。
  - 复用状态：partial；类型：unknown
- `HOXD55.mtx`
  - 能力：benchmark matrix input
  - 用途：推断为附带的矩阵型测试/基准输入。
  - 复用状态：unknown；类型：unknown
- `HOXD70.mtx`
  - 能力：benchmark matrix input
  - 用途：推断为附带的矩阵型测试/基准输入。
  - 复用状态：unknown；类型：unknown

### evaluation

- `benches/recgraph_benchmark.rs`
  - 能力：benchmark harness
  - 用途：推断为性能/吞吐基准脚本。
  - 复用状态：ready_for_review；类型：unknown
- `.github/workflows/rust.yml`
  - 能力：CI test workflow
  - 用途：推断为自动构建/测试验证流程。
  - 复用状态：ready_for_review；类型：config

### inference

- `src/main.rs`
  - 能力：command-line alignment inference
  - 用途：推断为执行比对与输出的主程序入口。
  - 复用状态：ready_for_review；类型：unknown
- `src/args_parser.rs`
  - 能力：argument parsing and mode selection
  - 用途：推断为参数解析与任务分发。
  - 复用状态：ready_for_review；类型：unknown
- `src/api.rs`
  - 能力：library API for alignment
  - 用途：推断为供外部调用的 API 层。
  - 复用状态：ready_for_review；类型：unknown

### reusable_assets

- `src/pathwise_alignment_recombination.rs`
  - 能力：recombination-aware sequence-to-graph alignment
  - 用途：推断为主算法核心，实现重组感知的路径比对。
  - 复用状态：ready_for_review；类型：unknown
- `src/pathwise_alignment.rs`
  - 能力：pathwise alignment core
  - 用途：推断为通用路径比对框架。
  - 复用状态：ready_for_review；类型：unknown
- `src/pathwise_alignment_gap.rs`
  - 能力：gap-aware pathwise alignment
  - 用途：推断为带 gap 的路径比对变体。
  - 复用状态：ready_for_review；类型：unknown
- `src/pathwise_alignment_semiglobal.rs`
  - 能力：semiglobal pathwise alignment
  - 用途：推断为 semiglobal 比对变体。
  - 复用状态：ready_for_review；类型：unknown
- `src/pathwise_alignment_gap_semi.rs`
  - 能力：gap-semiglobal pathwise alignment
  - 用途：推断为 gap + semiglobal 变体。
  - 复用状态：ready_for_review；类型：unknown
- `src/global_abpoa.rs`
  - 能力：global POA alignment
  - 用途：推断为全局 ABPOA 比对实现。
  - 复用状态：ready_for_review；类型：unknown
- `src/local_poa.rs`
  - 能力：local POA alignment
  - 用途：推断为局部 POA 比对实现。
  - 复用状态：ready_for_review；类型：unknown
- `src/graph.rs`
  - 能力：graph/path data structures
  - 用途：推断为图与路径表示层。
  - 复用状态：ready_for_review；类型：unknown
- `src/main.rs`
  - 能力：CLI inference entrypoint
  - 用途：推断为命令行运行入口。
  - 复用状态：ready_for_review；类型：unknown
- `src/api.rs`
  - 能力：library API entrypoint
  - 用途：推断为供外部调用的 API 层。
  - 复用状态：ready_for_review；类型：unknown

## 使用限制

- 仅作静态盘点，未运行 cargo build/test。
- 依赖未安装，无法验证实际编译或运行结果。
- 未发现训练入口、训练模块或 checkpoint 产物。
- example/ 与 HOXD*.mtx 的来源及授权未独立确认；未见单独数据许可。

## 仍未知

- README 全文未解析，只能依据文件名推断用途。
- HOXD55.mtx/HOXD70.mtx 是否为外部基准集及其授权未知。
- CI/benchmark 文件的实际通过情况未验证。
- 是否存在未跟踪的大文件或生成物无法从静态清单确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
