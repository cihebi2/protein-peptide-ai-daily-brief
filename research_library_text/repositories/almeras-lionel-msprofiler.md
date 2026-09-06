# Almeras-Lionel/MSProfileR

- **仓库：** [https://github.com/Almeras-Lionel/MSProfileR](https://github.com/Almeras-Lionel/MSProfileR)
- **固定 commit：** `f106bf3eeeae2bf36c583a924afa39d14f5368d6`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 19

## 仓库摘要

这是一个GPL-3.0授权的R包，提供MALDI-TOF MS谱图的加载、预处理、峰检测、对齐、分箱、特征矩阵构建、注释与报告导出；未见训练产物、模型检查点或可执行的学习型管线。

## 可复用模块与资源

### datasets

- `data/Legs_Guiana_Culex.rda`
  - 能力：示例谱图数据
  - 用途：包内示例数据，供教程和演示分析使用
  - 复用状态：partial；类型：unknown
- `data/Thorax_Guiana_Culex.rda`
  - 能力：示例谱图数据
  - 用途：包内示例数据，供教程和演示分析使用
  - 复用状态：partial；类型：unknown

### evaluation

- `R/conformityTests.R`
  - 能力：一致性/同质性检查
  - 用途：对谱图或样本集合做一致性测试
  - 复用状态：ready_for_review；类型：code_entry
- `R/conformitySpectra.R`
  - 能力：谱图一致性分析
  - 用途：评估谱图之间的一致性并辅助筛选
  - 复用状态：ready_for_review；类型：code_entry
- `R/computePeakCountsBySNR.R`
  - 能力：峰质量统计
  - 用途：按 signal-to-noise ratio 统计峰数量，作为质量诊断指标
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `R/runMSProfileR.R`
  - 能力：顶层分析入口
  - 用途：对输入谱图运行整套分析工作流
  - 复用状态：ready_for_review；类型：code_entry
- `R/runProcessing.R`
  - 能力：处理流水线入口
  - 用途：对选定数据执行处理流程
  - 复用状态：ready_for_review；类型：code_entry
- `R/executePreprocessing.R`
  - 能力：预处理执行
  - 用途：将预处理参数应用到谱图集合
  - 复用状态：ready_for_review；类型：code_entry
- `R/executeProcessing.R`
  - 能力：后处理执行
  - 用途：将处理参数应用到已预处理的数据
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `R/loadSpectra.R`
  - 能力：谱图加载与流程入口
  - 用途：读取输入谱图并交给后续预处理/处理链
  - 复用状态：ready_for_review；类型：code_entry
- `R/executePreprocessing.R`
  - 能力：预处理编排
  - 用途：串联清洗、截断、筛峰、对齐等预处理步骤
  - 复用状态：ready_for_review；类型：code_entry
- `R/cleanSpectra.R`
  - 能力：谱图清洗与截断
  - 用途：对原始谱图做清洗，并配合截断处理输入区间
  - 复用状态：ready_for_review；类型：code_entry
- `R/detectPeaks_.R`
  - 能力：峰检测
  - 用途：检测谱峰并供后续筛选、对齐和统计使用
  - 复用状态：ready_for_review；类型：code_entry
- `R/alignSpectra_.R`
  - 能力：峰对齐与分箱
  - 用途：跨样本对齐峰位，并与分箱/合并逻辑协同
  - 复用状态：ready_for_review；类型：code_entry
- `R/computeIntensityMatrix.R`
  - 能力：特征矩阵构建
  - 用途：把峰信息汇总为 intensity matrix，供统计、筛选和可视化使用
  - 复用状态：ready_for_review；类型：code_entry
- `R/computeReferencePeaks.R`
  - 能力：参考峰与一致性分析
  - 用途：构建参考峰并辅助一致性检查与下游筛选
  - 复用状态：ready_for_review；类型：code_entry
- `R/processAnnotations.R`
  - 能力：注释处理
  - 用途：读取、整理并写回样本注释
  - 复用状态：ready_for_review；类型：code_entry
- `R/writeReport.R`
  - 能力：报告与图表导出
  - 用途：生成报告、图表与压缩输出
  - 复用状态：ready_for_review；类型：code_entry
- `R/writeH5File.R`
  - 能力：结果导出
  - 用途：导出 HDF5 等中间或最终结果文件
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审计，未执行仓库代码、测试或工作流
- 依赖未安装，无法验证运行时行为、外部包和实际输出
- 仓库中未见训练入口、训练模块或 checkpoints 文件
- 数据与教程文件的具体来源和再许可范围未能从静态清单完全确认
- 仅依据文件路径和静态清单归纳功能，未读取源码内容

## 仍未知

- data/Legs_Guiana_Culex.rda 与 data/Thorax_Guiana_Culex.rda 的精确来源、授权和可再分发条件
- vignettes/MS-profileR_tutorial_V1.0.Rmd 与生成的 PDF 是否包含额外外部素材
- 若存在隐式依赖或生成文件，其许可和可复用性未在清单中显式呈现
- 各 helper 函数的具体算法细节未经过源码级逐行核验

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
