# 3BioCompBio/StructureDCA

- **仓库：** [https://github.com/3BioCompBio/StructureDCA](https://github.com/3BioCompBio/StructureDCA)
- **固定 commit：** `9c6751cd117d70ce8a91393f8d9646d992dca530`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 18

## 仓库摘要

这是一个 MIT 许可的 StructureDCA 代码仓库，包含序列/结构读取、DCA 数据结构、plmDCA 后端封装、CLI 与教程；未见独立训练入口、正式评测脚本或检查点文件，数据与 vendored 子树需分别核查许可边界。

## 可复用模块与资源

### datasets

- `test_data/B1-beta-lactamases_msa.fasta`
  - 能力：MSA 示例数据
  - 用途：示例/测试用 MSA 输入
  - 复用状态：unknown；类型：unknown
- `test_data/6acv_A_29-94.pdb`
  - 能力：配套结构示例
  - 用途：示例结构输入
  - 复用状态：unknown；类型：unknown
- `test_data/6acv_A_29-94.csv`
  - 能力：配套标签/结果示例
  - 用途：示例结果或标签文件，可能与同名 fasta/pdb 配套
  - 复用状态：unknown；类型：unknown
- `test_data/cMSA_ParE-ParD.a3m`
  - 能力：A3M 示例 MSA
  - 用途：示例/测试用 A3M 输入
  - 复用状态：unknown；类型：unknown
- `test_data/NDM1_trimmed.fasta`
  - 能力：trimmed FASTA 示例
  - 用途：示例/测试用 FASTA 输入
  - 复用状态：unknown；类型：unknown

### evaluation

- `colab_notebook_StructureDCA.ipynb`
  - 能力：Notebook 示例评测
  - 用途：展示完整交互式工作流
  - 复用状态：partial；类型：unknown
- `tutorials/3_sdca-standard-dca.ipynb`
  - 能力：标准 DCA 教程
  - 用途：展示标准 DCA 与 StructureDCA 的比较流程
  - 复用状态：partial；类型：unknown
- `tutorials/4_sdca-ppis.ipynb`
  - 能力：PPI 场景教程
  - 用途：展示 PPIs/接触分析示例流程
  - 复用状态：partial；类型：unknown

### inference

- `structuredca/structuredca.py`
  - 能力：StructureDCA 打分 API
  - 用途：提供主库级预测/打分接口
  - 复用状态：ready_for_review；类型：code_entry
- `structuredca/cli.py`
  - 能力：CLI 推理入口
  - 用途：命令行调用预测与转换流程
  - 复用状态：ready_for_review；类型：code_entry
- `structuredca/aligner/structure_sequence_alignment.py`
  - 能力：结构-序列对齐
  - 用途：将结构坐标映射到序列位置，为推断做预处理
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `structuredca/sequence/fasta_reader.py`
  - 能力：序列/FASTA 解析
  - 用途：读取 FASTA 与序列输入，为后续 DCA 流程准备对象
  - 复用状态：ready_for_review；类型：code_entry
- `structuredca/structure/structure_reader.py`
  - 能力：结构读取
  - 用途：读取 PDB/结构输入，支撑结构感知流程
  - 复用状态：ready_for_review；类型：code_entry
- `structuredca/sequence/msa.py`
  - 能力：MSA 数据结构
  - 用途：表示与操作 MSA，对接 DCA 建模与打分
  - 复用状态：ready_for_review；类型：code_entry
- `structuredca/dca_model/data_structures/sparse_matrix.py`
  - 能力：稀疏 DCA 数据结构
  - 用途：表示稀疏 coupling / 矩阵对象，服务于 DCA 计算
  - 复用状态：ready_for_review；类型：code_entry
- `structuredca/dca_model/gauge.py`
  - 能力：参数规整 / gauge 处理
  - 用途：对 DCA 参数做 gauge 变换或归一化处理
  - 复用状态：ready_for_review；类型：code_entry

### training

- `structuredca/dca_model/dca_solvers/dca_solver.py`
  - 能力：DCA 参数拟合
  - 用途：从 MSA 估计 DCA 模型参数
  - 复用状态：ready_for_review；类型：code_entry
- `structuredca/dca_model/dca_solvers/plmdca/plmdca.cpp`
  - 能力：plmDCA 优化后端
  - 用途：后端数值优化/拟合实现
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅基于静态路径清单，未安装依赖、未运行代码或 notebook、未执行测试。
- 未见独立 training entrypoint 或 CI 证据，训练逻辑可能分散在 solver/后端代码中。
- 未见 tracked checkpoint/weight 文件，无法判断是否依赖外部下载模型。
- `test_data/` 与 `plmdca/` 的再分发许可边界未核实。

## 仍未知

- `plmdca/` 子树是否完整 vendored、是否含本地修改，以及其上游许可边界，静态清单无法确认。
- `test_data/` 示例文件是否允许二次分发/再利用，没有单独数据许可证据。
- 教程 notebook 是否对应论文正式结果或只是演示，静态路径不足以证明。
- 仓库是否依赖未追踪的外部模型或数据下载，静态清单无法排除。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
