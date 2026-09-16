# intelligent-molecular-systems/all-atom-protein-sequence-generation

- **仓库：** [https://github.com/intelligent-molecular-systems/all-atom-protein-sequence-generation](https://github.com/intelligent-molecular-systems/all-atom-protein-sequence-generation)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** medium —— 训练/验证/Docker/Makefile 管线完整且新颖性评估脚本（BLAST、OmegaFold pLDDT）齐备，但 UniRef 数据集需自行构建下载
- **能力：** data_loader、training_pipeline、inference、benchmark

## 仓库摘要

基于 D3PM 离散扩散与修改版 ByteNet 的全原子（SELFIES）蛋白质序列从头生成，比较全原子表示与氨基酸表示在生成质量/多样性/新颖性上的差异，为 EvoDiff 的二次开发（硕士论文）。

## 入口脚本

- train.py
- validate.py
- create_dataset.py
- my_pipeline.py
- Makefile
- DOCKERFILE

## 数据加载

- MyUniRefDataset.py
- create_dataset.py
- evodiff/collaters.py

## 模型权重

- 无预置权重；cleanup_checkpoints.sh 管理训练 checkpoint

## 评测基准

- analysis/calc_blast_sim.py
- analysis/calc_omegafold_plddt.py
- analysis/analyse_selfies.py
- validate.py
- TestStatefulSamplers.py

## 文档

- README.md
- environment.yml
- config/

## 课题关联

- C007
- C013

## 与论文/课题的组合方式

- C
- 0
- 0
- 7
-  
- 条
- 件
- 生
- 成
- 课
- 题
- 可
- 直
- 接
- 复
- 用
- 其
-  
- B
- L
- A
- S
- T
-  
- 新
- 颖
- 性
- 与
-  
- p
- L
- D
- D
- T
-  
- 结
- 构
- 可
- 靠
- 性
- 评
- 估
- 协
- 议
- （
- C
- 0
- 1
- 3
-  
- 基
- 线
- 新
- 颖
- 性
- 量
- 化
- ）
- ；
- S
- E
- L
- F
- I
- E
- S
-  
- 全
- 原
- 子
- 表
- 示
- 可
- 扩
- 展
- 至
- 含
- 非
- 天
- 然
- 氨
- 基
- 酸
- 的
-  
- A
- M
- P
-  
- 设
- 计
- 。
