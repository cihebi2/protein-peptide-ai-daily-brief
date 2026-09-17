# jertubiana/pgm

- **仓库：** [https://github.com/jertubiana/pgm](https://github.com/jertubiana/pgm)
- **审计批次：** peptide-core 论文声明仓库
- **关联论文：** 10.1371/journal.pcbi.1010874
- **分析边界：** 仅静态审计
- **许可证：** BSD-3-Clause
- **复用度：** medium —— 代码结构清晰、文档与教程笔记本完备且自带数据，可直接改作序列生成基线；但无 pip 打包/setup、无自动化测试、纯 CPU（numba）、依赖路径需手动配置（Chimera/HMMer 可选），需以源码目录方式引入

## 仓库摘要

概率图模型（PGM）高阶面向对象 Python 库：实现受限玻尔兹曼机（RBM）、玻尔兹曼机（BM）、独立混合（MoI）、广义线性模型（GLM），基于 numpy/numba 纯 CPU 运行，面向蛋白质多重序列比对（MSA）与神经放电等离散生物数据；提供序列权重计算、序列 logo、隐单元可视化并映射到 PDB 结构、退火重要性采样（AIS）似然评估、MCMC 人工序列生成、条件采样与低温采样等配套工具，附带 WW/Kunitz/Hsp70 结构域、晶格蛋白（含真值适应度）与 MNIST 示例数据。

## 入口脚本

- source/pgm.py、source/rbm.py、source/bm.py、source/moi.py、source/glm.py（库 API，通过 RBM()/fit()/gen_data() 调用，无 CLI、无打包安装脚本）
- examples/*.ipynb（13 个 Jupyter 复现笔记本：Lattice Proteins、WW Domain、Kunitz Domain、Hsp70 Protein、MNIST、斑马鱼神经数据等，为实际使用入口）
- utilities/（Proteins_utils、Proteins_3D_utils、RBM_utils、evaluate_learning_utils 等辅助模块）

## 数据加载

- utilities/Proteins_utils.py：load_FASTA 加载 MSA、count_neighbours 计算序列权重
- utilities/dataset_utils.py、utilities/MNIST_utils.py（MNIST idx 格式加载）
- data/WW/WW_domain_MSA.fasta、data/Kunitz/Kunitz_domain_MSA.fasta + contact_map14_extended.mat、data/Hsp70/Hsp70_protein_MSA.fasta、data/Lattice_Proteins/（MSA + 真值 pnat 适应度）

## 模型权重

- 仓库不含预训练权重；模型由示例笔记本在附带数据上现场训练（如 WW 域 50 隐单元 Potts-dReLU RBM）

## 评测基准

- data/Lattice_Proteins/：晶格蛋白人工序列，含结构与适应度真值，用作生成模型质量基准（README 明示 benchmark against ground truth）
- AIS 估计配分函数后的序列似然评估（RBM.likelihood）
- MNIST 生成质量对比；无自动化测试套件（无 tests/）

## 文档

- README.md（含完整 API 使用示例与各笔记本摘要）
- examples/ 13 个教程笔记本
- figures/（论文图）

## 课题关联

- C007 条件生成：直接相关——RBM 条件采样与低温采样即约束/条件式序列生成手段
- L4 肽生成：直接相关——短结构域（WW N=31、Kunitz N=53）序列生成模型与评估流程可迁移到肽序列生成
- L5 肽优化：相关——低温/条件采样可作序列优化基线方法
- C013 基线新颖性：直接相关——RBM 是经典非自回归序列生成基线，适合作新颖性/性能对照
- C011 评估协议：相关——AIS 似然评估与生成序列 PWM 统计对比可作为评估协议组件
- C008 基准校准：部分相关——晶格蛋白真值适应度基准可校准生成质量评测
- C001/C002/C003/C004/C010：间接或弱相关（模型无活性/毒性/binder 端点头，需外接预测器）

## 与论文/课题的组合方式

- 对应论文 10.1371/journal.pcbi.1010874（PGM 方法学/应用论文）：建议在 C007/L4/L5 中把 RBM 条件/低温采样作为经典生成基线与自研模型同协议对比
- C013：以 RBM 生成序列的新颖性（与 MSA 距离/权重）与似然作基线新颖性参照
- C011/C008：复用其 AIS 似然评估与晶格蛋白真值基准校准评估管线
- C001/C002/C003：其生成端点为序列统计与结合特异性 motif，需外接 AMP 条件活性/毒性/多端点预测器才能组合
- C004：WW 结构域即结合域，Kunitz 为蛋白酶抑制剂——可作 binder/PPI 小结构域生成的研究对象，但无结构打分接口
