# AGI4Sci/SciForge

- **仓库：** [https://github.com/AGI4Sci/SciForge](https://github.com/AGI4Sci/SciForge)
- **固定 commit：** `d477916b38cfb46bb61673283869418feab8c466`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 18

## 仓库摘要

仓库是 SciForge 的大型多包代码库，重点覆盖科研协作、证据/项目 DAG、内容空间、模型路由与多模态工作流；冻结清单未发现训练入口、模型权重或可验证的运行复现。

## 可复用模块与资源

### checkpoints

- `packages/domains/research-checkpoints/src/main.ts`
  - 能力：research checkpoint 管理
  - 用途：研究产物 checkpoint 时间线、恢复与加密存储
  - 复用状态：partial；类型：code_entry
- `packages/domains/git-checkpoints/src/main.ts`
  - 能力：git checkpoint 运行时
  - 用途：基于 git 的 checkpoint 编排、服务与恢复流程
  - 复用状态：partial；类型：code_entry

### datasets

- `packages/domains/dataset-api/examples/ensembl-access-plan.json`
  - 能力：示例数据访问计划
  - 用途：Bundled 示例 access plan，用于 dataset API 流程演示
  - 复用状态：partial；类型：config
- `packages/domains/dataset-api/examples/multi-source-synthesis-plan.json`
  - 能力：多源合成计划示例
  - 用途：Bundled 多源合成计划示例，用于流程与集成测试
  - 复用状态：partial；类型：config
- `packages/domains/scientific-plotting/src/fixtures/single-cell/matrix-v1.mtx`
  - 能力：single-cell fixture 集
  - 用途：单细胞矩阵、features 与 barcodes 等测试/演示数据
  - 复用状态：partial；类型：unknown
- `packages/domains/scientific-plotting/src/fixtures/treatment-response.csv`
  - 能力：tabular plotting fixture
  - 用途：绘图与解析测试用的示例表格数据
  - 复用状态：partial；类型：unknown

### evaluation

- `packages/domains/evidence-dag/python/evidence_dag/metrics.py`
  - 能力：证据 DAG 指标
  - 用途：证据/复现相关指标定义与汇总
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/scientific-plotting-style-regression.mjs`
  - 能力：绘图样式回归评估
  - 用途：scientific plotting 输出样式回归检查
  - 复用状态：ready_for_review；类型：unknown
- `scripts/scientific-plotting-alphafold3-eval.mjs`
  - 能力：AlphaFold3 相关评估脚本
  - 用途：面向 AlphaFold3 的绘图/评估联动检查
  - 复用状态：ready_for_review；类型：unknown
- `packages/workers/sci-modality-router/tests/e2e_real_models.py`
  - 能力：真实模型端到端验证
  - 用途：真实模型链路的端到端验证
  - 复用状态：partial；类型：code_entry

### inference

- `packages/workers/model-router/src/router.ts`
  - 能力：模型路由与 trace 脱敏
  - 用途：统一上游模型请求路由、请求卫生、trace 关联与红action
  - 复用状态：ready_for_review；类型：code_entry
- `packages/workers/sci-modality-router/provider/server.py`
  - 能力：科学模态路由
  - 用途：按 protein、molecule、protein_structure、singlecell 等专家分发请求
  - 复用状态：ready_for_review；类型：code_entry
- `packages/workers/image-generation/src/image-generation-engine.ts`
  - 能力：图像生成管线
  - 用途：生成式图像工作流与视觉产物生成
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `packages/domains/evidence-dag/python/evidence_dag/model.py`
  - 能力：证据图与可复现性引擎
  - 用途：证据图、溯源、快照与复现相关核心逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `packages/domains/project-dag/python/project_dag/compiler.py`
  - 能力：项目 DAG 编译与判定
  - 用途：项目级 workflow 编译、判定、provenance 与存储
  - 复用状态：ready_for_review；类型：code_entry
- `packages/domains/content-space/src/main/index.ts`
  - 能力：内容空间与 OpenContent 连接层
  - 用途：provider 目录、验证策略、原生文档与内容空间编排
  - 复用状态：ready_for_review；类型：code_entry
- `packages/collaboration-server/src/service.ts`
  - 能力：协作服务与远程审批运行时
  - 用途：认证、API、远程审批、provider runtime 与数据库迁移支撑
  - 复用状态：ready_for_review；类型：code_entry
- `packages/domains/dataset-api/src/plan-executor.ts`
  - 能力：数据计划执行与资源编排
  - 用途：dataset plan 执行、对象存储与资源 provider 组合
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- 冻结清单未显示任何模型权重/ML checkpoint 二进制；checkpoint 仅体现为代码层管理模块。
- bundled 数据、图片、示例和第三方资源的独立许可边界未完全核实。
- large blobs 大于 5MiB 可能仅以 promisor/未完整取回状态存在；路径存在不代表可复现。

## 仍未知

- 外部模型/provider、云端服务与真实运行时行为未验证。
- 示例数据、图像和生成物的原始来源与单独许可仍不明确。
- 是否存在未跟踪的生成产物、私有配置或下载器副作用无法从静态清单确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
