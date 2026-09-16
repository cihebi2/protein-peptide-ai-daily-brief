# n-mourdou/admetrix

- **仓库：** [https://github.com/n-mourdou/admetrix](https://github.com/n-mourdou/admetrix)
- **固定 commit：** `6802d695115680bc4f93c7c904d8fea7bb60fd95`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** found
- **资产记录数：** 23

## 仓库摘要

这是一个以 ADMET 约束的 de novo molecular generation / scaffold hopping 为核心的仓库，含生成、服务、评估与少量数据/权重资产，但没有可验证的训练入口或已执行复现证据。

## 可复用模块与资源

### checkpoints

- `src/priors/reinvent.prior`
  - 能力：REINVENT prior 权重
  - 用途：prior-like 生成模型权重/初始化文件，可能作为生成器先验。
  - 复用状态：partial；类型：unknown

### datasets

- `src/data/admet_optimization/admet_properties_train_subset.csv`
  - 能力：ADMET 训练/优化数据
  - 用途：ADMET 属性子集，供优化或条件生成使用。
  - 复用状态：partial；类型：unknown
- `src/data/admet_optimization/de_novo_seed_42.csv`
  - 能力：de novo 种子集合
  - 用途：de novo 生成的起始种子之一。
  - 复用状态：partial；类型：unknown
- `src/data/admet_optimization/de_novo_seed_65.csv`
  - 能力：de novo 种子集合
  - 用途：de novo 生成的起始种子之一。
  - 复用状态：partial；类型：unknown
- `src/data/admet_optimization/de_novo_seed_77.csv`
  - 能力：de novo 种子集合
  - 用途：de novo 生成的起始种子之一。
  - 复用状态：partial；类型：unknown
- `src/data/scaffold_hopping/scaffold_hopping.csv`
  - 能力：scaffold hopping 基准数据
  - 用途：scaffold hopping 任务的数据输入/基准集。
  - 复用状态：partial；类型：unknown

### evaluation

- `src/evaluation/eval_utils.py`
  - 能力：评估工具函数
  - 用途：评估流程的公共辅助函数。
  - 复用状态：ready_for_review；类型：code_entry
- `src/evaluation/fcd_computation.py`
  - 能力：FCD 计算
  - 用途：Fréchet ChemNet Distance 相关计算。
  - 复用状态：ready_for_review；类型：code_entry
- `src/evaluation/kl_divergence.py`
  - 能力：KL divergence 计算
  - 用途：KL divergence 相关指标实现。
  - 复用状态：ready_for_review；类型：code_entry
- `src/evaluation/metrics.py`
  - 能力：评估指标汇总
  - 用途：生成分子评估指标的汇总实现。
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `src/admet_optimization.py`
  - 能力：ADMET 驱动分子生成
  - 用途：主生成/优化脚本，承载 ADMET 约束下的分子搜索或生成。
  - 复用状态：ready_for_review；类型：code_entry
- `src/admet_server.py`
  - 能力：推理/服务接口
  - 用途：ADMET 相关的服务端或推理接口。
  - 复用状态：ready_for_review；类型：code_entry
- `src/scaffold_hopping.py`
  - 能力：Scaffold hopping 生成
  - 用途：scaffold hopping 的生成或搜索脚本。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `Dockerfile.admet`
  - 能力：运行环境与容器化
  - 用途：构建 ADMET 工作流的容器环境。
  - 复用状态：ready_for_review；类型：unknown
- `environment.yml`
  - 能力：运行环境依赖
  - 用途：定义 Conda 环境与依赖集合。
  - 复用状态：ready_for_review；类型：config
- `requirements-admet.txt`
  - 能力：运行环境依赖
  - 用途：定义 pip 依赖约束。
  - 复用状态：ready_for_review；类型：unknown
- `src/conf/config.yaml`
  - 能力：全局配置
  - 用途：项目级配置入口。
  - 复用状态：ready_for_review；类型：config
- `src/admet_optimization.toml`
  - 能力：ADMET 优化参数
  - 用途：ADMET 优化流程的参数/recipe 配置。
  - 复用状态：ready_for_review；类型：config
- `src/scaffold_hopping.toml`
  - 能力：Scaffold hopping 参数
  - 用途：scaffold hopping 流程的参数/recipe 配置。
  - 复用状态：ready_for_review；类型：config
- `src/utils.py`
  - 能力：共享工具函数
  - 用途：被生成、优化或评估脚本复用的通用辅助函数。
  - 复用状态：ready_for_review；类型：code_entry

### training

- `src/data/admet_optimization/guacamol_v1_train.smiles`
  - 能力：生成模型训练语料
  - 用途：分子生成模型的训练语料。
  - 复用状态：partial；类型：unknown
- `src/data/admet_optimization/reinvent_training_data.txt`
  - 能力：生成模型训练语料
  - 用途：REINVENT 风格生成模型的训练文本语料。
  - 复用状态：partial；类型：unknown
- `src/data/admet_optimization/reinvnet_congif.toml`
  - 能力：训练/优化 recipe
  - 用途：REINVENT 相关训练或优化流程的配置文件。
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做静态库存审查，未运行代码、未安装依赖、未执行测试。
- 未发现可验证的训练入口或独立 data_loader；训练与推理角色主要依据文件名与路径判断。
- 未发现明确的 checkpoint 目录；`src/priors/reinvent.prior` 只能作为 prior-like 权重文件处理。
- bundle 数据的来源、授权与可再分发边界未从静态清单中确认。
- 子模块未初始化，且存在大 blob/Promisor 风险，实际内容可能不完整。

## 仍未知

- `src/priors/reinvent.prior` 的具体格式、来源与授权状态未知。
- `guacamol_v1_train.smiles` 与 `reinvent_training_data.txt` 的来源及是否为第三方数据未核实。
- `src/admet_optimization.py` 与 `src/scaffold_hopping.py` 的精确执行路径、输入输出和是否包含训练逻辑未验证。
- `src/ADMETrix_results.ipynb` 未纳入本次资产分层判断。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。

## 2026-09-16 复审补充（mass-review 批次）

- **复用度（复审）：** high —— 完整多目标生成管线：附带 REINVENT 预训练先验（reinvent.prior）、GuacaMol 训练 SMILES、多 seed 生成结果、骨架跳跃数据与评测模块；但需另装增强版 REINVENT4 fork 与 ADMET AI（Docker 可选），许可为 Research Use Only
- **许可证（复审）：** research_use_only（自定义 Research Use Only 许可，非 OSI 标准协议）
- **能力（复审）：** training_pipeline、inference、benchmark、data_loader、visualization

**课题关联：**

- C003多端点（27 个 ADMET 端点+10 理化描述符的多目标优化是直接同构问题）
- C002肽毒性（含毒性降低的骨架跳跃示范，方法论可迁移）
- C007条件生成（性质约束下的从头生成）
- C008基准校准（GuacaMol FCD/KL 评测指标实现）

**与论文/课题的组合方式：**

- 与
- 多
- 端
- 点
- 优
- 化
- 课
- 题
- （
- C
- 0
- 0
- 3
- ）
- 组
- 合
- ：
- 其
-  
- 2
- 7
-  
- 端
- 点
- 奖
- 励
- 加
- 权
- 方
- 案
- 与
-  
- G
- u
- a
- c
- a
- M
- o
- l
-  
- 评
- 测
- （
- F
- C
- D
- /
- K
- L
- ）
- 可
- 直
- 接
- 作
- 为
- 分
- 子
- 端
- 多
- 目
- 标
- 生
- 成
- 的
- 参
- 照
- 实
- 现
- ；
- 毒
- 性
- 骨
- 架
- 跳
- 跃
- （
- 双
- 氯
- 芬
- 酸
- 案
- 例
- ）
- 可
- 与
-  
- C
- 0
- 0
- 2
-  
- 联
- 用
- 研
- 究
- 毒
- 性
- 降
- 低
- 的
- 结
- 构
- 操
- 作
- 。
