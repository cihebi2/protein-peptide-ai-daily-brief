# abhik1368/aop-visualizer-clean

- **仓库：** [https://github.com/abhik1368/aop-visualizer-clean](https://github.com/abhik1368/aop-visualizer-clean)
- **固定 commit：** `3c2f0b8b50f8e7ea12a88215b5b71ee0056cd408`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 24

## 仓库摘要

仓库是一个面向 AOP（Adverse Outcome Pathway）可视化与路径分析的前后端项目，核心内容集中在数据预处理、超图/网络图展示、搜索与路径发现；静态清单未显示训练或 checkpoint 资产，且未找到仓库级许可证文件，复用边界需保守。

## 可复用模块与资源

### datasets

- `data/aop_chemical.csv`
  - 能力：AOP chemical table
  - 用途：化学实体/关系数据源
  - 复用状态：blocked；类型：unknown
- `data/aop_gene.csv`
  - 能力：AOP gene table
  - 用途：基因实体/关系数据源
  - 复用状态：blocked；类型：unknown
- `data/aop_ke_ec.tsv`
  - 能力：key event relation table
  - 用途：AOP 关键事件到 EC 关系数据
  - 复用状态：blocked；类型：unknown
- `data/aop_ke_ker.tsv`
  - 能力：key event relation table
  - 用途：AOP 关键事件到 KER 关系数据
  - 复用状态：blocked；类型：unknown
- `data/aop_ke_mie_ao.tsv`
  - 能力：key event relation table
  - 用途：AOP 关键事件到 MIE/AO 关系数据
  - 复用状态：blocked；类型：unknown

### evaluation

- `tests/test_pathfinding.py`
  - 能力：pathfinding tests
  - 用途：验证路径发现行为
  - 复用状态：blocked；类型：code_entry
- `tests/test_pathfinding_algorithms.py`
  - 能力：algorithm tests
  - 用途：验证路径算法实现
  - 复用状态：blocked；类型：code_entry
- `tests/test_graph_data.py`
  - 能力：graph data tests
  - 用途：检查图数据结构与内容
  - 复用状态：blocked；类型：code_entry
- `tests/test_hypergraph.py`
  - 能力：hypergraph tests
  - 用途：检查超图构建与表示
  - 复用状态：blocked；类型：code_entry
- `tests/test_backend.py`
  - 能力：backend tests
  - 用途：验证后端服务与接口
  - 复用状态：blocked；类型：code_entry
- `tests/pathfinding_demo.py`
  - 能力：demo/guide
  - 用途：路径发现演示脚本
  - 复用状态：blocked；类型：code_entry
- `tests/PATHFINDING_GUIDE.md`
  - 能力：documentation guide
  - 用途：路径发现使用说明/操作步骤
  - 复用状态：blocked；类型：unknown
- `tests/FULL_DATABASE_PATHFINDING_COMPLETE.md`
  - 能力：completion note
  - 用途：全库路径发现完成记录
  - 复用状态：blocked；类型：unknown

### inference

- `backend/src/main.py`
  - 能力：runtime backend
  - 用途：运行时后端服务与数据查询接口
  - 复用状态：blocked；类型：code_entry
- `backend/src/clean_data_loader.py`
  - 能力：runtime data loading
  - 用途：加载清洗后的 AOP 实体与关系数据
  - 复用状态：blocked；类型：code_entry
- `backend/src/hypergraph_utils.py`
  - 能力：runtime graph logic
  - 用途：路径检索、超图遍历与图结构处理
  - 复用状态：blocked；类型：code_entry
- `backend/src/aop_search_index.json`
  - 能力：derived runtime index
  - 用途：AOP 搜索索引/检索加速数据
  - 复用状态：blocked；类型：config
- `backend/src/clean_aop_entities.json`
  - 能力：derived entity cache
  - 用途：清洗后的 AOP 实体缓存
  - 复用状态：blocked；类型：config

### reusable_assets

- `backend/src/data_preprocessor.py`
  - 能力：data preprocessing
  - 用途：AOP 数据清洗、标准化与预处理入口
  - 复用状态：blocked；类型：code_entry
- `backend/src/hypergraph_utils.py`
  - 能力：graph/path utilities
  - 用途：超图构建、关系遍历与路径发现辅助逻辑
  - 复用状态：blocked；类型：code_entry
- `backend/src/main.py`
  - 能力：backend service
  - 用途：后端 API/服务入口，承载数据查询与图分析接口
  - 复用状态：blocked；类型：code_entry
- `frontend/src/components/HypergraphNetworkGraph.jsx`
  - 能力：frontend visualization
  - 用途：超图网络可视化组件
  - 复用状态：blocked；类型：code_entry
- `frontend/src/components/NetworkGraph.jsx`
  - 能力：frontend visualization
  - 用途：普通网络图展示组件
  - 复用状态：blocked；类型：code_entry
- `frontend/src/components/SearchPanel.jsx`
  - 能力：frontend search/UI
  - 用途：AOP 搜索与筛选交互面板
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅进行了静态清单审查；未执行仓库代码、未安装依赖、未运行测试。
- 仓库未见 LICENSE 文件，代码重用边界保守。
- `frontend/vite-cache/deps` 这类构建缓存/打包依赖应视为 vendored_third_party，而非项目原创贡献。
- 数据文件的上游来源与数据许可未在静态清单中得到确认。

## 仍未知

- `backend/src/aop_search_index.json` 与 `backend/src/clean_aop_entities.json` 的具体生成流程、输入来源与许可未核验。
- `frontend/vite-cache/deps` 中各第三方包的精确版本与上游许可证未逐一核验。
- 测试目录中的“complete/guide/demo”文档是否对应真实 CI 结果，静态证据不足。
- `data/README.md` 与各 TSV/CSV 的数据出处未读取，无法确认是否含外部汇编数据。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
