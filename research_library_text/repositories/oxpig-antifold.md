# oxpig/antifold

- **仓库：** [https://github.com/oxpig/antifold](https://github.com/oxpig/antifold)
- **固定 commit：** `789d46786624c01eb44f177ef4c0deeeb6e77469`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** BSD-3-Clause
- **资产记录数：** 30

## 仓库摘要

该仓库静态呈现为 AntiFold 的抗体结构基础逆折叠与设计实现：包含 GVP/Transformer 模型代码、示例 PDB/CSV 输入、推理脚本与测试脚本；未见独立训练入口、正式评测流水线或已跟踪的权重文件，示例数据的来源与授权仅凭静态清单仍不完全确定。

## 可复用模块与资源

### checkpoints

- `antifold/esm/pretrained.py`
  - 能力：pretrained checkpoint loader
  - 用途：检查点/权重选择与加载的邻接代码；冻结清单中未见实际权重 blob
  - 复用状态：partial；类型：code_entry

### datasets

- `data/antibody_antigen.csv`
  - 能力：antibody-antigen example inputs
  - 用途：示例配对输入表；与同目录 PDB 一起构成演示数据
  - 复用状态：partial；类型：unknown
- `data/antibody_antigen/3hfm.pdb`
  - 能力：antibody-antigen example structure
  - 用途：示例结构文件；用于配对/设计演示
  - 复用状态：partial；类型：unknown
- `data/example_pdbs.csv`
  - 能力：example PDB manifest
  - 用途：示例结构清单；用于批量演示输入
  - 复用状态：partial；类型：unknown
- `data/mini.csv`
  - 能力：mini example manifest
  - 用途：更小规模的示例输入清单
  - 复用状态：partial；类型：unknown
- `data/nanobody.csv`
  - 能力：nanobody example inputs
  - 用途：nanobody 示例输入表
  - 复用状态：partial；类型：unknown
- `data/nanobody/8oi2_imgt.pdb`
  - 能力：nanobody example structure
  - 用途：nanobody 示例结构文件
  - 复用状态：partial；类型：unknown
- `data/nanobody/nanobody_antigen_9hzj_imgt.pdb`
  - 能力：nanobody-antigen example structure
  - 用途：nanobody-抗原配对示例结构
  - 复用状态：partial；类型：unknown
- `data/pdbs/6y1l_imgt.pdb`
  - 能力：PDB example structure
  - 用途：示例 PDB 结构输入
  - 复用状态：partial；类型：unknown
- `data/pdbs/8ee8_imgt.pdb`
  - 能力：PDB example structure
  - 用途：示例 PDB 结构输入
  - 复用状态：partial；类型：unknown
- `data/pdbs/C143_immunebuilder.pdb`
  - 能力：PDB example structure
  - 用途：示例 PDB 结构输入
  - 复用状态：partial；类型：unknown

### evaluation

- `test/default.sh`
  - 能力：default smoke test wrapper
  - 用途：默认示例/冒烟测试脚本
  - 复用状态：partial；类型：code_entry
- `test/antibody_antigen.sh`
  - 能力：antibody-antigen test wrapper
  - 用途：针对 antibody-antigen 示例的测试脚本
  - 复用状态：partial；类型：code_entry
- `test/nanobody_antigen.sh`
  - 能力：nanobody-antigen test wrapper
  - 用途：针对 nanobody-antigen 示例的测试脚本
  - 复用状态：partial；类型：code_entry
- `test/tests.sh`
  - 能力：test aggregator
  - 用途：测试聚合/调度脚本
  - 复用状态：partial；类型：code_entry

### inference

- `antifold/main.py`
  - 能力：structure-based design inference entrypoint
  - 用途：主推理入口；用于根据结构输入生成候选序列
  - 复用状态：partial；类型：code_entry
- `run_example.sh`
  - 能力：example inference wrapper
  - 用途：示例推理执行脚本；封装仓库的演示流程
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `antifold/main.py`
  - 能力：antibody inverse-folding CLI（artifact_kind=code_entry）
  - 用途：主入口脚本；从结构输入生成设计结果的推理/运行调度点
  - 复用状态：ready_for_review；类型：code_entry
- `run_example.sh`
  - 能力：example inference wrapper（artifact_kind=code_entry）
  - 用途：示例运行封装；用于调用仓库的例子流程
  - 复用状态：ready_for_review；类型：code_entry
- `antifold/esm/inverse_folding/gvp_encoder.py`
  - 能力：GVP encoder module（artifact_kind=unknown）
  - 用途：逆折叠模型的编码器实现模块
  - 复用状态：ready_for_review；类型：code_entry
- `antifold/esm/inverse_folding/gvp_transformer.py`
  - 能力：GVP transformer module（artifact_kind=unknown）
  - 用途：GVP/Transformer 结构的核心建模模块
  - 复用状态：ready_for_review；类型：code_entry
- `antifold/esm/inverse_folding/gvp_transformer_encoder.py`
  - 能力：GVP transformer encoder stack（artifact_kind=unknown）
  - 用途：编码器堆栈与特征流转接实现
  - 复用状态：ready_for_review；类型：code_entry
- `antifold/esm/inverse_folding/transformer_decoder.py`
  - 能力：Transformer decoder module（artifact_kind=unknown）
  - 用途：序列解码模块；支持候选氨基酸序列生成
  - 复用状态：ready_for_review；类型：code_entry
- `antifold/esm/inverse_folding/util.py`
  - 能力：inverse-folding helper utilities（artifact_kind=unknown）
  - 用途：结构/序列处理的辅助函数集合
  - 复用状态：ready_for_review；类型：code_entry
- `antifold/esm/inverse_folding/features.py`
  - 能力：feature extraction helpers（artifact_kind=unknown）
  - 用途：模型输入特征构建的辅助模块
  - 复用状态：ready_for_review；类型：code_entry
- `antifold/esm/data.py`
  - 能力：data loader helpers（artifact_kind=unknown）
  - 用途：数据读取与批处理辅助代码
  - 复用状态：ready_for_review；类型：code_entry
- `antifold/if1_dataset.py`
  - 能力：IF1 dataset helper（artifact_kind=unknown）
  - 用途：仓库自带的数据集组织/样本构建辅助
  - 复用状态：ready_for_review；类型：code_entry
- `antifold/esm_util_custom.py`
  - 能力：custom ESM helper utilities（artifact_kind=unknown）
  - 用途：围绕 ESM/逆折叠流程的定制辅助代码
  - 复用状态：ready_for_review；类型：code_entry
- `antifold/esm_multichain_util_custom.py`
  - 能力：custom multichain helper utilities（artifact_kind=unknown）
  - 用途：多链输入/上下文处理的定制辅助代码
  - 复用状态：ready_for_review；类型：code_entry
- `antifold/_anarci/ImmunoPDB.py`
  - 能力：ANARCI/ImmunoPDB helper（artifact_kind=unknown）
  - 用途：抗体编号/结构处理的辅助实现
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未安装依赖、未执行代码、未运行测试。
- 未见 tracked 的实际模型权重文件；`antifold/esm/pretrained.py` 仅表明存在检查点邻接逻辑。
- 示例 PDB/CSV 数据的上游来源、再分发权利和衍生关系未能仅凭清单完全确认。
- 测试脚本存在，但没有任何执行结果可证明其在当前冻结环境中可通过。
- `antifold/esm/` 与 `_anarci/` 子树看起来像外来/vendored 代码，但精确上游版本与改动范围未核实。

## 仍未知

- 训练入口与训练数据集未见；无法判断是否存在未跟踪训练流程。
- 实际 checkpoint/weight 文件是否在未跟踪位置存在，静态清单无法确认。
- `output/` 目录中的 CSV/FASTA/log 仅能说明有示例结果，不能证明重新生成。
- 部分代码树可能是 vendored third-party，具体许可证边界与内部改动未逐文件核验。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
