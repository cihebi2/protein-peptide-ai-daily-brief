# oxpig/ablang2

- **仓库：** [https://github.com/oxpig/ablang2](https://github.com/oxpig/ablang2)
- **固定 commit：** `586af3083c32b5fb2f0a1c855f2ad4f1cad15ec3`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** BSD-3-Clause
- **资产记录数：** 22

## 仓库摘要

该冻结仓库是 AbLang2 抗体语言模型包：主要包含 AbLang1/AbLang2 架构、tokenizer/vocab、预训练加载与恢复工具、以及示例 notebook；未见训练入口、评测管线或 bundled 数据/权重。

## 可复用模块与资源

### checkpoints

- `ablang2/models/ablang1/pretrained.py`
  - 能力：checkpoint
  - 用途：artifact_kind=checkpoint_adjacent；AbLang1 预训练模型注册/装配辅助，未见权重本体。
  - 复用状态：partial；类型：code_entry
- `ablang2/pretrained.py`
  - 能力：checkpoint
  - 用途：artifact_kind=checkpoint_adjacent；top-level pretrained 模块入口，偏向 checkpoint 访问而非权重文件。
  - 复用状态：partial；类型：code_entry
- `ablang2/pretrained_utils/__init__.py`
  - 能力：checkpoint
  - 用途：artifact_kind=checkpoint_adjacent；pretrained_utils 包导出，作为 checkpoint 辅助入口。
  - 复用状态：partial；类型：code_entry
- `ablang2/pretrained_utils/alignment.py`
  - 能力：checkpoint
  - 用途：artifact_kind=checkpoint_adjacent；对齐/映射辅助，服务于预训练权重恢复。
  - 复用状态：partial；类型：code_entry
- `ablang2/pretrained_utils/extra_utils.py`
  - 能力：checkpoint
  - 用途：artifact_kind=checkpoint_adjacent；附加辅助函数，服务于预训练模块。
  - 复用状态：partial；类型：code_entry
- `ablang2/pretrained_utils/restoration.py`
  - 能力：checkpoint
  - 用途：artifact_kind=checkpoint_adjacent；checkpoint 恢复/重建逻辑。
  - 复用状态：partial；类型：code_entry
- `notebooks/pretrained_module.ipynb`
  - 能力：checkpoint
  - 用途：artifact_kind=checkpoint_adjacent；预训练模块示例 notebook。
  - 复用状态：partial；类型：unknown
- `notebooks/pretrained_module_tcrlang.ipynb`
  - 能力：checkpoint
  - 用途：artifact_kind=checkpoint_adjacent；TCRLang 相关示例 notebook。
  - 复用状态：partial；类型：unknown

### inference

- `ablang2/load_model.py`
  - 能力：inference
  - 用途：artifact_kind=code_entry；构建/加载预训练模型对象，用于推理阶段接入。
  - 复用状态：partial；类型：code_entry
- `ablang2/pretrained_utils/encodings.py`
  - 能力：inference
  - 用途：artifact_kind=code_entry；序列编码与输入准备。
  - 复用状态：partial；类型：code_entry
- `ablang2/pretrained_utils/scores.py`
  - 能力：inference
  - 用途：artifact_kind=code_entry；输出分数/打分辅助。
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `ablang2/models/ablang1/model.py`
  - 能力：model_architecture
  - 用途：artifact_kind=code_entry；AbLang1 核心网络定义，承载抗体序列表示学习。
  - 复用状态：ready_for_review；类型：code_entry
- `ablang2/models/ablang1/embedding.py`
  - 能力：model_architecture
  - 用途：artifact_kind=code_entry；AbLang1 embedding 层。
  - 复用状态：ready_for_review；类型：code_entry
- `ablang2/models/ablang1/encoderblocks.py`
  - 能力：model_architecture
  - 用途：artifact_kind=code_entry；AbLang1 编码器堆叠。
  - 复用状态：ready_for_review；类型：code_entry
- `ablang2/models/ablang1/fairseq_mha.py`
  - 能力：model_architecture
  - 用途：artifact_kind=code_entry；多头注意力实现。
  - 复用状态：ready_for_review；类型：code_entry
- `ablang2/models/ablang1/extra_fns.py`
  - 能力：model_architecture
  - 用途：artifact_kind=code_entry；辅助张量/函数工具。
  - 复用状态：ready_for_review；类型：code_entry
- `ablang2/models/ablang2/ablang.py`
  - 能力：model_architecture
  - 用途：artifact_kind=code_entry；AbLang2 核心网络定义。
  - 复用状态：ready_for_review；类型：code_entry
- `ablang2/models/ablang2/encoderblock.py`
  - 能力：model_architecture
  - 用途：artifact_kind=code_entry；AbLang2 编码器块。
  - 复用状态：ready_for_review；类型：code_entry
- `ablang2/models/ablang2/tokenizers.py`
  - 能力：model_architecture
  - 用途：artifact_kind=tokenizer；AbLang2 分词逻辑。
  - 复用状态：ready_for_review；类型：tokenizer
- `ablang2/models/ablang1/tokenizers.py`
  - 能力：model_architecture
  - 用途：artifact_kind=tokenizer；AbLang1 分词逻辑。
  - 复用状态：ready_for_review；类型：tokenizer
- `ablang2/models/ablang2/vocab.py`
  - 能力：model_architecture
  - 用途：artifact_kind=tokenizer；AbLang2 词表与符号映射。
  - 复用状态：ready_for_review；类型：tokenizer
- `setup.py`
  - 能力：config_recipe
  - 用途：artifact_kind=config；包安装与依赖声明。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未运行代码或测试。
- 依赖未安装，子模块未初始化。
- 冻结清单未见实际权重文件或 bundled 数据；checkpoint 仅见辅助代码与示例 notebook。
- 无法从路径本身确认第三方代码是否被改写、内嵌或外部下载。

## 仍未知

- 外部预训练语料与下载位置未显式冻结。
- 真实模型权重是否位于未公开路径或远端下载源未知。
- `load_model.py`、`encodings.py`、`scores.py` 的实际推理调用链是否与论文主实验一致未知。
- notebook 是否依赖私有环境变量、额外数据或手工下载步骤未知。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
