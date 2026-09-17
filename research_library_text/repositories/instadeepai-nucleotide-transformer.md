# instadeepai/nucleotide-transformer

- **仓库：** [https://github.com/instadeepai/nucleotide-transformer](https://github.com/instadeepai/nucleotide-transformer)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1038/s41592-024-02523-z
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** CC BY-NC-SA 4.0（非商业）
- **语言：** Python (JAX/Flax)
- **复用度：** high —— 推理/微调代码完整、权重经HF一键下载、notebook+docs齐全、多规格模型可选；但为DNA基因组领域且CC BY-NC-SA非商业许可证，JAX栈与蛋白肽课题常用PyTorch栈不同。
- **能力：** inference、training_pipeline、data_loader、benchmark

## 仓库摘要

InstaDeep基因组学基础模型hub：Nucleotide Transformer（DNA语言模型，3200+人类基因组预训练，500M-2.5B多规格）及其衍生家族（AgroNT、SegmentNT、ChatNT、NTv3等），提供JAX推理/微调代码与HuggingFace权重。Nature Methods 2025论文官方仓库。

## 入口脚本

- nucleotide_transformer/pretrained.py（预训练模型加载入口，hf_hub_download拉取权重）
- nucleotide_transformer/model.py
- nucleotide_transformer_v3/pretrained.py（NTv3加载）
- notebooks/nucleotide_transformer/inference.ipynb
- notebooks/nucleotide_transformer_v3/inference_pretrained.ipynb
- notebooks/nucleotide_transformer_v3/inference_posttrained.ipynb

## 数据加载

- nucleotide_transformer/tokenizers.py（k-mer分词/单碱基分词）
- notebooks内自带示例序列数据

## 模型权重

- 权重不在仓库内，经HuggingFace Hub分发：https://huggingface.co/InstaDeepAI（NT 500M-human-ref/2B5-1000G/v2系列、AgroNT、SegmentNT、ChatNT、NTv3等）

## 评测基准

- notebooks/各模型子目录推理示例
- docs/*.md（各模型评测协议与任务说明：功能track预测、基因组注释等）

## 文档

- README.md
- docs/nucleotide_transformer.md
- docs/nucleotide_transformer_v3.md
- docs/segment_nt.md
- docs/chat_nt.md
- docs/agro_nucleotide_transformer.md
- docs/mojo.md
- docs/sct.md
- docs/isoformer.md
- docs/bulk_rna_bert.md
- docs/codon_nt.md

## 课题关联

- L2蛋白语言模型（基因组语言模型方法论镜像：预训练+下游探针/微调）
- C007条件生成（NTv3可控增强子序列生成+STARR-seq实验验证范式直接可借鉴）
- C003多端点（NTv3多功能track/注释多任务预测）
- C005表型（分子表型预测任务）
- C011评估协议（跨物种跨任务评测组织方式）

## 与论文/课题的组合方式

- 配论文10.1038/s41592-024-02523-z复现NT模型下游分子表型预测；NTv3的可控生成（masked diffusion后训练成生成模型+实验验证闭环）是C007条件生成课题的直接方法论模板；多任务头设计(heads.py)可参考用于C003多端点建模。注意非商业许可限制。
