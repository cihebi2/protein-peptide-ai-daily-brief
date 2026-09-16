# tyang816/protrem

- **仓库：** [https://github.com/tyang816/protrem](https://github.com/tyang816/protrem)
- **固定 commit：** `7c687ad72b8b1e16eae23e938852c8bd93012b75`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** found
- **资产记录数：** 18

## 仓库摘要

仓库主要围绕蛋白突变零样本打分：包含数据格式转换、MSA/结构特征构建、GVP 风格结构编码、fitness 计算入口与静态 checkpoint；未见可核验训练或完整评测流程。

## 可复用模块与资源

### checkpoints

- `src/structure/static/AE.pt`
  - 能力：model weight / auxiliary checkpoint
  - 用途：static checkpoint loaded by the structure module; whether it is final inference weight or auxiliary autoencoder weight is not confirmed
  - 复用状态：partial；类型：model_weight

### datasets

- `data/pdb_chain_uniprot_plus_current.o2.csv`
  - 能力：PDB/UniProt 映射表
  - 用途：结构与序列对齐的基础表
  - 复用状态：partial；类型：unknown
- `data/pdb_chain_uniprot_plus_current.o2.fasta`
  - 能力：PDB/UniProt 序列集合
  - 用途：与映射表配套的 FASTA 序列资源
  - 复用状态：partial；类型：unknown
- `data/proteingym_v1/DMS_substitutions.csv`
  - 能力：ProteinGym v1 substitution 列表
  - 用途：突变位点/替换定义的输入表
  - 复用状态：partial；类型：unknown
- `data/proteingym_v1/protein_info.csv`
  - 能力：ProteinGym v1 蛋白元数据
  - 用途：样本级蛋白信息与任务索引
  - 复用状态：partial；类型：unknown
- `data/proteingym_v1/aa_seq.tar.gz`
  - 能力：序列归档数据
  - 用途：bundled sequence archive used by preprocessing scripts
  - 复用状态：partial；类型：unknown
- `data/proteingym_v1/pdbs.tar.gz`
  - 能力：结构归档数据
  - 用途：bundled structure archive used by preprocessing scripts
  - 复用状态：partial；类型：unknown
- `data/proteingym_v1/struc_seq.tar.gz`
  - 能力：结构-序列归档数据
  - 用途：bundled structure-sequence archive used by preprocessing scripts
  - 复用状态：partial；类型：unknown
- `data/proteingym_v1/struc_seq_aln_foldseek.tar.gz`
  - 能力：Foldseek 对齐归档
  - 用途：bundled alignment archive used by preprocessing scripts
  - 复用状态：partial；类型：unknown
- `data/proteingym_v1/substitutions.tar.gz`
  - 能力：替换归档数据
  - 用途：bundled substitution archive used by preprocessing scripts
  - 复用状态：partial；类型：unknown

### inference

- `compute_fitness.py`
  - 能力：mutation fitness ranking
  - 用途：primary Python scorer for zero-shot mutation/fitness prediction
  - 复用状态：partial；类型：code_entry
- `script/compute_fitness.sh`
  - 能力：runtime launcher
  - 用途：shell wrapper for the fitness computation pipeline
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `script/data_format_convert.sh`
  - 能力：数据格式转换/预处理
  - 用途：shell wrapper for the data conversion pipeline
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/get_msa.py`
  - 能力：MSA 构建
  - 用途：构建或提取 multiple-sequence alignment 输入
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/get_sav.py`
  - 能力：SAV/突变样本准备
  - 用途：准备 single amino acid variant 相关样本与特征
  - 复用状态：ready_for_review；类型：code_entry
- `src/structure/build_graph.py`
  - 能力：结构图构建
  - 用途：把蛋白结构转换为图输入
  - 复用状态：ready_for_review；类型：code_entry
- `src/structure/encoder/gvp.py`
  - 能力：结构编码模块
  - 用途：GVP 风格结构编码器核心实现
  - 复用状态：ready_for_review；类型：code_entry
- `src/structure/static/1024.joblib`
  - 能力：静态序列化辅助工件
  - 用途：同目录还有 20/64/128/512/2048/4096.joblib；更像索引/缓存而非主权重
  - 复用状态：partial；类型：unknown

## 使用限制

- not_executed_static_analysis_only
- dependencies_not_installed
- repository_code_not_executed
- tests_not_run
- submodules_not_initialized
- large_blobs_over_5MiB_may_be_promisor_only
- path_presence_is_not_reproduction_evidence

## 仍未知

- `compute_fitness.py` 与 `script/compute_fitness.sh` 的真实运行顺序无法仅凭清单确认。
- `src/structure/static/AE.pt` 的训练来源、任务角色与是否为最终推理权重未核实。
- 多个 `data/proteingym_v1/*.tar.gz` 与 `*.csv` 的上游授权条款未从静态清单中解析。
- 未发现可核验的训练入口、系统评测脚本或完整 model architecture 清单。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。

## 2026-09-16 复审补充（mass-review 批次）

- **复用度（复审）：** medium —— 推理管线、数据准备 shell 脚本与环境文件完整且同源序列数据有 HF 全量链接，但模型权重获取路径未在 README 中明示、需依赖 plmc/EVcouplings 外部工具链
- **许可证（复审）：** CC BY-NC-ND 4.0
- **能力（复审）：** data_loader、inference、benchmark、protocol

**课题关联：**

- C005
- C011
- C001

**与论文/课题的组合方式：**

- C
- 0
- 0
- 5
-  
- 表
- 型
- /
- 突
- 变
- 效
- 应
- 课
- 题
- 可
- 用
- 其
-  
- c
- o
- m
- p
- u
- t
- e
- _
- f
- i
- t
- n
- e
- s
- s
- .
- p
- y
-  
- 对
- 自
- 建
-  
- D
- M
- S
- /
- A
- M
- P
-  
- 突
- 变
- 库
- 做
- 零
-  
- s
- h
- o
- t
-  
- 适
- 合
- 度
- 打
- 分
- ；
- P
- r
- o
- t
- e
- i
- n
- G
- y
- m
-  
- 评
- 测
- 协
- 议
- （
- s
- c
- r
- i
- p
- t
- /
-  
- 下
- 全
- 套
- ）
- 可
- 直
- 接
- 作
- 为
-  
- C
- 0
- 1
- 1
-  
- 评
- 估
- 协
- 议
- 课
- 题
- 的
- 参
- 照
- 实
- 现
- 。
