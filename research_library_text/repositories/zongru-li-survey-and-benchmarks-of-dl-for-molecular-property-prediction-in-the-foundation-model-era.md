# Zongru-Li/Survey-and-Benchmarks-of-DL-for-Molecular-Property-Prediction-in-the-Foundation-Model-Era

- **仓库：** [https://github.com/Zongru-Li/Survey-and-Benchmarks-of-DL-for-Molecular-Property-Prediction-in-the-Foundation-Model-Era](https://github.com/Zongru-Li/Survey-and-Benchmarks-of-DL-for-Molecular-Property-Prediction-in-the-Foundation-Model-Era)
- **固定 commit：** `6384dd0e2c0be2c48686b7d2eea462848e2ee487`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 13

## 仓库摘要

该仓库主要提供分子性质预测的模型实现、配置、数据集与批处理脚本，适合做基准实验；静态清单未见可验证的训练入口、已发布权重或独立评测模块，且仅确认根目录 MIT 代码许可。

## 可复用模块与资源

### datasets

- `data/ADME.csv`
  - 能力：ADME benchmark data
  - 用途：HLM/HPPB/MDR1/RLM/RPPB/SOL 相关性质数据表
  - 复用状态：partial；类型：unknown
- `data/ADME_Time/ADME_HLM_train.csv`
  - 能力：ADME_Time 训练/测试划分
  - 用途：时间切分的 ADME 任务 train/test CSV
  - 复用状态：partial；类型：unknown
- `data/bace.csv`
  - 能力：通用分子性质分类基准
  - 用途：分类与多标签分子性质预测基准
  - 复用状态：partial；类型：unknown
- `assets/adme_time_splitting.xlsx`
  - 能力：ADME 时间切分说明
  - 用途：时间切分参考表/划分说明
  - 复用状态：unknown；类型：unknown

### evaluation

- `scripts/run_all_adme.sh`
  - 能力：批量实验脚本
  - 用途：批量运行 ADME 与时间切分基准实验
  - 复用状态：partial；类型：code_entry
- `src/utils/output.py`
  - 能力：结果输出
  - 用途：结果整理、保存与绘图支持
  - 复用状态：partial；类型：code_entry

### inference

- `scripts/generate_adme_datasets.py`
  - 能力：ADME 数据生成
  - 用途：生成或转换 ADME 数据集文件与切分产物
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `src/models/attentivefp.py`
  - 能力：模型实现
  - 用途：多种分子性质预测模型实现（GNN、预训练、n-gram/树模型等）
  - 复用状态：ready_for_review；类型：code_entry
- `configs/common.py`
  - 能力：配置模板
  - 用途：模型、数据集与超参数配置；覆盖多种基线和预训练设置
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils/data.py`
  - 能力：数据加载与图预处理
  - 用途：读取 CSV、构建图数据并生成训练/验证/测试划分
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils/checkpoint.py`
  - 能力：检查点辅助
  - 用途：模型状态保存/恢复的辅助逻辑；静态清单未显示实际权重文件
  - 复用状态：ready_for_review；类型：code_entry

### training

- `src/utils/training.py`
  - 能力：训练循环
  - 用途：损失优化、反向传播与训练过程封装
  - 复用状态：partial；类型：code_entry
- `src/run.py`
  - 能力：实验入口
  - 用途：读取配置并驱动训练/验证/记录流程
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未跑测试。
- 未发现可复用的序列化模型权重或 checkpoint 文件；`src/utils/checkpoint.py` 只是辅助代码。
- 数据集来源、二次分发权限与上游许可证未核实。
- 训练/评测效果、超参数与指标只能从文件名和路径推断，不能当作实证。

## 仍未知

- `README.md` 和脚本正文未逐文件解析，无法确认完整使用流程。
- `assets/adme_time_splitting.xlsx` 的生成逻辑、权属与对应数据来源未明。
- 是否存在未跟踪的大文件、外部下载资产或隐藏权重无法确认。
- 部分模型实现可能为作者原创或改写自第三方实现，但仅凭静态路径无法区分。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
