# yuzhewangpku/diffpepbuilder

- **仓库：** [https://github.com/yuzhewangpku/diffpepbuilder](https://github.com/yuzhewangpku/diffpepbuilder)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** high —— 训练/推理/后处理/docking 全流程代码完整且有 Colab demo，PepPC/PepPC-F 数据集 CSV 内置、原始数据与模型权重在 Zenodo 公开；需自行下载权重并安装 PyRosetta 做后处理
- **能力：** data_loader、training_pipeline、inference、benchmark、protocol、visualization

## 仓库摘要

DiffPepBuilder 是基于扩散模型的靶点特异性 de novo 肽 binder 设计工具（JCIM 2024），可指定靶点热点残基条件生成全原子肽配体；扩展版 DiffPepDock（Protein Science 2025）支持蛋白-肽对接与虚拟筛选，并发布 PepPC/PepPC-F 训练数据集。

## 入口脚本

- experiments/run_inference.py
- experiments/run_docking.py
- experiments/run_postprocess.py
- experiments/train.py
- examples/DiffPepBuilder_demo.ipynb
- examples/DiffPepDock_demo.ipynb

## 数据加载

- data/pdb_data_loader.py
- experiments/process_dataset.py
- experiments/process_receptor.py
- experiments/process_batch_dock.py
- experiments/split_dataset.py

## 模型权重

- Zenodo 公开权重（README 给出链接）：diffpepbuilder_v1.pth (zenodo.org/records/12794439)、DiffPepDock 权重 (zenodo.org/records/15398020)，需下载至 experiments/checkpoints/

## 评测基准

- datasets/docking/docking_benchmark.csv
- datasets/docking/PBD_data_subsampled.csv
- datasets/docking/PBD_screening_metrics.csv
- analysis/metrics.py
- config/eval.yaml

## 文档

- README.md
- datasets/README.md
- examples/（含 Colab demo 与示例受体数据）
- config/

## 课题关联

- C004
- C007
- C016

## 与论文/课题的组合方式

- C004 binder/PPI 课题的核心生成引擎：给定靶点热点生成肽 binder 并用其 docking 模块验证；DiffPepDock 可与 HADDOCK3 互为肽对接基线（C016）；PepPC 数据集可支撑条件生成（C007）的训练与评估。
