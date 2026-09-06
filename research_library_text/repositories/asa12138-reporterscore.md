# Asa12138/ReporterScore

- **仓库：** [https://github.com/Asa12138/ReporterScore](https://github.com/Asa12138/ReporterScore)
- **固定 commit：** `8df9e8cbd68c04face69e030273f7e536b26c6bc`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 19

## 仓库摘要

该仓库是 ReporterScore 论文对应的 R 包实现，包含 ReporterScore 计算、KO/Pathway 富集、KEGG 网络、绘图和示例数据；但未发现 LICENSE、训练入口或 checkpoint，且仅能做静态审阅，不能证明可复现执行。

## 可复用模块与资源

### datasets

- `data/KO_abundance_test.rda`
  - 能力：KO 丰度示例数据
  - 用途：示例/测试用 KO abundance 数据，支撑演示与文档示例。
  - 复用状态：blocked；类型：unknown
- `data/reporter_score_res.rda`
  - 能力：结果对象示例
  - 用途：示例输出或参考结果对象，用于文档与结果展示。
  - 复用状态：blocked；类型：unknown
- `data/KO_htable.rda`
  - 能力：KO 参考表
  - 用途：KO 层级/映射参考数据。
  - 复用状态：blocked；类型：unknown
- `data/KOlist.rda`
  - 能力：KO 列表
  - 用途：KO 索引/字典型参考数据。
  - 复用状态：blocked；类型：unknown
- `data/Pathway_htable.rda`
  - 能力：Pathway 参考表
  - 用途：Pathway 映射与层级参考数据。
  - 复用状态：blocked；类型：unknown
- `data/Module_htable.rda`
  - 能力：Module 参考表
  - 用途：Module 映射与层级参考数据。
  - 复用状态：blocked；类型：unknown
- `data/Compound_htable.rda`
  - 能力：Compound 参考表
  - 用途：Compound 映射与层级参考数据。
  - 复用状态：blocked；类型：unknown
- `data/CPDlist.rda`
  - 能力：Compound 列表
  - 用途：Compound 索引/字典型参考数据。
  - 复用状态：blocked；类型：unknown
- `data/genedf.rda`
  - 能力：基因注释/映射表
  - 用途：基因到功能条目的映射或注释数据。
  - 复用状态：blocked；类型：unknown
- `data/hsa_kegg_pathway.rda`
  - 能力：人类 KEGG pathway 参考数据
  - 用途：人类 pathway 映射或网络参考数据。
  - 复用状态：blocked；类型：unknown
- `data/mmu_kegg_pathway.rda`
  - 能力：小鼠 KEGG pathway 参考数据
  - 用途：小鼠 pathway 映射或网络参考数据。
  - 复用状态：blocked；类型：unknown

### evaluation

- `.github/workflows/R-CMD-check.yaml`
  - 能力：R 包静态验证与站点构建
  - 用途：CI 检查、pkgdown 构建和 PR 命令验证；仅见配置，未见执行结果。
  - 复用状态：blocked；类型：config

### inference

- `R/enrichment.R`
  - 能力：ReporterScore/富集推断
  - 用途：对输入丰度矩阵或 KO 列表计算得分与富集结果；属于分析推断步骤，不是训练。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `R/calculation.R`
  - 能力：ReporterScore 计算主流程
  - 用途：对输入 omics/KO 表计算 ReporterScore，并串联后续结果汇总。
  - 复用状态：blocked；类型：code_entry
- `R/enrichment.R`
  - 能力：富集分析接口集合
  - 用途：封装 KO_enrich、KO_gsea、KO_gsva、KO_padog、KO_safe、KO_sea、KO_fisher 等分析接口。
  - 复用状态：blocked；类型：code_entry
- `R/kegg_net.R`
  - 能力：KEGG/路径网络工具
  - 用途：处理 pathway network、KEGG map 与网络索引相关辅助逻辑。
  - 复用状态：blocked；类型：code_entry
- `R/plot.R`
  - 能力：绘图与报告输出
  - 用途：输出 feature、network、significance、report 等可视化与报告图。
  - 复用状态：blocked；类型：code_entry
- `R/data.R`
  - 能力：包内数据加载与检查
  - 用途：提供内置数据加载、更新与辅助函数入口。
  - 复用状态：blocked；类型：code_entry
- `README.Rmd`
  - 能力：文档与示例工作流
  - 用途：展示安装、用法、流程图和示例输出。
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态审阅；未运行任何 R 代码、未安装依赖、未执行测试。
- 仓库未发现 LICENSE；代码与数据的直接复用均缺少明确授权边界。
- `.rda` 数据文件的真实来源、是否由第三方数据库导入或二次整理，无法仅凭路径确认。
- CI/workflow 只能证明配置存在，不能证明测试通过或结果可复现。
- 未发现训练入口、模型 checkpoint 或可执行权重文件。

## 仍未知

- `data/*` 中哪些对象是项目自制、哪些可能是从 KEGG/GO/CARD/CAZy 等第三方资源整理而来，不明。
- `update_*`/`load_*` 相关函数是否包含联网更新或外部抓取逻辑，未做内容级验证。
- README/vignette 中的图示与示例结果是否完全由仓库内路径重现，不明。
- 由于未读取文件内容，无法确认每个函数的精确输入输出契约。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
