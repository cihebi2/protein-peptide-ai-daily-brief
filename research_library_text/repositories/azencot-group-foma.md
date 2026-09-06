# azencot-group/FOMA

- **仓库：** [https://github.com/azencot-group/FOMA](https://github.com/azencot-group/FOMA)
- **固定 commit：** `d5012c048c175517a5b7221a61ba275aefcc8f4d`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 36

## 仓库摘要

该仓库是 FOMA 论文对应的静态代码仓库，包含 FOMA 与 intrinsic dimension 相关方法、多个回归/视频数据加载器、训练入口与评估辅助模块；未发现 checkpoint 或 bundled data，且仅做静态审查未运行代码。

## 可复用模块与资源

### datasets

- `src/data/airfoil.py`
  - 能力：回归基准数据加载器
  - 用途：加载 Airfoil 回归数据集
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/communities_and_crime.py`
  - 能力：回归基准数据加载器
  - 用途：加载 Communities and Crime 回归数据集
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/no2.py`
  - 能力：回归基准数据加载器
  - 用途：加载 NO2 回归数据集
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/skillcraft.py`
  - 能力：回归基准数据加载器
  - 用途：加载 SkillCraft 回归数据集
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/time_series.py`
  - 能力：时间序列回归数据加载器
  - 用途：加载时间序列回归/预测相关数据
  - 复用状态：ready_for_review；类型：code_entry
- `src/data_generate.py`
  - 能力：合成/规则数据生成
  - 用途：生成实验用合成数据或派生数据
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/dti_dg.py`
  - 能力：DTI domain-generalization 数据加载
  - 用途：加载 DTI DG 实验数据
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/Dti_dg_lib/datasets.py`
  - 能力：DTI 数据集注册/组织
  - 用途：管理 DTI DG 相关数据集定义与拆分
  - 复用状态：ready_for_review；类型：code_entry
- `EchoNet/echonet/datasets/echo.py`
  - 能力：EchoNet 视频数据加载
  - 用途：加载 EchoNet 视频/超声数据
  - 复用状态：partial；类型：code_entry

### evaluation

- `src/data/Dti_dg_lib/model_selection.py`
  - 能力：模型选择/验证
  - 用途：进行验证集选择、模型选择或实验比较
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/Dti_dg_lib/lib/reporting.py`
  - 能力：实验报告汇总
  - 用途：汇总训练/验证结果并输出报告
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/Dti_dg_lib/lib/query.py`
  - 能力：结果查询/检索
  - 用途：检索实验结果、运行记录或统计量
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/Dti_dg_lib/lib/misc.py`
  - 能力：通用评估辅助
  - 用途：提供评估/实验运行中的通用辅助函数
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils.py`
  - 能力：通用评估辅助
  - 用途：支持实验统计、指标计算或结果整理
  - 复用状态：ready_for_review；类型：code_entry
- `EchoNet/echonet/utils/utils.py`
  - 能力：EchoNet 评估辅助
  - 用途：支持 EchoNet 子树的评估或通用实验工具
  - 复用状态：partial；类型：code_entry

### inference

- `PovertyMap/utils.py`
  - 能力：推理前后处理
  - 用途：为 PovertyMap 模型推理提供通用工具、预处理或后处理
  - 复用状态：ready_for_review；类型：code_entry
- `EchoNet/echonet/utils/video.py`
  - 能力：视频推理/IO 辅助
  - 用途：为 EchoNet 视频输入的推理前处理、读取或编码提供支持
  - 复用状态：partial；类型：code_entry
- `EchoNet/echonet/utils/segmentation.py`
  - 能力：推理/评估辅助
  - 用途：为分割或结果处理提供推理辅助
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `src/foma.py`
  - 能力：FOMA 核心增强实现
  - 用途：作为回归任务中的核心 FOMA 数据增强/扰动逻辑复用
  - 复用状态：ready_for_review；类型：code_entry
- `PovertyMap/foma.py`
  - 能力：FOMA 核心增强实现
  - 用途：作为 PovertyMap 子项目中的 FOMA 变体/移植实现复用
  - 复用状态：ready_for_review；类型：code_entry
- `src/intrinsic_dimension.py`
  - 能力：intrinsic dimension 估计
  - 用途：作为 manifold/表示复杂度分析的支撑工具复用
  - 复用状态：ready_for_review；类型：code_entry
- `PovertyMap/intrinsic_dimension.py`
  - 能力：intrinsic dimension 估计
  - 用途：作为 PovertyMap 子项目中的 intrinsic dimension 分析逻辑复用
  - 复用状态：ready_for_review；类型：code_entry
- `EchoNet/echonet/utils/foma.py`
  - 能力：FOMA/视频实验辅助实现
  - 用途：作为 EchoNet 子树中的 FOMA 辅助实现候选，需先确认子树许可边界
  - 复用状态：partial；类型：code_entry
- `EchoNet/echonet/utils/intrinsic_dimension.py`
  - 能力：intrinsic dimension 相关辅助
  - 用途：作为 EchoNet 子树中的 intrinsic dimension 辅助实现候选
  - 复用状态：partial；类型：code_entry

### training

- `src/main.py`
  - 能力：主训练入口
  - 用途：启动 src 子项目的训练/实验流程
  - 复用状态：ready_for_review；类型：code_entry
- `PovertyMap/main.py`
  - 能力：PovertyMap 训练入口
  - 用途：启动 PovertyMap 子项目训练/实验流程
  - 复用状态：ready_for_review；类型：code_entry
- `EchoNet/echonet/__main__.py`
  - 能力：EchoNet 命令行入口
  - 用途：作为 EchoNet 子树的包级 CLI/训练入口候选
  - 复用状态：partial；类型：code_entry
- `src/algorithm.py`
  - 能力：训练流程编排
  - 用途：封装算法选择、训练循环或实验编排
  - 复用状态：ready_for_review；类型：code_entry
- `src/models.py`
  - 能力：模型定义
  - 用途：提供 src 子项目的模型结构
  - 复用状态：ready_for_review；类型：code_entry
- `PovertyMap/model.py`
  - 能力：PovertyMap 模型定义
  - 用途：提供 PovertyMap 任务模型实现
  - 复用状态：ready_for_review；类型：code_entry
- `PovertyMap/models/poverty.py`
  - 能力：PovertyMap 模型实现
  - 用途：提供 PovertyMap 相关模型类
  - 复用状态：ready_for_review；类型：code_entry
- `PovertyMap/resnet_multispectral.py`
  - 能力：多光谱骨干网络
  - 用途：提供多光谱 ResNet 训练骨干
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/Dti_dg_lib/algorithms.py`
  - 能力：DTI DG 算法实现
  - 用途：封装 DTI DG 训练算法或 baseline
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/Dti_dg_lib/networks.py`
  - 能力：DTI DG 网络定义
  - 用途：提供 DTI DG 训练所需网络结构
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/Dti_dg_lib/hparams_registry.py`
  - 能力：超参数注册
  - 用途：提供训练超参数的注册/默认值
  - 复用状态：ready_for_review；类型：code_entry
- `src/data/Dti_dg_lib/lib/fast_data_loader.py`
  - 能力：数据加载加速
  - 用途：为训练循环提供高吞吐数据加载器
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未安装依赖、未运行代码、未跑测试。
- 未发现 checkpoint 文件或 bundled data。
- 仓库中含 EchoNet 子树与 PovertyMap 子树，是否存在第三方移植/再分发边界无法仅凭路径完全确认。
- 数据下载器与真实外部数据源映射未验证。

## 仍未知

- EchoNet/LICENSE.txt 的具体条款未读，子树是否完全 vendored_third_party 仍需确认。
- src/data/Dti_dg_lib 是否源自外部框架或为项目内改写，单靠路径无法判定。
- 各 main.py 是否覆盖全部实验模式、参数默认值与日志/保存路径尚未验证。
- 未见 checkpoint 与数据文件，因此训练复现链条是否完整未知。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
