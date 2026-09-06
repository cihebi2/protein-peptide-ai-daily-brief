# basiralab/SPHERE

- **仓库：** [https://github.com/basiralab/SPHERE](https://github.com/basiralab/SPHERE)
- **固定 commit：** `10c0ae0f045b6382a757219a73dd99652679f048`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 8

## 仓库摘要

该仓库在冻结清单中主要是四个学科目录下的 JSON/JSONL 资源与 LICENSE/README；未发现方法代码、训练入口、推理入口、评估脚本或 checkpoint。

## 可复用模块与资源

### datasets

- `biology/annotated_biology_sentences.jsonl`
  - 能力：biology annotated sentence corpus
  - 用途：生物学句子标注语料；可作为后续信息抽取或知识图谱构建输入
  - 复用状态：partial；类型：unknown
- `biology/final_biology_knowledge_graph.json`
  - 能力：biology knowledge graph export
  - 用途：生物学知识图谱导出结果；可作为下游分析或对照资源
  - 复用状态：partial；类型：config
- `computer_science/computer_science.jsonl`
  - 能力：computer science sentence corpus
  - 用途：计算机科学语料/句子集合；可作为后续结构化抽取输入
  - 复用状态：partial；类型：unknown
- `computer_science/final_cs_knowledge_graph.json`
  - 能力：computer science knowledge graph export
  - 用途：计算机科学知识图谱导出结果；可作为下游分析或对照资源
  - 复用状态：partial；类型：config
- `material_science/annotated_materials_sentences.jsonl`
  - 能力：materials science annotated sentence corpus
  - 用途：材料科学句子标注语料；可作为后续信息抽取或知识图谱构建输入
  - 复用状态：partial；类型：unknown
- `material_science/final_materials_knowledge_graph_4_levels.json`
  - 能力：materials science knowledge graph export
  - 用途：材料科学知识图谱导出结果；可作为下游分析或对照资源
  - 复用状态：partial；类型：config
- `physics/annotated_physics_sentences.jsonl`
  - 能力：physics annotated sentence corpus
  - 用途：物理学句子标注语料；可作为后续信息抽取或知识图谱构建输入
  - 复用状态：partial；类型：unknown
- `physics/final_physics_knowledge_graph.json`
  - 能力：physics knowledge graph export
  - 用途：物理学知识图谱导出结果；可作为下游分析或对照资源
  - 复用状态：partial；类型：config

## 使用限制

- 仅做静态清单审计，未执行仓库代码。
- 未发现训练、推理、评估或 checkpoint 路径。
- 未安装依赖，未运行测试。
- path 存在不等于可复现或已验证内容。
- 未见独立数据/模型许可文件。

## 仍未知

- 各 JSON/JSONL 文件的具体字段、标注方案和来源未解析。
- 无法确认这些数据是否完全由本仓库生成，或是否包含第三方版权材料。
- README 内容未在本次证据中展开，因此无法核实其是否描述额外资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
