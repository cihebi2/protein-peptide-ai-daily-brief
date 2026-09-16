# blazerye/drugassist

- **仓库：** [https://github.com/blazerye/drugassist](https://github.com/blazerye/drugassist)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** high —— 完整 LoRA 微调+合并+Gradio 推理+评测脚本链，训练数据集(MolOpt-Instructions)与模型权重(DrugAssist-7B)均在 HuggingFace 公开，开箱可跑
- **能力：** training_pipeline、inference、benchmark

## 仓库摘要

DrugAssist 是基于 Llama2-7B-Chat LoRA 微调的分子优化大语言模型，通过交互式指令对分子进行条件优化（提升活性/降低毒性等属性）。配套 MolOpt-Instructions 指令数据集与 HF 权重。

## 入口脚本

- run_sft_lora.py
- run_sft_lora.sh
- gradio_service.py
- merge_model.py

## 数据加载

- utils/build_dataset.py

## 模型权重

- HuggingFace: blazerye/DrugAssist-7B 及 DrugAssist-7B-4bit.gguf（README 给出链接，仓库内无权重文件）

## 评测基准

- evaluate/main_eval.py
- evaluate/small_molecule_editing.py
- evaluate/testset.csv
- evaluate/mol_DB.csv
- evaluate/evaluate.md

## 文档

- README.md
- quantized_model_deploy.md
- evaluate/evaluate.md

## 课题关联

- C007

## 与论文/课题的组合方式

- 可将其指令微调范式迁移到 AMP/肽条件优化：用自建肽属性指令集替换 MolOpt-Instructions，复用 run_sft_lora 与 evaluate 脚本快速搭建 LLM 肽优化基线，与扩散/生成模型对比。
