# bunnybeibei/gexmolgen

- **仓库：** [https://github.com/bunnybeibei/gexmolgen](https://github.com/bunnybeibei/gexmolgen)
- **固定 commit：** `d03c40700c80fc4d327d390bc3b38211ec9b485b`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** mixed
- **资产记录数：** 23

## 仓库摘要

仓库实现了 GexMolGen 的分子生成主干：含 hgraph 模型、数据加载与 server demo，但未见训练入口、评估脚本或 checkpoints；根许可缺失且 hgraph/ 下有独立 LICENSE，复用边界受限。

## 可复用模块与资源

### datasets

- `AKT2_ref.csv`
  - 能力：reference dataset
  - 用途：artifact_kind=unknown；AKT2 参考数据/对照表
  - 复用状态：unknown；类型：unknown
- `Supplementary_Tables/Supplementary Table 1.csv`
  - 能力：supplementary table
  - 用途：artifact_kind=unknown；论文补充表/结果表
  - 复用状态：unknown；类型：unknown
- `Supplementary_Tables/Supplementary Table 2.csv`
  - 能力：supplementary table
  - 用途：artifact_kind=unknown；论文补充表/结果表
  - 复用状态：unknown；类型：unknown
- `Supplementary_Tables/Supplementary Table 3.csv`
  - 能力：supplementary table
  - 用途：artifact_kind=unknown；论文补充表/结果表
  - 复用状态：unknown；类型：unknown
- `Supplementary_Tables/Supplementary Table 4.csv`
  - 能力：supplementary table
  - 用途：artifact_kind=unknown；论文补充表/结果表
  - 复用状态：unknown；类型：unknown
- `Supplementary_Tables/Supplementary Table 5.csv`
  - 能力：supplementary table
  - 用途：artifact_kind=unknown；论文补充表/结果表
  - 复用状态：unknown；类型：unknown
- `Supplementary_Tables/Supplementary Table 6.csv`
  - 能力：supplementary table
  - 用途：artifact_kind=unknown；论文补充表/结果表
  - 复用状态：unknown；类型：unknown
- `Supplementary_Tables/Supplementary Table 7.csv`
  - 能力：supplementary table
  - 用途：artifact_kind=unknown；论文补充表/结果表
  - 复用状态：unknown；类型：unknown
- `Supplementary_Tables/Supplementary Table 8.csv`
  - 能力：supplementary table
  - 用途：artifact_kind=unknown；论文补充表/结果表
  - 复用状态：unknown；类型：unknown
- `Supplementary_Tables/Supplementary Table 9.csv`
  - 能力：supplementary table
  - 用途：artifact_kind=unknown；论文补充表/结果表
  - 复用状态：unknown；类型：unknown

### evaluation

- `server_test_ctl_AKT2.csv`
  - 能力：test fixture
  - 用途：artifact_kind=unknown；AKT2 control 测试输入
  - 复用状态：unknown；类型：unknown
- `server_test_pert_AKT2.csv`
  - 能力：test fixture
  - 用途：artifact_kind=unknown；AKT2 perturbed 测试输入
  - 复用状态：unknown；类型：unknown

### inference

- `data/model_loader.py`
  - 能力：model bootstrap
  - 用途：artifact_kind=code_entry；推理时模型实例化与权重装载
  - 复用状态：blocked；类型：code_entry
- `server.py`
  - 能力：service entrypoint
  - 用途：artifact_kind=code_entry；demo/服务推理入口
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `hgraph/encoder.py`
  - 能力：model architecture
  - 用途：artifact_kind=unknown；gene-expression 条件生成的编码器模块
  - 复用状态：blocked；类型：code_entry
- `hgraph/decoder.py`
  - 能力：model architecture
  - 用途：artifact_kind=unknown；分子生成/解码模块
  - 复用状态：blocked；类型：code_entry
- `hgraph/hgnn.py`
  - 能力：graph neural network
  - 用途：artifact_kind=unknown；图神经网络子模块
  - 复用状态：blocked；类型：code_entry
- `hgraph/vocab.py`
  - 能力：tokenizer
  - 用途：artifact_kind=tokenizer；词表与 token 映射
  - 复用状态：blocked；类型：tokenizer
- `data/model_loader.py`
  - 能力：model loading
  - 用途：artifact_kind=code_entry；模型实例化与权重装载辅助
  - 复用状态：blocked；类型：code_entry
- `data/data_loader.py`
  - 能力：data loading
  - 用途：artifact_kind=code_entry；读取并整理 gene expression / molecule 输入
  - 复用状态：blocked；类型：code_entry
- `server.py`
  - 能力：inference demo
  - 用途：artifact_kind=code_entry；AKT2 demo / 服务入口
  - 复用状态：blocked；类型：code_entry

### training

- `hgraph/dataset.py`
  - 能力：training support
  - 用途：artifact_kind=unknown；训练/采样用数据集封装
  - 复用状态：blocked；类型：code_entry
- `data/data_loader.py`
  - 能力：training support
  - 用途：artifact_kind=code_entry；训练批处理与输入整理
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- 未见独立 training entrypoint、evaluation 脚本或本地 checkpoints，无法证明可复现。
- 根许可缺失，直接复用仓库代码受限；子目录许可边界需单独审查。

## 仍未知

- hgraph/ 子树是否为 vendored_third_party 仍需源码历史或上游比对确认。
- CSV 文件更像 reference / supplementary / test fixture，但静态命名不足以判定其是否为原始训练数据。
- server.py 的实际运行路径及外部权重来源未在冻结清单中明确。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
