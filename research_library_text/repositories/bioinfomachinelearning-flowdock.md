# BioinfoMachineLearning/FlowDock

- **仓库：** [https://github.com/BioinfoMachineLearning/FlowDock](https://github.com/BioinfoMachineLearning/FlowDock)
- **固定 commit：** `9473b8e5600981950c88f3963cf3871ce8a8d1f2`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 13

## 仓库摘要

该仓库主要提供 FlowDock 的核心模型、数据处理、训练/推理/评估入口与配置，并带有 MOAD/PDBbind 亲和力表、切分文件和测试案例；未见 tracked checkpoint，且静态审查无法证明实际运行或复现。

## 可复用模块与资源

### datasets

- `data/moad/moad_binding_affinity_data/binding_affinity_values.txt`
  - 能力：MOAD/PDBbind 亲和力标签表
  - 用途：监督训练或评估所需的 binding affinity 数值
  - 复用状态：partial；类型：unknown
- `data/splits/timesplit_no_lig_overlap_train`
  - 能力：docking/generalisation 时间切分与验证/测试划分
  - 用途：定义训练/验证/测试 split，支持无 ligand overlap 等实验设置
  - 复用状态：partial；类型：unknown
- `data/test_cases/prediction_inputs/flowdock_batched_inputs.csv`
  - 能力：推理测试用例与示例输出
  - 用途：批量推理输入样例与对应的示例预测结构输出
  - 复用状态：ready_for_review；类型：unknown
- `flowdock/data/components/chemical/ALA.pdb`
  - 能力：标准氨基酸模板与 UFF 参数
  - 用途：标准残基模板、化学几何与参数化输入
  - 复用状态：partial；类型：unknown

### evaluation

- `flowdock/eval.py`
  - 能力：评估入口与指标计算
  - 用途：运行 benchmark 评估并汇总 structure/affinity metrics
  - 复用状态：ready_for_review；类型：code_entry
- `notebooks/dockgen_structure_prediction_results_plotting.ipynb`
  - 能力：离线基准分析笔记本
  - 用途：结果整理、作图与基准对比分析
  - 复用状态：partial；类型：unknown

### inference

- `flowdock/sample.py`
  - 能力：推理/采样入口
  - 用途：生成候选构象、运行批量采样与输出结果
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `flowdock/models/components/flowdock.py`
  - 能力：FlowDock 核心生成式对接模型
  - 用途：主模型封装，统筹 flow matching、构象生成与亲和力预测相关组件
  - 复用状态：ready_for_review；类型：code_entry
- `flowdock/data/components/process_mols.py`
  - 能力：分子与蛋白预处理/featurization 流水线
  - 用途：分子解析、特征构造、chi/physical/residue 编码以及 ESMFold 相关前处理
  - 复用状态：ready_for_review；类型：code_entry
- `configs/train.yaml`
  - 能力：训练/实验配置总入口
  - 用途：Hydra 配置训练、callback、logger、strategy 与模型/数据 recipe
  - 复用状态：ready_for_review；类型：config

### training

- `flowdock/train.py`
  - 能力：训练入口
  - 用途：启动训练流程、装配 model/datamodule/callback/logger
  - 复用状态：ready_for_review；类型：code_entry
- `configs/train.yaml`
  - 能力：训练与实验配置
  - 用途：控制训练参数、设备、日志与回调组合
  - 复用状态：ready_for_review；类型：config
- `scripts/esmfold_prior_training.sh`
  - 能力：前处理/预训练脚本
  - 用途：shell 级训练、分阶段训练与数据下载/准备辅助
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未跑测试。
- submodules 未初始化，且大型 blob 可能仅为 promisor 视图。
- 路径存在不代表数据、训练或评估流程真实执行。
- 未对外部下载器、notebook 以及 shell 脚本的运行结果做复现验证。

## 仍未知

- 化学模板与 UFF 参数的上游来源/许可未在静态清单中明确。
- MOAD/PDBbind 标签表与 split 文件的具体生成流程和再分发边界未完全显式。
- 未发现 tracked checkpoint 文件，无法判断是否遗漏权重资产。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
