# aoulas/scRANK

- **仓库：** [https://github.com/aoulas/scRANK](https://github.com/aoulas/scRANK)
- **固定 commit：** `83e2ae778dd6a1999bf0ecec0b7603a6909d52f1`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 8

## 仓库摘要

该冻结快照是一个 R 包 scRANK，围绕单细胞 RNA-seq 的 cluster ranking、CellChat、外部数据库/MalaCards 检索与结果可视化；未见训练入口、数据集或 checkpoints，且未发现许可证文件。

## 可复用模块与资源

### evaluation

- `R/plotCellRank.R`
  - 能力：ranking 结果可视化与诊断
  - 用途：绘制 ranking 结果，便于人工检查输出是否合理。
  - 复用状态：blocked；类型：code_entry
- `man/plotProportions.Rd`
  - 能力：输出摘要图
  - 用途：展示比例与 DEG 总量等摘要信息，属于结果诊断而非正式 benchmark。
  - 复用状态：blocked；类型：unknown

### inference

- `R/cellScan.R`
  - 能力：cell cluster ranking / scoring
  - 用途：对输入单细胞数据输出 cluster ranking 或分数。
  - 复用状态：blocked；类型：code_entry
- `R/searchDatabases.R`
  - 能力：数据库驱动的先验知识检索
  - 用途：运行时查询数据库以支撑 ranking 与后续分析。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `R/seuratBasic.R`
  - 能力：基础单细胞分析
  - 用途：封装基础分析流程，供输入 scRNA-seq/Seurat 对象调用。
  - 复用状态：blocked；类型：code_entry
- `R/cellChat.R`
  - 能力：CellChat 分析流程
  - 用途：运行并展示 CellChat 相关分析。
  - 复用状态：blocked；类型：code_entry
- `R/malacardsConn.R`
  - 能力：外部数据库与 MalaCards 知识连接
  - 用途：查询外部数据库并提取 Malacards 先验知识，支撑排名流程。
  - 复用状态：blocked；类型：code_entry
- `README.md`
  - 能力：包说明与元数据
  - 用途：提供包级说明、命名空间与品牌资源。
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态清点，未执行代码、测试或安装依赖
- tracked inventory 未显示 bundled data、训练入口或 checkpoints
- 文件内容未逐行审计，实际输入输出和运行时下载行为未验证
- 仓库许可证缺失，直接复用受阻

## 仍未知

- `DESCRIPTION` / `NAMESPACE` 的具体依赖声明未解析
- 各 R 函数内部算法细节与参数契约未核验
- 是否存在运行时外部数据下载或隐藏资源不可确认

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
