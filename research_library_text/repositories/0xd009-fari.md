# 0xd009/fari

- **仓库：** [https://github.com/0xd009/fari](https://github.com/0xd009/fari)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 预训练权重直接打包在仓库内（--name fari_default 即可评测），训练/评测脚本与数据准备说明完整
- **能力：** training_pipeline、inference、benchmark

## 仓库摘要

FARI（ICLR 2026）：扩散模型水印的鲁棒单步反演方法，将反演轨迹压缩为单步近似并微调轻量 LoRA 适配器，在图像失真下鲁棒恢复 Gaussian Shading / Tree-Ring 水印。

## 入口脚本

- train.py
- val_gs.py
- val_tr.py

## 数据加载

- src/utils.py（prompt 加载，支持 HF 数据集/JSON/CSV）；COCO 验证数据经 Tree-Ring 项目 Google Drive 下载

## 模型权重

- results/fari_default/fari_weights.pth（仓库内自带 10MB 预训练 LoRA 权重）；底模 Stable Diffusion 2.1 Base（HF 公开）

## 评测基准

- val_gs.py（Gaussian Shading 评测）
- val_tr.py（Tree-Ring 评测）

## 文档

- readme.md
- CITATION.cff

## 课题关联

- （无）

## 与论文/课题的组合方式

- 与生物课题族无直接关联；若开展生成模型可信性/鲁棒性子课题，其'单步反演+LoRA 微调'与失真鲁棒评测设计可作方法学参考
