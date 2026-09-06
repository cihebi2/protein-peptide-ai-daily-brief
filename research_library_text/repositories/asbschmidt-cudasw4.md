# asbschmidt/CUDASW4

- **仓库：** [https://github.com/asbschmidt/CUDASW4](https://github.com/asbschmidt/CUDASW4)
- **固定 commit：** `3401c3df8708c6a88796206ad3bd191d31f7b233`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 6

## 仓库摘要

这是一个面向蛋白序列 Smith-Waterman 数据库搜索的 CUDA 仓库，包含搜索核心、数据库/序列 I/O、构建参数、若干基准脚本，以及一个 FASTA 输入文件；未见训练流程、checkpoint 或独立模型工件，代码许可证为 Apache-2.0。

## 可复用模块与资源

### datasets

- `allqueries.fasta`
  - 能力：查询序列样例/基准输入
  - 用途：单个 FASTA 输入文件；从文件名看似用于查询集或 benchmark 输入，但具体语义未验证
  - 复用状态：unknown；类型：unknown

### evaluation

- `benchmarksetup.sh`
  - 能力：基准运行脚本
  - 用途：准备并运行不同数据库规模/场景的性能评测
  - 复用状态：partial；类型：code_entry

### inference

- `src/main.cu`
  - 能力：命令行 GPU 搜索推理
  - 用途：解析参数并启动 Smith-Waterman 数据库搜索
  - 复用状态：ready_for_review；类型：unknown

### reusable_assets

- `src/main.cu`
  - 能力：GPU Smith-Waterman 搜索核心
  - 用途：实现主搜索流程、核函数实例化与比对评分路径
  - 复用状态：ready_for_review；类型：unknown
- `src/dbdata.cpp`
  - 能力：数据库/序列 I/O 与批处理
  - 用途：支持 FASTA/数据库读取、构建、批处理与 GPU 内存分配
  - 复用状态：ready_for_review；类型：unknown
- `Makefile`
  - 能力：构建与参数配置
  - 用途：提供编译配置与运行参数解析
  - 复用状态：ready_for_review；类型：unknown

## 使用限制

- 仅做静态清点，未编译、未运行、未测试。
- 依赖未安装，外部 GPU/数据库环境未知。
- benchmark 脚本依赖的外部数据库/下载步骤未验证。
- `allqueries.fasta` 的真实用途只能从路径名推断。

## 仍未知

- `allqueries.fasta` 是正式数据集还是示例输入未确认。
- 是否存在未跟踪的大文件或外部数据库依赖未确认。
- README 中的执行说明和参数约定未展开验证。
- benchmark 输入/输出结果没有静态证据。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
