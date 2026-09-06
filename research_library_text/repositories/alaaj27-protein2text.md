# alaaj27/Protein2Text

- **仓库：** [https://github.com/alaaj27/Protein2Text](https://github.com/alaaj27/Protein2Text)
- **固定 commit：** `421e888bbcb138646c61047e42abd08f064f8620`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 8

## 仓库摘要

静态清单显示该仓库实现了 Protein2Text 的蛋白序列到自然语言文本生成管线：`esm_encoder.py`、`GCA.py`、`llava_llama.py`、`llava_arch.py` 与 `multimodal_projector`/`builder.py` 共同构成多模态推理架构，`evaluation/inference_model.py` 负责推理入口。冻结库存未见训练入口或 checkpoint，仅见 `data/sample_input.json` 示例输入与 `results/sample_input_results.jsonl` 样例输出；许可证只在代码层面明确为 MIT。

## 可复用模块与资源

### datasets

- `data/sample_input.json`
  - 能力：示例输入
  - 用途：演示用蛋白序列/输入样本，不足以代表训练语料
  - 复用状态：partial；类型：config

### evaluation

- `evaluation/conversation.py`
  - 能力：评测对话模板与常量
  - 用途：构造评测交互格式与提示模板
  - 复用状态：ready_for_review；类型：code_entry
- `results/sample_input_results.jsonl`
  - 能力：样例评测输出
  - 用途：示例生成结果，可用于人工对照但不是权重或训练数据
  - 复用状态：partial；类型：unknown

### inference

- `evaluation/inference_model.py`
  - 能力：文本生成推理
  - 用途：将蛋白输入转为自然语言输出
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `evaluation/model/multimodal_encoder/esm_encoder.py`
  - 能力：蛋白序列编码
  - 用途：把蛋白序列编码为下游多模态模型可消费的表示
  - 复用状态：ready_for_review；类型：code_entry
- `evaluation/model/gated_cross_attention/GCA.py`
  - 能力：多模态融合与门控交叉注意力
  - 用途：融合蛋白表示与语言模型上下文
  - 复用状态：ready_for_review；类型：code_entry
- `evaluation/model/language_model/llava_llama.py`
  - 能力：语言模型封装
  - 用途：提供 LLaVA/Llama 文本生成接口
  - 复用状态：ready_for_review；类型：code_entry
- `evaluation/model/builder.py`
  - 能力：模型组装
  - 用途：拼装 encoder、projector、fusion 模块与语言模型
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅基于冻结静态清单，未执行代码、未安装依赖、未运行测试。
- 未见 training_entrypoint / training_module，也未见 checkpoint，无法证明训练或复现。
- `results/sample_input_results.jsonl` 仅是样例输出痕迹，不能当作模型权重或数据集证据。
- 第三方依赖与潜在 vendored 代码的边界无法仅凭路径确定。
- path presence is not reproduction evidence.

## 仍未知

- `README.md` 仅有声明级证据，未读取正文，无法确认数据来源与运行方式。
- `evaluation/model/*` 是否包含上游 LLaVA 或 ESM 的 vendored/改写代码，静态路径无法证明。
- `data/sample_input.json` 的具体内容与许可未见。
- `results/sample_input_results.jsonl` 的生成流程与可重用性不明。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
