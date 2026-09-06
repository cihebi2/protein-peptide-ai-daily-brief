# idrblab/annopro

- **仓库：** [https://github.com/idrblab/annopro](https://github.com/idrblab/annopro)
- **固定 commit：** `547770e508a89621e5a14f5aaee125dacfb3e7b5`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 11

## 仓库摘要

该仓库围绕 AnnoPRO 提供蛋白质功能注释的训练、推理、数据处理与示例产物；代码许可证为 MIT，但静态清单未见已追踪模型权重或可验证的复现实验记录。

## 可复用模块与资源

### datasets

- `example/bp_result.csv`
  - 能力：bundled example prediction outputs
  - 用途：BP/CC/MF 示例预测结果中的一部分，供演示输出格式
  - 复用状态：partial；类型：unknown
- `example/input-protein.dat`
  - 能力：bundled example inputs/outputs
  - 用途：示例推理输入与参数文件，配套 output-protein.dat 作为演示输出
  - 复用状态：partial；类型：unknown
- `example/protein.pkl`
  - 能力：bundled example artifact
  - 用途：示例序列或中间对象缓存；具体内容无法仅凭静态路径确认
  - 复用状态：unknown；类型：unknown

### evaluation

- `test_all.py`
  - 能力：smoke tests
  - 用途：安装、导入或基础功能检查；不代表公开基准评测
  - 复用状态：partial；类型：code_entry

### inference

- `annopro/prediction.py`
  - 能力：prediction pipeline
  - 用途：推理与批量预测入口
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `annopro/train_model.py`
  - 能力：training and model architecture
  - 用途：训练入口、模型结构与优化流程的核心实现
  - 复用状态：ready_for_review；类型：code_entry
- `annopro/prediction.py`
  - 能力：inference
  - 用途：预测入口与推理流程
  - 复用状态：ready_for_review；类型：code_entry
- `annopro/data_procession/data_predict.py`
  - 能力：data preprocessing
  - 用途：示例输入解析、特征/格式转换与推理前处理
  - 复用状态：ready_for_review；类型：code_entry
- `annopro/focal_loss/_binary_focal_loss.py`
  - 能力：loss function
  - 用途：focal loss 实现，用于类别不平衡训练
  - 复用状态：partial；类型：code_entry
- `annopro/__main__.py`
  - 能力：command-line entry
  - 用途：包级 CLI 入口
  - 复用状态：partial；类型：code_entry

### training

- `annopro/train_model.py`
  - 能力：training entrypoint
  - 用途：训练主流程、模型构建与权重导出入口
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅基于静态清单，未执行代码、未安装依赖、未运行测试。
- 未发现 tracked checkpoint/model weight；`example/protein.pkl` 的具体性质无法仅凭路径确认。
- `test_all.py` 与 CI 只能说明存在测试入口，不能证明评测结果或覆盖充分。
- 示例 CSV/Dat 文件更像 bundled demo 资产，不能直接等同于可再现训练数据集。

## 仍未知

- `example/protein.pkl` 是否为模型权重、缓存还是输入序列序列化对象，不明。
- `annopro/train_model.py` 中的具体网络结构、超参数与保存策略未读文件，无法进一步核实。
- 示例数据与输出文件的来源、生成方式及再分发权利未见独立说明。
- 是否存在未追踪的大文件或外部下载数据，静态清单无法排除。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
