# anphan0828/CAFA_forever

- **仓库：** [https://github.com/anphan0828/CAFA_forever](https://github.com/anphan0828/CAFA_forever)
- **固定 commit：** `c3fd5b9a5226348d88b9efadddb3214c803b80c4`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 12

## 仓库摘要

仓库主要是一个以 Nextflow + Streamlit/React 实现的蛋白功能注释方法纵向评测与展示平台，包含多轮 release 的 ground truth 与评估结果 TSV，但未见训练入口或 checkpoint。

## 可复用模块与资源

### datasets

- `data/releases/Sep_2025_Nov_2025/groundtruth_LK.tsv`
  - 能力：ground truth labels
  - 用途：不同 release window 的 ground truth / benchmark 标签
  - 复用状态：partial；类型：unknown
- `data/releases/Sep_2025_Nov_2025/method_names.tsv`
  - 能力：method catalog and availability
  - 用途：方法名称、可用性与比较视图索引
  - 复用状态：partial；类型：unknown
- `data/releases/Sep_2025_Nov_2025/groundtruth_targets.tsv`
  - 能力：target selection metadata
  - 用途：定义评测目标集合与 terms of interest
  - 复用状态：partial；类型：unknown

### evaluation

- `workflows/evaluate_window.nf`
  - 能力：window-level scoring pipeline
  - 用途：按 release window 计算评估指标并汇总结果
  - 复用状态：ready_for_review；类型：unknown
- `workflows/evaluate_late_predictions.nf`
  - 能力：late-prediction evaluation
  - 用途：评估 late predictions / longitudinal 更新
  - 复用状态：ready_for_review；类型：unknown
- `data/releases/Sep_2025_Nov_2025/results_LK/evaluation_all.tsv`
  - 能力：stored benchmark outputs
  - 用途：保存各方法的评估结果，供榜单和图表读取
  - 复用状态：partial；类型：unknown

### inference

- `app/config.py`
  - 能力：interactive release browsing
  - 用途：加载冻结 release 数据并配置 Streamlit 视图
  - 复用状态：ready_for_review；类型：config
- `frontend/src/hooks/useReleaseData.ts`
  - 能力：client-side data loading
  - 用途：前端读取 release / comparison 数据并驱动图表
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `main.nf`
  - 能力：release window orchestration
  - 用途：组织 release window/timepoint 构建与流水线入口
  - 复用状态：ready_for_review；类型：unknown
- `app/streamlit_app.py`
  - 能力：dashboard app
  - 用途：读取冻结 TSV 并提供交互式比较与可视化
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/publish_release_windows.py`
  - 能力：release publishing and data prep
  - 用途：发布 release 窗口与整理批次数据
  - 复用状态：ready_for_review；类型：code_entry
- `frontend/src/components/charts/PRCurvePlot.tsx`
  - 能力：frontend comparison UI
  - 用途：前端 PR/Fmax 等评估图表的渲染组件
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审计，未执行代码、测试或 Nextflow/Streamlit/React 流程。
- 依赖未安装，frontend 与 Python/Nextflow 运行兼容性未验证。
- 未见 training entrypoint、training module 或 checkpoint，无法确认再训练或模型复现路径。
- 150 个 TSV 主要是 release/groundtruth/results 资源，生成链路与 provenance 仅能由文件名推断。
- 仓库存在 static logos 与前端资源，但未展开其第三方授权边界。

## 仍未知

- groundtruth/results TSV 是否为外部 CAFA 基准导入还是仓库内生成，静态证据不足。
- method_availability / method_names 的更新规则与来源未能从文件名确认。
- evaluation 指标定义、阈值和排序规则需要运行 workflow 才能验证。
- front-end 静态资源与 logo 的版权/商标授权未单独披露。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
