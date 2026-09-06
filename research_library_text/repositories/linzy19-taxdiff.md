# linzy19/taxdiff

- **仓库：** [https://github.com/linzy19/taxdiff](https://github.com/linzy19/taxdiff)
- **固定 commit：** `860ddbffdd7ba4746b60d6672dad475b4f07c51e`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 12

## 仓库摘要

该仓库是 TaxDiff 的核心实现快照：`models.py` 与 `diffusion/*.py` 构成主要方法，`sample_protein.py` 提供生成式推理入口，`ckpt/0012802_eval.pt` 是唯一权重文件。冻结清单只见 `data_reader/Taxonnmic_classfication.xlsx` 和 `decoder_data/*.txt` 等数据样式文件，但未见独立训练脚本或评估脚本；代码层有 MIT LICENSE，数据与 checkpoint 的单独许可和来源仍不明确。

## 可复用模块与资源

### checkpoints

- `ckpt/0012802_eval.pt`
  - 能力：evaluation checkpoint / model weight
  - 用途：冻结快照中的唯一 `.pt` 权重文件，推测用于评估或采样；仅凭静态清单不能证明训练完成或指标来源。
  - 复用状态：partial；类型：model_weight

### datasets

- `data_reader/Taxonnmic_classfication.xlsx`
  - 能力：taxonomy classification table
  - 用途：表格型分类/标签数据，供 data_reader/decoder.py 读取；具体字段与来源在冻结证据中不可见。
  - 复用状态：partial；类型：unknown
- `decoder_data/model_10.txt`
  - 能力：辅助文本数据
  - 用途：文本型辅助数据或模型输出痕迹；仅能确认文件存在，无法静态判定其是训练语料、样本输出还是中间产物。
  - 复用状态：partial；类型：unknown
- `decoder_data/model_10_info.txt`
  - 能力：辅助元数据
  - 用途：与 `model_10.txt` 配套的说明/元数据文件。
  - 复用状态：partial；类型：unknown

### inference

- `sample_protein.py`
  - 能力：protein sequence generation entrypoint
  - 用途：从已保存权重执行推理/采样的入口脚本。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `models.py`
  - 能力：核心模型结构
  - 用途：定义 TaxDiff 的主模型结构，属于蛋白序列生成的核心方法代码。
  - 复用状态：ready_for_review；类型：code_entry
- `diffusion/gaussian_diffusion.py`
  - 能力：扩散过程实现
  - 用途：实现扩散前向/反向过程与采样相关的核心数学逻辑。
  - 复用状态：ready_for_review；类型：code_entry
- `diffusion/diffusion_utils.py`
  - 能力：扩散辅助工具
  - 用途：提供扩散计算与张量处理的辅助逻辑。
  - 复用状态：ready_for_review；类型：code_entry
- `diffusion/respace.py`
  - 能力：步数重采样与调度
  - 用途：支持 diffusion 采样步数重采样/调度的辅助模块。
  - 复用状态：ready_for_review；类型：code_entry
- `diffusion/timestep_sampler.py`
  - 能力：时间步采样
  - 用途：提供 diffusion 时间步采样或调度相关逻辑。
  - 复用状态：ready_for_review；类型：code_entry
- `requirements.txt`
  - 能力：运行依赖规格
  - 用途：声明 Python 依赖；冻结快照未安装依赖，不能据此证明可运行性。
  - 复用状态：ready_for_review；类型：unknown

### training

- `data_reader/decoder.py`
  - 能力：数据读取与训练支撑
  - 用途：提供数据读取与 decoder 侧批处理逻辑，属于训练/推理周边模块；冻结快照未见独立训练入口。
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清点，代码未执行、依赖未安装、测试未运行。
- 冻结清单未见独立训练入口或训练日志，无法证明训练流程可复现。
- 未见独立评估脚本或指标文件，评估结论无法从仓库静态证据确认。
- 数据表与 checkpoint 没有单独许可边界证据，复用时需额外核验来源。

## 仍未知

- `data_reader/Taxonnmic_classfication.xlsx` 的来源、字段语义与授权未明。
- `decoder_data/model_10.txt` 和 `decoder_data/model_10_info.txt` 可能是训练数据、样本输出或中间产物，但静态清单无法区分。
- `ckpt/0012802_eval.pt` 的训练来源、对应 epoch 与是否匹配论文报告模型都无法仅凭仓库清单确认。
- 冻结快照之外是否存在未收录的训练/评估代码未能核实。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
