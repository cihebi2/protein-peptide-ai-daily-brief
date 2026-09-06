# sirius777coder/gpdl

- **仓库：** [https://github.com/sirius777coder/gpdl](https://github.com/sirius777coder/gpdl)
- **固定 commit：** `aeb718f15cf0e6708db13dd8fca519e98b3966b4`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 20

## 仓库摘要

该仓库是一个面向 protein backbone design 的静态代码库，包含 inpainting/hallucination 推理、训练原型、基准评测 notebook、筛选脚本、PDB/FASTA 数据和一个 checkpoint；本次仅做静态清点，未执行代码。

## 可复用模块与资源

### checkpoints

- `gpdl_inpainting/checkpoints/inpaint_weight_11.pt`
  - 能力：trained inpainting weights
  - 用途：GPDL inpainting 模型参数文件
  - 复用状态：partial；类型：model_weight
- `gpdl_inpainting/esm/pretrained.py`
  - 能力：checkpoint loader shim
  - 用途：预训练权重的定位/加载引用
  - 复用状态：partial；类型：code_entry
- `gpdl_inpainting/esm/esmfold/v1/pretrained.py`
  - 能力：ESMFold checkpoint loader shim
  - 用途：ESMFold 预训练权重引用
  - 复用状态：partial；类型：code_entry

### datasets

- `data/esm_pdb_denovo/1QYS.pdb`
  - 能力：de novo backbone input set
  - 用途：蛋白骨架输入样本/采样语料
  - 复用状态：partial；类型：unknown
- `data/esm_pdb_fasta/1QYS.fasta`
  - 能力：paired sequence record
  - 用途：与结构配对的 FASTA 序列样本
  - 复用状态：partial；类型：unknown
- `data/pdb/1QYS.pdb`
  - 能力：raw PDB input copy
  - 用途：结构输入或预处理源文件
  - 复用状态：partial；类型：unknown
- `gpdl_inpainting/benchmark_set/1BCF.pdb`
  - 能力：benchmark structure set
  - 用途：静态基准评测样本
  - 复用状态：partial；类型：unknown

### evaluation

- `gpdl_inpainting/benchmark.ipynb`
  - 能力：benchmark notebook
  - 用途：静态基准评测与结果展示
  - 复用状态：partial；类型：unknown

### inference

- `gpdl_hallucination/inference_v1.py`
  - 能力：hallucination inference entry
  - 用途：生成候选 backbone/序列的推理脚本
  - 复用状态：partial；类型：code_entry
- `gpdl_hallucination/inference_v2.py`
  - 能力：hallucination inference entry
  - 用途：推理脚本的迭代版本
  - 复用状态：partial；类型：code_entry
- `sample_sequences.py`
  - 能力：sequence sampling demo
  - 用途：示例式序列采样/生成入口
  - 复用状态：partial；类型：code_entry
- `gpdl_inpainting/esm_inference.py`
  - 能力：ESM-backed inpainting inference
  - 用途：调用 ESM/ESMFold 相关组件做推理
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `gpdl_hallucination/hallucination.py`
  - 能力：protein backbone hallucination / proposal generation
  - 用途：生成候选骨架或序列的核心逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `gpdl_hallucination/mutate.py`
  - 能力：mutation / scoring helper
  - 用途：候选序列或结构的扰动与采样辅助
  - 复用状态：ready_for_review；类型：code_entry
- `gpdl_hallucination/loss.py`
  - 能力：loss utility
  - 用途：设计流程中的损失/打分计算辅助
  - 复用状态：ready_for_review；类型：code_entry
- `scripts/fape_loss.py`
  - 能力：geometry loss utility
  - 用途：结构几何相关损失计算
  - 复用状态：ready_for_review；类型：code_entry
- `ProteinMPNN`
  - 能力：external inverse folding toolkit
  - 用途：下游序列恢复/设计依赖，疑似 vendored 依赖
  - 复用状态：partial；类型：unknown
- `gpdl_inpainting/esm/model/esm2.py`
  - 能力：protein language model component
  - 用途：ESM 语言模型/编码器相关实现
  - 复用状态：partial；类型：code_entry

### training

- `gpdl_inpainting/train_poc.py`
  - 能力：prototype training loop
  - 用途：训练/微调原型逻辑
  - 复用状态：partial；类型：code_entry
- `gpdl_inpainting/train_poc.sh`
  - 能力：shell training wrapper
  - 用途：提交训练作业的 shell 封装
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清单，未执行仓库代码、测试或 notebook。
- 缺少 dependencies/config recipe/CI，无法据此确认可复现运行路径。
- 数据与 checkpoint 没有单独冻结许可证明，不能直接当作可自由复用资源。
- 存在大文件与 promisor-only 风险；路径存在不等于可复现结果。

## 仍未知

- `inpaint_weight_11.pt` 是否为最终训练产物、对应训练轮次与数据划分未知。
- `ProteinMPNN` 与 `gpdl_inpainting/esm` 是原样 vendoring 还是本地改写未知。
- `benchmark.ipynb` 中的具体指标、结论与运行条件未验证。
- 训练超参、随机种子、外部下载依赖与环境版本未冻结。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
