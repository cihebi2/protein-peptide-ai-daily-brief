# GfellerLab/MixMHCpred

- **仓库：** [https://github.com/GfellerLab/MixMHCpred](https://github.com/GfellerLab/MixMHCpred)
- **固定 commit：** `c29e4db17abe6266bfee72750efb713459540d18`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 13

## 仓库摘要

该仓库是 MixMHCpred 的静态预测资源包，核心为 MHC-I ligand/presentation 打分代码、长度 8–14 的 PWM/权重文件与多物种/多等位基因参考表；未见训练或正式评测入口，且标准 LICENSE 未发现。

## 可复用模块与资源

### checkpoints

- `lib/weights/weights_M8.npy`
  - 能力：learned weight arrays
  - 用途：长度 8–14 的 learned weights
  - 复用状态：blocked；类型：unknown
- `lib/Length_weights.npy`
  - 能力：辅助数值参数
  - 用途：长度权重与 substitution matrix 更新参数
  - 复用状态：blocked；类型：unknown

### datasets

- `lib/MHC_I_sequences.txt`
  - 能力：MHC-I 序列与位点参考
  - 用途：allele 序列、对齐与 binding-site 注释
  - 复用状态：unknown；类型：unknown
- `lib/proteome/AA_frequency_human_Methionine.csv`
  - 能力：背景 proteome n-mer 采样
  - 用途：背景频率与长度分布采样库
  - 复用状态：unknown；类型：unknown
- `input/test.fasta`
  - 能力：示例/测试输入
  - 用途：仓库自带的示例输入或对齐样例
  - 复用状态：unknown；类型：unknown

### evaluation

- `output/out_compare.txt`
  - 能力：示例比较输出
  - 用途：静态样例输出；未见完整 benchmark harness
  - 复用状态：unknown；类型：unknown

### inference

- `code/MixMHCpred.py`
  - 能力：推理入口与核心打分逻辑
  - 用途：加载预训练参数并对输入肽段/序列进行 MHC-I 打分与排序
  - 复用状态：blocked；类型：code_entry
- `lib/pwm/class1_8/PWM_A0101_1.csv`
  - 能力：PWM/核 motif 查表
  - 用途：按长度和等位基因读取 PWM/alphas 进行序列评分
  - 复用状态：blocked；类型：unknown
- `lib/PerRank/A0201.txt`
  - 能力：rank/长度校准
  - 用途：对原始打分进行 allele rank 归一化和偏置修正
  - 复用状态：unknown；类型：unknown

### reusable_assets

- `code/MixMHCpred.py`
  - 能力：推理入口与核心打分逻辑
  - 用途：加载预训练参数并对输入肽段/序列进行 MHC-I 打分与排序
  - 复用状态：blocked；类型：code_entry
- `lib/pwm/class1_8/PWM_A0101_1.csv`
  - 能力：allele-specific PWM/motif 资产
  - 用途：8–14mer 的 PWM CSV 与 motif PNG，供查表打分或解释输出
  - 复用状态：blocked；类型：unknown
- `lib/PerRank/A0101.txt`
  - 能力：per-allele rank 校准表
  - 用途：多等位基因/物种的 rank 归一化与校准
  - 复用状态：blocked；类型：unknown
- `lib/shifts/bias.txt`
  - 能力：长度/偏置参数表
  - 用途：分数的 bias 与标准差校正参数
  - 复用状态：unknown；类型：unknown

## 使用限制

- not_executed_static_analysis_only
- dependencies_not_installed
- repository_code_not_executed
- tests_not_run
- submodules_not_initialized
- large_blobs_over_5MiB_may_be_promisor_only
- path_presence_is_not_reproduction_evidence
- 未发现可识别训练入口或训练模块，仓库更像预训练推理包
- 缺少可确认的机器可读 LICENSE，直接复用边界未闭合

## 仍未知

- MixMHCpred_license.pdf 是否覆盖代码、数据与模型的完整范围未解析
- lib/pwm、lib/PerRank、lib/proteome 中哪些文件是作者生成、哪些是外部导入无法仅凭路径确认
- lib/weights/*.npy 是否为最终发布 checkpoint 还是中间产物无法仅凭静态存在确认

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
