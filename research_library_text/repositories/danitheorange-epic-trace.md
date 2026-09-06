# DaniTheOrange/EPIC-TRACE

- **仓库：** [https://github.com/DaniTheOrange/EPIC-TRACE](https://github.com/DaniTheOrange/EPIC-TRACE)
- **固定 commit：** `cc5324894ff9cddc792504c06dcc53dff1d73fc3`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 19

## 仓库摘要

静态清点显示该仓库包含训练、评估、推理后处理、ProtBERT 嵌入辅助代码及若干 TCR/MHC 数据字典；未见许可证或 checkpoint，且未执行任何脚本。

## 可复用模块与资源

### datasets

- `data/trajs.tsv`
  - 能力：training_dataset
  - 用途：TCR α 链 J 相关表（按路径名推断）
  - 复用状态：blocked；类型：unknown
- `data/travs.tsv`
  - 能力：training_dataset
  - 用途：TCR α 链 V 相关表（按路径名推断）
  - 复用状态：blocked；类型：unknown
- `data/trbjs.tsv`
  - 能力：training_dataset
  - 用途：TCR β 链 J 相关表（按路径名推断）
  - 复用状态：blocked；类型：unknown
- `data/trbvs.tsv`
  - 能力：training_dataset
  - 用途：TCR β 链 V 相关表（按路径名推断）
  - 复用状态：blocked；类型：unknown

### evaluation

- `src/test_results.py`
  - 能力：evaluation_entrypoint
  - 用途：测试/评估结果检查
  - 复用状态：blocked；类型：code_entry
- `src/sgather_results.py`
  - 能力：result_aggregator
  - 用途：多轮/多折结果汇总
  - 复用状态：blocked；类型：code_entry

### inference

- `src/get_results.py`
  - 能力：prediction_postprocess
  - 用途：结果生成/推理后处理（按文件名推断）
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `src/EPICTRACE_model.py`
  - 能力：model_architecture
  - 用途：EPIC-TRACE 主模型结构定义
  - 复用状态：blocked；类型：code_entry
- `protBERT/bert_mdl.py`
  - 能力：embedding_helper
  - 用途：ProtBERT 相关模型/嵌入辅助封装
  - 复用状态：blocked；类型：code_entry
- `protBERT/get_embs.py`
  - 能力：embedding_extraction
  - 用途：序列嵌入生成与缓存
  - 复用状态：blocked；类型：code_entry
- `data/MHC_all_dict.bin`
  - 能力：supporting_dictionary
  - 用途：MHC 映射字典
  - 复用状态：blocked；类型：unknown
- `data/MHC_lvl2nd_dict.bin`
  - 能力：supporting_dictionary
  - 用途：MHC 二级层级映射字典
  - 复用状态：blocked；类型：unknown
- `data/MHC_lvl3rd_dict.bin`
  - 能力：supporting_dictionary
  - 用途：MHC 三级层级映射字典
  - 复用状态：blocked；类型：unknown

### training

- `src/train.py`
  - 能力：training_entrypoint
  - 用途：训练入口与训练循环
  - 复用状态：blocked；类型：code_entry
- `scripts/runEPICTRACE.sh`
  - 能力：pipeline_launcher
  - 用途：端到端运行/训练封装脚本
  - 复用状态：blocked；类型：code_entry
- `scripts/cv_split.sh`
  - 能力：data_split
  - 用途：交叉验证切分脚本
  - 复用状态：blocked；类型：code_entry
- `src/split.py`
  - 能力：data_split
  - 用途：数据切分逻辑
  - 复用状态：blocked；类型：code_entry
- `src/construct_long.py`
  - 能力：preprocess
  - 用途：样本/序列构造预处理
  - 复用状态：blocked；类型：code_entry
- `src/SWA.py`
  - 能力：optimization_helper
  - 用途：Stochastic Weight Averaging 训练辅助
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清点，未执行任何脚本或测试
- 依赖未安装，无法验证训练/推理/评估链路
- 未见 LICENSE，代码/数据/模型复用边界未清晰授权
- 未见可用 checkpoint，无法确认已保存权重

## 仍未知

- protBERT/ 目录是否为第三方改写、捆绑或自研封装，无法仅凭路径确认
- src/get_results.py 与 src/sgather_results.py 的精确职责仅凭文件名推断
- data/*.tsv 与 data/*.bin 的生成来源、许可和可再分发条件未确认
- 仓库是否存在未纳入冻结清单的大文件或外部下载资源未知

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
