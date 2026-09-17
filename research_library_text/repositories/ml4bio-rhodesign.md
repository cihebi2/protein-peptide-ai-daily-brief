# ml4bio/rhodesign

- **仓库：** [https://github.com/ml4bio/rhodesign](https://github.com/ml4bio/rhodesign)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1038/s43588-024-00720-6
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 推理/评测脚本+示例数据+五折划分ID齐全，checkpoint经Google Drive可取，MIT许可证无传染性；GVP+Transformer结构条件序列生成架构对蛋白/肽逆向折叠课题是直接可改造的模板。
- **能力：** inference、training_pipeline、benchmark、data_loader、visualization

## 仓库摘要

RhoDesign：RNA逆向折叠（结构到序列）设计模型，GVP几何编码器+Transformer编码-解码器，输入RNA三级结构(+二级结构图)生成序列，用RhoFold做结构预测回补增强训练。Nature Computational Science 2024论文官方代码。

## 入口脚本

- src/inference.py（PDB+接触图输入推理）
- src/inference_without2d.py（仅三级结构输入）
- src/eval_model.py（评测/复现主脚本）
- src/RhoDesign.py、src/RhoDesign_without2d.py（模型定义）

## 数据加载

- src/util.py、src/alphabet.py
- data/cross_fold_validation/（五折交叉验证划分：序列相似度<0.6与结构相似度<0.5两套）
- example/（示例PDB与接触图npy）

## 模型权重

- checkpoint/（空，仅readme）；权重经Google Drive分发（https://drive.google.com/drive/folders/1H3Itu6TTfaVErPH50Ly7rmQDxElH3JEz，含五折checkpoint .pth）

## 评测基准

- src/eval_model.py（recovery等指标评测）
- src/benchmark_and_demo_v1.ipynb、analysis_notebooks/benchmark_and_demo_v1.ipynb、analysis_notebooks/cluster.ipynb

## 文档

- README.md
- environment.yml
- model_arc.png（架构图）

## 课题关联

- L1蛋白设计（结构条件逆向折叠，与ProteinMPNN同范式的RNA版本）
- C007条件生成（结构到序列的条件生成+温度采样控制多样性）
- C011评估协议（序列/结构双维度相似度去泄漏五折划分，评测协议设计典范）
- C013基线新颖性（recovery率+采样多样性评测角度）
- L4肽生成（结构条件序列生成可迁移至肽骨架）

## 与论文/课题的组合方式

- 配论文10.1038/s43588-024-00720-6复现RNA逆向折叠与五折评测；其相似度感知的交叉验证划分协议(data/cross_fold_validation)可直接移植到C011/C013课题做去泄漏评估；GVP几何编码+自回归解码的inverse folding管线可作为L1/L4肽结构条件生成的基线模型。
