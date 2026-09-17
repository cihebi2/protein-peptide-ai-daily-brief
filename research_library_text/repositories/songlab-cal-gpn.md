# songlab-cal/gpn

- **仓库：** [https://github.com/songlab-cal/gpn](https://github.com/songlab-cal/gpn)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1073/pnas.2311219120
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— pip 可安装、HuggingFace AutoClass 原生集成、CLI 覆盖训练/VEP/嵌入、含维护的训练配方与 Colab demo、CI 测试与详尽文档，MIT 许可；其预训练-微调-零样本打分的工程范式可直接迁移。
- **能力：** data_loader、training_pipeline、inference、benchmark、protocol

## 仓库摘要

GPN（Genomic Pretrained Network）：基因组预训练语言模型官方实现，覆盖 GPN/GPN-MSA/PhyloGPN/GPN-Star 四个模型家族，提供训练配方、变异效应预测（VEP）、logits/embedding 推理 CLI 与 HuggingFace Transformers 集成（如 songlab/gpn-star-hg38-v100-200m）。

## 入口脚本

- src/gpn/cli.py
- src/gpn/training.py
- src/gpn/inference.py
- recipes/gpn_training/
- recipes/gpn_star_training/

## 数据加载

- src/gpn/data.py
- src/gpn/msa/
- src/gpn/star/
- src/gpn/ss/

## 模型权重

- HuggingFace Hub：songlab/gpn-star-hg38-v100-200m 等（AutoModelForMaskedLM 加载）；已发布对齐、分数与 benchmark 数据集见 readthedocs 模型页

## 评测基准

- tests/
- docs 中的 GPN-Star benchmark 数据集（readthedocs published assets）

## 文档

- README.md
- docs/（readthedocs）
- colabs/gpn_demo.ipynb
- colabs/gpn_star_demo.ipynb
- colabs/gpn_star_precomputed_scores.ipynb
- colabs/phylogpn_demo.ipynb
- CHANGELOG.md
- AGENTS.md

## 课题关联

- L2蛋白语言模型（同为生物序列语言模型，训练/推理工程范式高度可迁移）
- C011评估协议（VEP 变异效应预测的标准化评估协议）
- C008基准校准（自带 benchmark 数据集与评估资产）
- C013基线新颖性（zero-shot 似然打分基线的参照实现）

## 与论文/课题的组合方式

- 与 DOI 10.1073/pnas.2311219120（GPN 原始论文）组合：用 recipes/gpn_training 与 gpn ss train/vep CLI 复现基因组 LM 训练与变异效应预测；课题组合中其'预训练模型 + 零样本似然 + 标准化 VEP 评估'流水线可作为 L2 蛋白语言模型课题的协议模板，与 plmeae 的 ESM zero-shot 形成跨模态对照。
