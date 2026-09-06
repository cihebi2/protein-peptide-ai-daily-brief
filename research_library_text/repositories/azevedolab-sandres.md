# azevedolab/sandres

- **仓库：** [https://github.com/azevedolab/sandres](https://github.com/azevedolab/sandres)
- **固定 commit：** `ce6f5dc81546ed94a4b92d4d664aad42295face5`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 35

## 仓库摘要

这是一个 SAnDReS 2.0 配套仓库：顶层 LICENSE 为 GPL-3.0，仓库中同时包含训练/评测数据、若干已训练模型压缩包、虚拟筛选与 AutoDock Vina 相关工具包，以及案例研究与补充材料；静态清单未显示明确训练入口，且所有压缩包内容均未解包核验。

## 可复用模块与资源

### checkpoints

- `CDK19_IC50_ExtraTreeRegressor.zip`
  - 能力：序列化树模型
  - 用途：看起来是 CDK19 / IC50 的 ExtraTreeRegressor 训练后模型归档
  - 复用状态：partial；类型：unknown
- `CDK2_IC50_ExtraTreeRegressor.zip`
  - 能力：序列化树模型
  - 用途：看起来是 CDK2 / IC50 的 ExtraTreeRegressor 训练后模型归档
  - 复用状态：partial；类型：unknown
- `CDK2_Ki_DecisionTreeRegressorCV.zip`
  - 能力：序列化树模型
  - 用途：看起来是 CDK2 / Ki 的交叉验证决策树回归模型归档
  - 复用状态：partial；类型：unknown
- `Ki_CASF-2016_F14_ExtraTreesRegressorCV.zip`
  - 能力：序列化树模型
  - 用途：看起来是 CASF-2016 F14 相关的 ExtraTreesRegressor 交叉验证模型归档
  - 复用状态：partial；类型：unknown
- `sandres2.zip`
  - 能力：模型/应用打包件
  - 用途：看起来是 SAnDReS 2.0 的综合模型或应用打包件
  - 复用状态：partial；类型：unknown

### datasets

- `affinity_BindingDB_Ki.csv`
  - 能力：亲和力标注表
  - 用途：BindingDB Ki 亲和力数据表，支持回归建模与数据整理
  - 复用状态：partial；类型：unknown
- `cdk19_ic50.tsv`
  - 能力：靶点-活性数据
  - 用途：CDK19 / IC50 相关标签表，支持训练或评测配对数据构建
  - 复用状态：partial；类型：unknown
- `cdk2_ic50.tsv`
  - 能力：靶点-活性数据
  - 用途：CDK2 / IC50 相关标签表，支持训练或评测配对数据构建
  - 复用状态：partial；类型：unknown
- `cdk2_ki.tsv`
  - 能力：靶点-活性数据
  - 用途：CDK2 / Ki 相关标签表，支持训练或评测配对数据构建
  - 复用状态：partial；类型：unknown
- `cdk19_ic50.sdf`
  - 能力：结构输入数据
  - 用途：CDK19 / IC50 的结构化分子文件，可能用于特征提取或对接前处理
  - 复用状态：partial；类型：unknown
- `cdk2_ic50.sdf`
  - 能力：结构输入数据
  - 用途：CDK2 / IC50 的结构化分子文件，可能用于特征提取或对接前处理
  - 复用状态：partial；类型：unknown
- `cdk19_ic50.mol2`
  - 能力：结构输入数据
  - 用途：CDK19 / IC50 的 MOL2 结构文件，可能用于对接或特征工程
  - 复用状态：partial；类型：unknown
- `cdk2_ic50.mol2`
  - 能力：结构输入数据
  - 用途：CDK2 / IC50 的 MOL2 结构文件，可能用于对接或特征工程
  - 复用状态：partial；类型：unknown
- `cdk2_ki.mol2`
  - 能力：结构输入数据
  - 用途：CDK2 / Ki 的 MOL2 结构文件，可能用于对接或特征工程
  - 复用状态：partial；类型：unknown
- `fda_50.mol2`
  - 能力：候选分子集合
  - 用途：50 个 FDA 分子候选集合，可能用于筛选或外部评测
  - 复用状态：partial；类型：unknown
- `taba.mol2`
  - 能力：候选分子集合
  - 用途：单独的分子结构文件，可能用于案例分析或示例筛选
  - 复用状态：partial；类型：unknown
- `pdb_codes.csv`
  - 能力：蛋白结构/条目标识表
  - 用途：PDB 编号与条目索引，支持结构检索与对接输入准备
  - 复用状态：partial；类型：unknown

### evaluation

- `JCC_2024_case_study_1.zip`
  - 能力：案例研究评测包
  - 用途：JCC 2024 case study 1 的评测材料或结果包
  - 复用状态：partial；类型：unknown
- `JCC_2024_case_study_2.zip`
  - 能力：案例研究评测包
  - 用途：JCC 2024 case study 2 的评测材料或结果包
  - 复用状态：partial；类型：unknown
- `JCC_2024_case_study_3.zip`
  - 能力：案例研究评测包
  - 用途：JCC 2024 case study 3 的评测材料或结果包
  - 复用状态：partial；类型：unknown
- `SAnDReS_2_Case_Studies.zip`
  - 能力：综合案例与补充材料
  - 用途：汇总式案例研究材料，可能用于方法展示和评测对照
  - 复用状态：partial；类型：unknown
- `Supplementary_materials.zip`
  - 能力：补充评测材料
  - 用途：补充材料归档，可能含结果表、图或额外评测说明
  - 复用状态：partial；类型：unknown

### inference

- `VS_Convert.zip`
  - 能力：虚拟筛选/对接运行包
  - 用途：看起来用于格式转换或对接前处理的运行包，可能支撑推理流程
  - 复用状态：partial；类型：unknown
- `VS_Vina.zip`
  - 能力：虚拟筛选/对接运行包
  - 用途：看起来用于 Vina 虚拟筛选流程的运行包，可能支撑推理流程
  - 复用状态：partial；类型：unknown
- `pdb.zip`
  - 能力：对接输入准备
  - 用途：蛋白结构或中间输入归档，可能用于推理前准备
  - 复用状态：partial；类型：unknown
- `pdbqt.zip`
  - 能力：对接输入准备
  - 用途：PDBQT 输入归档，可能用于 AutoDock Vina 推理
  - 复用状态：partial；类型：unknown
- `autodock_vina_1_1_2_linux_x86.tgz`
  - 能力：第三方对接执行器
  - 用途：AutoDock Vina Linux 二进制包，提供 docking / inference 执行能力
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `README.md`
  - 能力：项目说明与材料索引
  - 用途：概览仓库结构、材料分组与使用说明，便于定位训练/评测/模型归档
  - 复用状态：partial；类型：unknown
- `scikit_version.py`
  - 能力：环境版本记录
  - 用途：记录或打印 scikit-learn 版本，辅助环境对齐与复现实验说明
  - 复用状态：partial；类型：code_entry

### training

- `IC50.zip`
  - 能力：训练数据归档
  - 用途：IC50 训练或分层数据归档，具体内容未解包核验
  - 复用状态：partial；类型：unknown
- `Ki.zip`
  - 能力：训练数据归档
  - 用途：Ki 训练或分层数据归档，具体内容未解包核验
  - 复用状态：partial；类型：unknown
- `Kd.zip`
  - 能力：训练数据归档
  - 用途：Kd 训练或分层数据归档，具体内容未解包核验
  - 复用状态：partial；类型：unknown
- `bind_IC50.zip`
  - 能力：训练/绑定数据归档
  - 用途：绑定态 IC50 数据包，可能含训练样本或特征文件
  - 复用状态：partial；类型：unknown
- `bind_Ki.zip`
  - 能力：训练/绑定数据归档
  - 用途：绑定态 Ki 数据包，可能含训练样本或特征文件
  - 复用状态：partial；类型：unknown
- `bind_Kd.zip`
  - 能力：训练/绑定数据归档
  - 用途：绑定态 Kd 数据包，可能含训练样本或特征文件
  - 复用状态：partial；类型：unknown

## 使用限制

- not_executed_static_analysis_only
- dependencies_not_installed
- repository_code_not_executed
- tests_not_run
- submodules_not_initialized
- large_blobs_over_5MiB_may_be_promisor_only
- path_presence_is_not_reproduction_evidence

## 仍未知

- 各 zip/tgz 内部到底是源码、序列化模型、数据还是混合包，未解包核验
- 顶层 GPL-3.0 是否覆盖全部数据与模型资产，未见单独许可文件
- 未发现明确训练入口或可执行推理脚本，现有判断主要依赖文件名
- AutoDock Vina 二进制包的再分发条件与平台适配性未核验

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
