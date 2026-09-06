# achillobator/GAHACR

- **仓库：** [https://github.com/achillobator/GAHACR](https://github.com/achillobator/GAHACR)
- **固定 commit：** `f574669a4a828661616dd6b7acbc03baff8b042d`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 13

## 仓库摘要

该仓库主要是围绕 GAHACR 论文的 R/Rmd/notebook 分析与作图工件；可见 DEG、PANTHER、GO 图和校准快照，但未发现 LICENSE、独立 checkpoint 或可验证的训练/推理入口。

## 可复用模块与资源

### datasets

- `Ambient_GAHACR_DEG_caller/counts.txt`
  - 能力：计数矩阵
  - 用途：DEG caller 的输入 count 数据
  - 复用状态：blocked；类型：unknown
- `Ambient_GAHACR_DEG_caller/metadat.txt`
  - 能力：样本元数据
  - 用途：样本分组和注释元信息
  - 复用状态：blocked；类型：unknown
- `GO_analysis_Supplemental 3B/All_Degs_panther.txt`
  - 能力：DEG 富集输入/PANTHER 列表
  - 用途：All DEGs 的 PANTHER 结果或输入列表
  - 复用状态：blocked；类型：unknown
- `GO_analysis_Supplemental 3B/Down_panther.txt`
  - 能力：DEG 富集输入/PANTHER 列表
  - 用途：下调 DEGs 的 PANTHER 结果或输入列表
  - 复用状态：blocked；类型：unknown
- `GO_analysis_Supplemental 3B/Up_panther.txt`
  - 能力：DEG 富集输入/PANTHER 列表
  - 用途：上调 DEGs 的 PANTHER 结果或输入列表
  - 复用状态：blocked；类型：unknown

### evaluation

- `GO_analysis_Supplemental 3B/Rplot_all_go_combined.pdf`
  - 能力：GO 富集结果图
  - 用途：All_Degs 的 GO 汇总展示
  - 复用状态：blocked；类型：unknown
- `GO_analysis_Supplemental 3B/Rplot_up_only.pdf`
  - 能力：上调 GO 结果图
  - 用途：上调 DEG 的 GO 可视化
  - 复用状态：blocked；类型：unknown
- `GO_analysis_Supplemental 3B/Up_v2_GO.pdf`
  - 能力：补充 GO 图
  - 用途：补充版 GO 富集图
  - 复用状态：blocked；类型：unknown
- `GA_Model/calibrating_txn_scale/GAI_snap.tiff`
  - 能力：转录校准快照集
  - 用途：GAI、RGA、ubq10 的校准图像快照
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `Ambient_GAHACR_DEG_caller/Ambient_Amaryllis.Rmd`
  - 能力：DEG 分析/R Markdown 工作流
  - 用途：整理 ambient 条件下的 DEG caller 分析流程
  - 复用状态：blocked；类型：unknown
- `GA_Model/GAHACR model.ipynb`
  - 能力：模型分析 notebook
  - 用途：记录 GAHACR 模型构建、调参或结果生成
  - 复用状态：blocked；类型：unknown
- `GO_analysis_Supplemental 3B/GOplot_20220821.R`
  - 能力：GO 富集绘图脚本
  - 用途：生成 GO 富集图和补充图
  - 复用状态：blocked；类型：code_entry

### training

- `GA_Model/GAHACR model.ipynb`
  - 能力：模型训练/参数标定记录
  - 用途：疑似包含模型训练、调参与结果保存；静态清单不足以确认真实训练入口
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅静态清单审查，未执行代码或测试
- dependencies 未安装，submodules 未初始化
- 路径存在不等于可复现、已训练或已推理

## 仍未知

- `GA_Model/GAHACR model.ipynb` 是否包含真实训练或独立推理入口无法确认
- `GA_Model/calibrating_txn_scale/*.tiff` 更像图像快照而非 checkpoint
- 未发现 LICENSE，第三方与衍生内容的权属不明

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
