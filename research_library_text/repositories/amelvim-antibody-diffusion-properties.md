# amelvim/antibody-diffusion-properties

- **仓库：** [https://github.com/amelvim/antibody-diffusion-properties](https://github.com/amelvim/antibody-diffusion-properties)
- **固定 commit：** `7a29262fe0e4ecf036a1f632a75af22c66226c2a`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 18

## 仓库摘要

该仓库是 antibody diffusion 共设计与 developability 评估代码包，包含核心生成模型、训练/推理/评估脚本、对接与松弛封装、示例结构和一个 ddG checkpoint；静态审计仅能确认代码为 Apache-2.0，数据与权重的独立许可和来源仍需单独核验。

## 可复用模块与资源

### checkpoints

- `diffab/tools/ddg/data/model.pt`
  - 能力：ddG 预训练权重
  - 用途：属性/ΔΔG 预测模型参数。
  - 复用状态：blocked；类型：model_weight

### datasets

- `data/examples/3QHF_Fv.pdb`
  - 能力：示例结构集
  - 用途：提供 3QHF_Fv、7DK2_AB_C、Omicron_RBD 等示例输入。
  - 复用状态：blocked；类型：unknown
- `data/sabdab_summary_all.tsv`
  - 能力：SAbDab 汇总表
  - 用途：SAbDab 相关样本与元数据索引。
  - 复用状态：blocked；类型：unknown

### evaluation

- `eval.py`
  - 能力：评估入口与指标
  - 用途：总评估入口，调用 energy、hydropathy、similarity 指标实现。
  - 复用状态：ready_for_review；类型：code_entry
- `configs/test/abopt_singlecdr.yml`
  - 能力：评估 recipes
  - 用途：abopt_singlecdr、codesign_*、fixbb、strpred 等测试/评估配置。
  - 复用状态：ready_for_review；类型：config

### inference

- `diffab/utils/inference.py`
  - 能力：推理核心
  - 用途：采样、候选生成与推理调度。
  - 复用状态：ready_for_review；类型：code_entry
- `design_pdb.py`
  - 能力：设计 CLI
  - 用途：面向单结构/复合物的设计脚本；同类脚本还包括 design_dock.py、design_testset.py 及 diffab/tools/runner/*。
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `diffab/models/diffab.py`
  - 能力：核心 antibody diffusion 共设计模型
  - 用途：联合生成抗体序列与结构的主模型入口。
  - 复用状态：ready_for_review；类型：code_entry
- `diffab/modules/common/geometry.py`
  - 能力：几何与结构基础模块
  - 用途：SO(3)、几何、拓扑与结构表示的底层算子。
  - 复用状态：ready_for_review；类型：code_entry
- `diffab/utils/transforms/mask.py`
  - 能力：输入选择与补丁变换
  - 用途：残基/原子选择、mask、merge、patch 等样本变换与预处理。
  - 复用状态：ready_for_review；类型：code_entry
- `diffab/datasets/sabdab.py`
  - 能力：SAbDab 数据集装配与读取
  - 用途：训练数据读取、自定义数据集组织与样本构建。
  - 复用状态：ready_for_review；类型：code_entry
- `diffab/tools/dock/hdock.py`
  - 能力：对接工作流封装
  - 用途：antibody-antigen docking 的工具封装与调用流程。
  - 复用状态：partial；类型：code_entry
- `diffab/tools/relax/run.py`
  - 能力：结构松弛工作流封装
  - 用途：OpenMM 与 PyRosetta relax 流程封装。
  - 复用状态：partial；类型：code_entry
- `diffab/tools/ddg/predictor.py`
  - 能力：ddG / developability 预测模块
  - 用途：属性打分与辅助引导的预测器代码。
  - 复用状态：partial；类型：code_entry

### training

- `train.py`
  - 能力：训练入口
  - 用途：启动训练并调度共享训练逻辑。
  - 复用状态：ready_for_review；类型：code_entry
- `diffab/utils/train.py`
  - 能力：训练共享模块
  - 用途：训练循环、优化与日志等通用逻辑。
  - 复用状态：ready_for_review；类型：code_entry
- `configs/train/codesign_fv.yml`
  - 能力：训练 recipes
  - 用途：codesign_single、codesign_multicdrs、codesign_fv、fixbb、strpred 等训练配置。
  - 复用状态：ready_for_review；类型：config
- `diffab/datasets/sabdab.py`
  - 能力：训练数据管道
  - 用途：SAbDab 读取与自定义数据集封装，用于训练样本构建。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审计，未执行仓库代码或测试。
- 依赖未安装，外部二进制/工具链（如 HDOCK、OpenMM、PyRosetta）未验证。
- 大文件可能仍受 promisor/blob 限制，静态存在不等于内容完整可用。
- 路径存在不能证明训练、推理或评估在该提交上真实跑通。
- 未见核心生成模型的独立 checkpoint，复现完整结果仍不确定。

## 仍未知

- `data/examples/*.pdb` 与 `data/sabdab_summary_all.tsv` 的上游来源、筛选规则和再分发条款未核实。
- `diffab/tools/ddg/data/model.pt` 的训练数据、训练流程与模型来源未核实。
- 主扩散模型是否还有未跟踪的权重文件未知。
- 对接与松弛封装是否依赖仓库外部可用的命令行工具未知。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
