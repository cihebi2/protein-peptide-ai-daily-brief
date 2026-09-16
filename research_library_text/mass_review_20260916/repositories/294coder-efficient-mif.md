# 294coder/efficient-mif

- **仓库：** [https://github.com/294coder/efficient-mif](https://github.com/294coder/efficient-mif)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** medium —— 训练/推理框架与 27 个模型 config 齐全，但需自备图像融合数据集，无预训练权重且无 license
- **能力：** training_pipeline、inference、data_loader

## 仓库摘要

高效多源图像融合训练框架：覆盖 pansharpening、高光谱-多光谱融合、可见-红外/医学图像融合等任务，注册式模型架构 + PyTorch/accelerate 双训练引擎。

## 入口脚本

- accelerate_run_main.py
- torch_run_main.py
- accelerate_run_hyper_ms_engine.py
- accelerate_run_VIS_IR_engine.py
- torch_inference_on_sharpening.py

## 数据加载

- task_datasets/（任务数据集目录）

## 模型权重

- 无预训练权重（框架代码，模型经 register_model 注册后自行训练）

## 评测基准

- （无）

## 文档

- README.md
- readmes/
- Pansharpening_Hyper_SR_Matlab_Test_Package/

## 课题关联

- （无）

## 与论文/课题的组合方式

- 与课题族（多肽/蛋白/药物设计）无关联；仅当需要多模态图像融合基建时可考虑
