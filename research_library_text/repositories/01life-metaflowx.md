# 01life/MetaflowX

- **仓库：** [https://github.com/01life/MetaflowX](https://github.com/01life/MetaflowX)
- **固定 commit：** `c815413e6bb3216ef8e576bd703cbd0a0321a3f2`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 20

## 仓库摘要

该仓库是一个 MIT 许可的 Nextflow 元基因组分析工作流，覆盖 QC、组装、分箱、重组装/精炼、基因集构建、分类/功能注释与报告；静态清单可见测试样例和第三方数据库快照，但未见训练型模型、checkpoint 或运行验证。

## 可复用模块与资源

### datasets

- `test/data/Sample1_R1.fq.gz`
  - 能力：paired-end smoke-test reads
  - 用途：烟雾测试与示例输入读段
  - 复用状态：partial；类型：unknown
- `test/data/test_minigut_R1.fastq.gz`
  - 能力：additional metagenomic test reads
  - 用途：更完整的示例工作流输入
  - 复用状态：partial；类型：unknown
- `test/database/GTDB/R220/release220/mash/gtdb_ref_sketch.msh`
  - 能力：GTDB reference snapshot
  - 用途：taxonomy/binning 参考数据库快照
  - 复用状态：partial；类型：unknown
- `test/database/EggNOG/eggnog_5.0/eggnog.db`
  - 能力：EggNOG annotation database
  - 用途：功能注释数据库
  - 复用状态：partial；类型：unknown
- `test/database/metaphlan/mpa_vOct22_202403/mpa_vOct22_CHOCOPhlAnSGB_202403.1.bt2l`
  - 能力：taxonomic profiling references
  - 用途：MetaPhlAn/HUMAnN 相关分类学参考
  - 复用状态：partial；类型：unknown
- `test/database/Homo_sapiens/hg38_bowtie2_index/hg38.index.1.bt2`
  - 能力：contamination screening references
  - 用途：宿主去除与污染过滤参考索引
  - 复用状态：partial；类型：unknown
- `docs/Execution_Modes/example_input/clean.csv`
  - 能力：example input tables
  - 用途：不同 execution mode 的示例输入
  - 复用状态：ready_for_review；类型：unknown

### evaluation

- `modules/local/assembly/metaquast.nf`
  - 能力：assembly quality evaluation
  - 用途：评估 assembly 指标并合并 MetaQUAST 结果
  - 复用状态：ready_for_review；类型：unknown
- `modules/local/binning/checkm2.nf`
  - 能力：bin quality evaluation
  - 用途：评估 bins 完整度/污染度并辅助筛选
  - 复用状态：ready_for_review；类型：unknown
- `modules/local/polish/multiQC.nf`
  - 能力：QC aggregation
  - 用途：汇总 QC、assembly 与 binning 结果
  - 复用状态：ready_for_review；类型：unknown
- `docs/MetaflowX_Test_Result/Resource_Requirement_and_Runtimes/Resource_Requirement_and_Runtimes.md`
  - 能力：runtime/resource benchmark outputs
  - 用途：资源与运行时间结果展示
  - 复用状态：partial；类型：unknown

### inference

- `subworkflows/local/RAPID_TAXONOMIC_PROFILING.nf`
  - 能力：taxonomic profiling
  - 用途：从 reads 推断分类组成与丰度
  - 复用状态：ready_for_review；类型：unknown
- `modules/local/marker/humann_v4.nf`
  - 能力：functional profiling
  - 用途：HUMAnN 方式推断功能丰度
  - 复用状态：ready_for_review；类型：unknown
- `modules/local/geneset/eggnog.nf`
  - 能力：gene function annotation
  - 用途：对 gene set 做 EggNOG 注释与功能推断
  - 复用状态：ready_for_review；类型：unknown
- `modules/local/geneset/rgi.nf`
  - 能力：AMR/BGC annotation
  - 用途：抗性基因与次级代谢簇相关注释推断
  - 复用状态：ready_for_review；类型：unknown

### reusable_assets

- `main.nf`
  - 能力：workflow orchestration
  - 用途：顶层 Nextflow 管线编排，串联 QC、assembly、binning、reassembly、注释与报告子流程
  - 复用状态：ready_for_review；类型：unknown
- `subworkflows/local/BINNING.nf`
  - 能力：pipeline subworkflow orchestration
  - 用途：binning 与后续 bin 处理的子工作流编排
  - 复用状态：ready_for_review；类型：unknown
- `bin/preprocess_bin_assembly.py`
  - 能力：preprocessing helper
  - 用途：assembly/binning 前处理与输入整理
  - 复用状态：ready_for_review；类型：code_entry
- `bin/report_main_V20240509.py`
  - 能力：report generation
  - 用途：汇总分析结果并生成最终报告
  - 复用状态：ready_for_review；类型：code_entry
- `modules/nf-core/fastp/main.nf`
  - 能力：vendored QC wrapper
  - 用途：复用 nf-core/fastp 进行 reads 质控
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态清单审查；未执行 Nextflow、脚本、容器或外部数据库流程。
- 依赖未安装，无法验证运行时兼容性与输出正确性。
- 未找到训练入口、模型文件或 checkpoint。
- test/data 与 test/database 中的资源多为第三方或示例性质，许可证未逐项核验。
- 大体积二进制/压缩文件可能为 promisor 或 LFS 占位，静态存在不等于可直接复现。

## 仍未知

- README 与各模块内部实现未逐文件展开，部分脚本的上游来源仍需人工确认。
- docs/MetaflowX_Test_Result 中的图表与报告是否来自真实运行无法仅凭静态文件证明。
- 第三方数据库（GTDB、EggNOG、MetaPhlAn、HUMAnN、VFDB）是否允许再分发，当前证据不足。
- 仓库未见 checkpoints；若作者在外部发布权重，本次未纳入。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
