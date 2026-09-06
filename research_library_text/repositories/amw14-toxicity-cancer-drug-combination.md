# amw14/toxicity-cancer-drug-combination

- **仓库：** [https://github.com/amw14/toxicity-cancer-drug-combination](https://github.com/amw14/toxicity-cancer-drug-combination)
- **固定 commit：** `cb8c7013954ad912f838d6892eeaf4427f61739d`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 8

## 仓库摘要

仓库以 notebook 为主，围绕 DrugBank、DDInter、SyntoX、TargPW、STRING 以及 DeepSynergy/GraphSynergy 做临床毒性与组合疗法分析；仅见 preprocessing_functions.py 这类辅助代码，未见训练入口、推理脚本、checkpoint 或本地数据。MIT 许可仅覆盖代码层。

## 可复用模块与资源

### evaluation

- `00_database_drugbank_ddinter_overview.ipynb`
  - 能力：数据库概览与交互关系清单
  - 用途：概览 DrugBank 与 DDInter 等外部资源，并组织后续对比分析。
  - 复用状态：partial；类型：unknown
- `01A_drugbank_syntox_analysis.ipynb`
  - 能力：DrugBank/DDInter 的 SyntoX 比较分析
  - 用途：比较 DrugBank 与 DDInter 的 SyntoX 毒性注释与差异。
  - 复用状态：partial；类型：unknown
- `02A_drugbank_targpw_analysis.ipynb`
  - 能力：DrugBank/DDInter 的 TargPW 比较分析
  - 用途：比较 DrugBank 与 DDInter 的 TargPW 相关毒性/通路注释。
  - 复用状态：partial；类型：unknown
- `03A_drugbank_avg_string_distance_analysis.ipynb`
  - 能力：STRING 距离分析
  - 用途：基于 STRING 距离度量做毒性相关分析，并有 DrugBank/DDInter 两个版本。
  - 复用状态：partial；类型：unknown
- `03A_drugbank_deeptrasynergy_toxscore.ipynb`
  - 能力：DeepSynergy 毒性评分
  - 用途：用 DeepSynergy 相关分数评估 DrugBank/DDInter 组合的毒性趋势。
  - 复用状态：partial；类型：unknown
- `03A_drugbank_graphsynergy_toxscore.ipynb`
  - 能力：GraphSynergy 毒性评分
  - 用途：用 GraphSynergy 相关分数评估 DrugBank/DDInter 组合的毒性趋势。
  - 复用状态：partial；类型：unknown
- `clinical_tox_disagreement.ipynb`
  - 能力：临床毒性分歧与类别比较
  - 用途：比较临床毒性分歧，并配合交集解析与类别比较 notebook。
  - 复用状态：partial；类型：unknown

### reusable_assets

- `preprocessing_functions.py`
  - 能力：通用预处理/解析辅助
  - 用途：为分析 notebooks 提供可复用的预处理与解析函数。
  - 复用状态：partial；类型：code_entry

## 使用限制

- not_executed_static_analysis_only
- dependencies_not_installed
- repository_code_not_executed
- tests_not_run
- path_presence_is_not_reproduction_evidence

## 仍未知

- 仓库清单未见任何数据文件；DrugBank、DDInter、SyntoX、TargPW、STRING、DeepSynergy、GraphSynergy 更像是 notebook 里引用的外部资源，而不是已打包数据。
- 未见训练入口、模型权重或 checkpoint，无法判断是否存在未跟踪的中间产物。
- 仅有 requirements.txt 作为依赖线索，未安装环境，无法确认 notebooks 是否可直接复现。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
