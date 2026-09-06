# aljpetri/isONclust3

- **仓库：** [https://github.com/aljpetri/isONclust3](https://github.com/aljpetri/isONclust3)
- **固定 commit：** `90a61e6d8e5e8130408b3640cf2520de3b1ebd04`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 13

## 仓库摘要

该冻结仓库是 isONclust3 的 Rust 代码库，静态清单显示其围绕长读 transcriptome clustering 提供 CLI、核心聚类、seed 过滤、FASTQ 排序、并行化与输出模块；未见训练、评估或 checkpoint 资产，仅有一个示例 FASTQ，且未执行代码。

## 可复用模块与资源

### datasets

- `example_data/test_data.fastq`
  - 能力：示例输入/测试夹具
  - 用途：仓库内示例 FASTQ 输入，可用于 smoke test 或手工验证流程
  - 复用状态：partial；类型：unknown

### inference

- `src/generate_sorted_fastq_for_cluster.rs`
  - 能力：排序 FASTQ 生成与聚类输入准备
  - 用途：生成用于聚类的排序 FASTQ，中间输入准备环节
  - 复用状态：ready_for_review；类型：unknown

### reusable_assets

- `Cargo.toml`
  - 能力：构建/依赖清单
  - 用途：定义 Rust 依赖、构建元数据与发行配置
  - 复用状态：ready_for_review；类型：config
- `Cargo.lock`
  - 能力：依赖锁定文件
  - 用途：固定依赖版本，便于后续构建复核
  - 复用状态：ready_for_review；类型：unknown
- `src/main.rs`
  - 能力：命令行入口
  - 用途：CLI 入口，串联聚类、输入输出与运行流程
  - 复用状态：ready_for_review；类型：unknown
- `src/clustering.rs`
  - 能力：核心聚类逻辑
  - 用途：实现主要聚类流程与簇构建逻辑
  - 复用状态：ready_for_review；类型：unknown
- `src/seeding_and_filtering_seeds.rs`
  - 能力：seed 生成与过滤
  - 用途：生成并筛选种子以支撑聚类前处理
  - 复用状态：ready_for_review；类型：unknown
- `src/Parallelization_side.rs`
  - 能力：并行化辅助
  - 用途：并行执行相关辅助逻辑
  - 复用状态：ready_for_review；类型：unknown
- `src/file_actions.rs`
  - 能力：文件 I/O 辅助
  - 用途：输入文件读取与通用文件操作
  - 复用状态：ready_for_review；类型：unknown
- `src/write_output.rs`
  - 能力：输出写入
  - 用途：写出聚类结果与相关输出文件
  - 复用状态：ready_for_review；类型：unknown
- `src/gff_handling.rs`
  - 能力：GFF 处理
  - 用途：处理 GFF 相关输入/注释数据
  - 复用状态：ready_for_review；类型：unknown
- `src/structs.rs`
  - 能力：共享结构体定义
  - 用途：定义跨模块共享的数据结构
  - 复用状态：ready_for_review；类型：unknown
- `src/side_functions_corr.rs`
  - 能力：支持/校正函数
  - 用途：辅助计算与校正相关的支持函数
  - 复用状态：ready_for_review；类型：unknown

## 使用限制

- 仅做静态清单审查，未执行代码。
- dependencies 未安装，无法验证 Cargo.toml/Cargo.lock 的实际可构建性。
- tests/CI 未见明确资产，且未运行测试。
- example_data/test_data.fastq 仅见路径，未检查内容、来源与许可。
- 未发现训练/评估/checkpoint 资产，但这只能说明冻结清单中未列出。

## 仍未知

- example_data/test_data.fastq 的具体内容、来源和许可未确认。
- src/clustering.rs 等核心模块的实际行为未通过运行验证。
- 是否存在未初始化 submodule 或未跟踪的大文件，静态清单无法完全排除。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
