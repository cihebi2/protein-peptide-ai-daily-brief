# zhenchengfang/metaprobiotics

- **仓库：** [https://github.com/zhenchengfang/metaprobiotics](https://github.com/zhenchengfang/metaprobiotics)
- **审计批次：** mass-review 论文声明仓库（repos2，浅克隆静态审计）
- **关联论文：** 10.1093/bib/bbae085
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** MATLAB (辅以 Shell 与捆绑的 jellyfish Linux 二进制)
- **复用度：** low —— 核心为MATLAB实现且Linux限定，无LICENSE文件（法律上复用受限），无pip/conda依赖管理；但预训练RF模型与k-mer词向量直接随仓库分发，dna2vec特征+RF的方法学本身易被Python复刻
- **能力：** 宏基因组bin级益生菌概率打分、dna2vec式k-mer语言模型特征提取、随机森林集成分类、jellyfish k-mer计数集成、虚拟机/Docker/MATLAB三通道分发

## 仓库摘要

metaProbiotics：基于语言模型从宏基因组分箱(bin)序列中挖掘益生菌的工具（Wu et al., Briefings in Bioinformatics 2024, bbae085 官方实现）。方法为 dna2vec 风格的 8-mer/100维 DNA 词向量特征(k8d100.txt, 54MB) + 随机森林集成(RF_all_3.mat, 43MB)，配 jellyfish 做 k-mer 计数。以一个或多个 fasta（每个 fasta 为同一 bin 的序列）为输入，输出益生菌概率分数，默认以 0.5 阈值判定。提供虚拟机、Docker、MATLAB 三种运行方式；核心代码为 MATLAB（metaProbiotics.m、dnaseq2vec.m、nt2num.m），MATLAB 路径仅限 Linux。

## 入口脚本

- metaProbiotics.m (MATLAB主入口)
- run_metaProbiotics.sh (MATLAB Runtime部署脚本)
- dnaseq2vec.m
- nt2num.m

## 数据加载

- example/example1.fasta
- example/example2.fasta
- example/example3.fasta
- example.fasta (bin级fasta输入格式示例)

## 模型权重

- RF_all_3.mat (43MB 训练好的随机森林集成模型)
- k8d100.txt (54MB 8-mer 100维dna2vec词向量权重)
- jellyfish-linux (3.7MB 捆绑k-mer计数二进制)

## 评测基准

- 无独立基准评测目录；输出为 Input_file|Score|Is_probiotics 三列，默认0.5阈值判定

## 文档

- README.md
- metaProbiotics_manual-20250221-revised.pdf (含虚拟机/Docker/MATLAB安装截图的详细手册)

## 课题关联

- C010
- C013
- L2

## 与论文/课题的组合方式

- C010校准弃权：其固定0.5阈值且无任何置信度校准/弃权机制的输出格式，是研究阈值校准与选择性预测价值的具体反例素材
- C013基线新颖性：dna2vec特征+随机森林代表'预训练词向量+传统ML'基线范式，可作为深度模型对比的强弱基线讨论案例
- L2蛋白语言模型：提供DNA k-mer级(而非氨基酸级)语言模型特征在分类任务上的实证参照
