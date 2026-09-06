# ncbi/GeneGPT

- **仓库：** [https://github.com/ncbi/GeneGPT](https://github.com/ncbi/GeneGPT)
- **固定 commit：** `0a2a327a507be49e660597769cc53431abd6613a`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** found
- **资产记录数：** 10

## 仓库摘要

该仓库是 GeneGPT 的官方静态代码库，主要包含工具辅助推理脚本、评测脚本、两份 bundled 任务数据和若干结果 JSON；未见训练入口或 checkpoint。

## 可复用模块与资源

### datasets

- `data/genehop.json`
  - 能力：GeneHop 任务数据
  - 用途：存放 GeneHop 任务样本/题目，作为推理与评测输入
  - 复用状态：partial；类型：config
- `data/geneturing.json`
  - 能力：GeneTuring 任务数据
  - 用途：存放 GeneTuring 任务样本/题目，作为推理与评测输入
  - 复用状态：partial；类型：config

### evaluation

- `evaluate.py`
  - 能力：评测脚本
  - 用途：对推理结果做静态评测/汇总
  - 复用状态：ready_for_review；类型：code_entry
- `genehop_results/genehop_blast_111011/sequence gene alias.json`
  - 能力：GeneHop 结果样本
  - 用途：保存某一配置下的 GeneHop 输出/结果样本
  - 复用状态：unknown；类型：config
- `geneturing_results/000001/Gene alias.json`
  - 能力：GeneTuring 结果样本
  - 用途：保存某一配置下的 GeneTuring 输出/结果样本
  - 复用状态：unknown；类型：config

### inference

- `main.py`
  - 能力：主推理入口
  - 用途：推理入口脚本；用于生成工具调用或答案的主流程
  - 复用状态：ready_for_review；类型：code_entry
- `main_turbo.py`
  - 能力：Turbo 推理入口
  - 用途：推理入口脚本的 turbo 变体
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `requirements.txt`
  - 能力：运行依赖声明
  - 用途：列出运行所需 Python 依赖，便于环境准备和静态审查
  - 复用状态：ready_for_review；类型：unknown
- `config.py`
  - 能力：运行配置
  - 用途：集中保存脚本运行配置/参数
  - 复用状态：ready_for_review；类型：config
- `gpts_schema.json`
  - 能力：工具/提示 schema
  - 用途：定义与 LLM/工具交互相关的 JSON schema 资源
  - 复用状态：partial；类型：config

## 使用限制

- 仅做静态盘点，未执行仓库代码或测试
- dependencies 未安装，无法验证运行可行性
- 未发现训练入口、训练模块或 checkpoint 文件
- bundled data 与结果 JSON 的来源和生成方式未核实

## 仍未知

- data/genehop.json 与 data/geneturing.json 的原始来源、许可和字段语义未核实
- genehop_results/ 与 geneturing_results/ 是否为官方生成结果或示例缓存未核实
- gpts_schema.json 与 config.py 的具体内容和调用关系未读文件内容确认
- evaluate.py 的实际指标、输入输出格式和依赖关系未执行验证

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
