# Wang-lab-UCSD/AntPack

- **仓库：** [https://github.com/Wang-lab-UCSD/AntPack](https://github.com/Wang-lab-UCSD/AntPack)
- **固定 commit：** `1828e0a850021f36c6ec7b2e1d711d0087b89aab`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** found
- **资产记录数：** 16

## 仓库摘要

仓库是 AntPack 的抗体/TCR 序列分析工具包，核心能力集中在编号注释、V/J 基因分配、序列评分、EM 聚类与本地数据库工具；未见明确训练入口或显式 checkpoint，主要依赖静态参考表、参数数组与测试夹具。

## 可复用模块与资源

### datasets

- `src/antpack/numbering_tools/consensus_data/mabs/IMGT_CONSENSUS_H.npy`
  - 能力：抗体编号参考表
  - 用途：IMGT/Kabat/Martin/AHO/CTermFinder 的抗体编号 consensus 与 k-mer 参考
  - 复用状态：ready_for_review；类型：unknown
- `src/antpack/numbering_tools/consensus_data/tcrs/TCR_AV.npy`
  - 能力：TCR 编号参考表
  - 用途：为 TCR 序列编号与注释提供 V/J 相关参考表
  - 复用状态：ready_for_review；类型：unknown
- `src/antpack/scoring_tools/model_data/human_heavy_mixweights.npy`
  - 能力：序列评分参数数组
  - 用途：提供 human_heavy 与 human_light mixture weights / mu 参数，供 sequence scoring 读取
  - 复用状态：ready_for_review；类型：unknown
- `src/antpack/vj_tools/consensus_data/human_imgt_IGHV_2025-03-14.fa.gz`
  - 能力：V/J germline 参考 FASTA
  - 用途：为 human/mouse/rabbit/alpaca 的 IGH/IGK/IGL/TRA/TRB/TRD/TRG V/J assignment 提供参考序列
  - 复用状态：ready_for_review；类型：unknown
- `tests/test_data/test_data.csv.gz`
  - 能力：测试夹具数据
  - 用途：为单元测试与集成测试提供样例输入与预期数据
  - 复用状态：ready_for_review；类型：unknown

### evaluation

- `.github/workflows/test.yml`
  - 能力：CI 构建与测试
  - 用途：在 GitHub Actions 中运行测试套件与构建检查
  - 复用状态：ready_for_review；类型：config
- `tests/numbering_tools/test_single_chain_annotator.py`
  - 能力：单元/集成测试套件
  - 用途：覆盖 numbering、clustering、database、scoring 与 VJ 工具的静态测试
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `src/antpack/scoring_tools/sequence_scoring_tool.py`
  - 能力：序列评分推理
  - 用途：对输入序列运行 scoring 流程并调用参数表完成打分
  - 复用状态：ready_for_review；类型：code_entry
- `src/antpack/vj_tools/vj_gene_assignment.py`
  - 能力：V/J gene assignment 推理
  - 用途：对输入序列执行 V/J 基因归属
  - 复用状态：ready_for_review；类型：code_entry
- `src/antpack/numbering_tools/paired_chain_annotator.py`
  - 能力：单链/配对编号推理
  - 用途：对输入抗体或 TCR 序列执行编号与注释
  - 复用状态：ready_for_review；类型：code_entry
- `src/antpack/database_tools/local_db_search.py`
  - 能力：本地数据库搜索推理
  - 用途：对本地构建的序列库执行查询与检索
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/antpack/numbering_tools/single_chain_annotator.py`
  - 能力：抗体/ TCR 序列编号与注释
  - 用途：对单链抗体序列做编号与区域注释，并配合配对链与 C-terminus 处理逻辑使用
  - 复用状态：ready_for_review；类型：code_entry
- `src/antpack/clustering_tools/em_categorical_mixture.py`
  - 能力：EM categorical mixture 聚类
  - 用途：对分类特征序列做 EM 混合模型聚类与打分
  - 复用状态：ready_for_review；类型：code_entry
- `src/antpack/database_tools/local_db_construct.py`
  - 能力：本地数据库构建与搜索
  - 用途：构建并检索本地序列数据库
  - 复用状态：ready_for_review；类型：code_entry
- `src/antpack/utilities/model_loader_utils.py`
  - 能力：模型参数加载与序列评分支撑
  - 用途：读取 human_heavy/light 的 mixture 参数并支撑 sequence scoring 运行
  - 复用状态：ready_for_review；类型：code_entry
- `src/antpack/utilities/vj_utilities.py`
  - 能力：V/J 基因分配辅助
  - 用途：为 V/J gene assignment 提供参考序列处理与工具函数
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清点，未运行任何代码或测试。
- 依赖未安装，仓库代码未执行。
- submodules 未初始化，extern/nanobind 与 extern/antpack_private 的真实内容和许可未核验。
- 存在多个 .gz/.npy 静态大文件，但未验证是否为完整、可复现的资产。
- 静态 path presence 不能证明训练、评估或复现已成功。

## 仍未知

- consensus_data 与 model_data 的来源、构建流程和授权未在冻结证据中确认。
- tests/test_data 是真实外部数据、脱敏样例还是合成夹具，无法仅凭路径判断。
- scoring_tools/model_data 是否可视为 checkpoint 仍不能确认；当前仅能确认其是参数数组。
- 是否有未列入 tracked_paths 的下载资源或生成脚本，冻结清单无法排除。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
