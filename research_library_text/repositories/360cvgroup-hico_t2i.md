# 360cvgroup/hico_t2i

- **仓库：** [https://github.com/360cvgroup/hico_t2i](https://github.com/360cvgroup/hico_t2i)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** medium —— 训练/推理/评测代码与内置 diffusers 修改版完整，HiCo-7k grounding 数据 json 内置，但底座 SD 权重与 HiCo checkpoint 需另行下载，无 LICENSE 文件
- **能力：** training_pipeline、inference、benchmark、visualization

## 仓库摘要

HiCo（NeurIPS 2024）是层次可控的 layout-to-image 扩散生成模型：将布局中的每个对象建模为独立分支控制器，分层注入 ControlNet 实现可控文生图。含训练/推理/Gradio 演示与 COCO 布局评测。

## 入口脚本

- train_hico.py
- gradio_hico.py
- infer-avg.py
- run.sh

## 数据加载

- dataset/coco.py
- dataset/grit.py
- dataset/augmentations.py

## 模型权重

- 无权重文件；底座模型 realisticVisionV51（SD1.5 系）与 HiCo 权重需按 README 用 git lfs 从 HuggingFace 下载

## 评测基准

- eval/infer_coco_HiCo.py
- eval/cal_ap_step1.py
- eval/cal_ap_step2.py
- eval/eval.sh
- benchmark/HiCo-7k-GroundingData-Open.json

## 文档

- README.md
- models/readme
- benchmark/readme

## 课题关联

- （无）

## 与论文/课题的组合方式

- 与肽/蛋白课题无直接关联；其'分层分支控制器注入条件'的可控生成思想可作为 C007 条件生成（多条件解耦控制）的方法学参考。
