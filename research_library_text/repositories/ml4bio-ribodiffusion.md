# ml4bio/RiboDiffusion

- **仓库：** [https://github.com/ml4bio/RiboDiffusion](https://github.com/ml4bio/RiboDiffusion)
- **固定 commit：** `3ac7a557f470c25d95379acedf75a9a49f70ef6e`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 6

## 仓库摘要

该仓库主要提供 RNA inverse folding 的生成式扩散模型实现与推理配置；可见 8 个 split TSV 和 1 个示例 PDB，但未发现独立训练入口、评测脚本或 checkpoint。代码许可证为 MIT，但数据与示例结构的许可边界未在静态清单中明确。

## 可复用模块与资源

### datasets

- `split_data/seq_identity_0.8_split_0.tsv`
  - 能力：sequence-identity split metadata
  - 用途：序列同一性 0.8 的预定义划分元数据；同系列还包括 split_1~3.tsv
  - 复用状态：partial；类型：unknown
- `split_data/struct_tmscore_0.6_split_0.tsv`
  - 能力：structure-TMscore split metadata
  - 用途：结构 TM-score 0.6 的预定义划分元数据；同系列还包括 split_1~3.tsv
  - 复用状态：partial；类型：unknown
- `example/R1107.pdb`
  - 能力：example RNA structure input
  - 用途：示例三维结构输入/演示样本，可供推理流程验证但不等同于训练数据集
  - 复用状态：partial；类型：unknown

### inference

- `configs/inference_ribodiffusion.py`
  - 能力：inference recipe
  - 用途：定义推理/采样参数、模型绑定与输入输出配置
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `models/GVP_diff.py`
  - 能力：RNA inverse folding generative diffusion model
  - 用途：定义结构条件下的序列生成/去噪主干，并与 EMA、ESM block、Transformer 层协同构成核心模型
  - 复用状态：ready_for_review；类型：code_entry
- `datasets/utils.py`
  - 能力：dataset loader and split utilities
  - 用途：读取和整理 split_data 下的划分文件，并为推理输入提供数据组织逻辑
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态盘点，未执行代码、未安装依赖、未运行测试，不能证明可运行性或复现性。
- 未发现 checkpoint 文件，当前冻结仓库未静态暴露可复用权重。
- 训练入口与评测脚本未被冻结清单识别，完整训练/评测链条不完整。
- 数据与示例结构的上游来源和许可边界未在仓库静态证据中明确。

## 仍未知

- main.py、run_lib.py、sampling.py 在未运行情况下的真实角色未确认。
- split_data/*.tsv 仅能确认存在预定义划分文件，不能从静态清单判断其是否覆盖全部训练/验证/测试语义。
- example/R1107.pdb 的来源（自有示例或外部结构派生）未能确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
