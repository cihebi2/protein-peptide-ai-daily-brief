# mhshuvo1/EquiRank

- **仓库：** [https://github.com/mhshuvo1/EquiRank](https://github.com/mhshuvo1/EquiRank)
- **固定 commit：** `2007e43220300614b9ad59655fe23f3e937312e9`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 8

## 仓库摘要

静态清点显示该仓库围绕 EquiRank 的接口质量估计/decoy 排序流程，包含主程序、MSA/几何特征脚本、外部工具目录、示例输入与 decoy 结构、以及模型权重文件；未发现 LICENSE、训练入口或可执行验证。

## 可复用模块与资源

### checkpoints

- `model/model_weight_dist`
  - 能力：模型权重 bundle
  - 用途：6 个权重文件之一；同目录下还有 lambda、lambdar、omega、tau、taur。
  - 复用状态：unknown；类型：unknown

### datasets

- `example/example.fasta`
  - 能力：示例序列与 MSA/ESM 输入包
  - 用途：示例复现输入；包含 A/B 链的 a3m、aln 与 ESM/npy 特征。
  - 复用状态：unknown；类型：unknown
- `example/example_decoys/decoys_1.pdb`
  - 能力：示例 decoy 结构集
  - 用途：示例接口 decoy，用于排序/评测演示。
  - 复用状态：unknown；类型：unknown

### evaluation

- `example/example_decoys/decoys_1.pdb`
  - 能力：示例评测对象
  - 用途：接口质量估计的静态示例评测对象。
  - 复用状态：unknown；类型：unknown

### inference

- `scripts/generate_rosetta.py`
  - 能力：Rosetta 生成/桥接脚本
  - 用途：推断阶段的 Rosetta 输入/输出准备。
  - 复用状态：unknown；类型：code_entry

### reusable_assets

- `EquiRank.py`
  - 能力：主模型与流水线
  - 用途：主排名/打分入口；按路径名看负责组织接口质量估计流程。
  - 复用状态：blocked；类型：code_entry
- `scripts/distance_generator.py`
  - 能力：特征生成与 MSA 处理
  - 用途：几何距离/方位特征、MSA 处理与拼接。
  - 复用状态：blocked；类型：code_entry
- `apps/dssp`
  - 能力：外部依赖工具集合
  - 用途：第三方结构/暴露度/MSA 相关辅助工具目录。
  - 复用状态：unknown；类型：unknown

## 使用限制

- 仅做静态清点，未执行代码、未安装依赖。
- 未发现 LICENSE 文件，直接复用受限。
- 模型权重与外部工具的上游许可/来源未从冻结证据中确认。
- 示例数据与 decoy 仅能证明存在，不能证明可复现训练或评测。
- 未见明确训练入口或独立评测脚本，无法从静态证据验证流程完整性。

## 仍未知

- README 内容未展开，无法核实安装/运行声明。
- model/model_weight_* 是否为训练产物、转换产物或第三方权重，静态路径本身无法确认。
- apps/* 中外部工具是否完整、是否含二进制或源码、以及对应许可证均未确认。
- example/*.npy 与 example_decoys/*.pdb 是否为项目自制示例还是外部数据派生，无法仅凭路径判断。
- LFS/large blob 是否为完整文件仍不确定；路径存在不等于可复现。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
