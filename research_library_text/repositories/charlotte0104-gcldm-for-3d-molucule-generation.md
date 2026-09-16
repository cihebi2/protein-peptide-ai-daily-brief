# charlotte0104/gcldm-for-3d-molucule-generation

- **仓库：** [https://github.com/charlotte0104/gcldm-for-3d-molucule-generation](https://github.com/charlotte0104/gcldm-for-3d-molucule-generation)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** medium —— 训练/评测代码与大量配置齐全、有预训练权重下载链接，但权重需自行下载且 README 较简略（条件生成需手改代码中的权重导入路径），无 LICENSE
- **能力：** training_pipeline、inference、benchmark、data_loader

## 仓库摘要

GCLDM：基于几何图条件隐空间扩散模型（PyTorch Lightning + PyG）的 3D 分子生成，支持 QM9 上的无条件生成与按性质（alpha/Cv/mu）条件生成，README 提供预训练权重（Google Drive）与复现命令。

## 入口脚本

- src/train_torch_latent.py
- src/mol_gen_eval_torch_latent.py
- src/mol_gen_eval_conditional_qm9_latent.py
- src/test_main.py
- scripts/generate_qm9_mol_gen_ddpm_grid_search_runs.py

## 数据加载

- edm_datamodule.py
- src/edm_datamodule.py

## 模型权重

- 预训练权重经 Google Drive 链接提供: https://drive.google.com/file/d/1QF-9UXZhEcGelECOwWw6U9tbHMyJbmyp/view（best_loss_mini_batch.pth 与性质分类器 exp_class_alpha），仓库内不含权重文件

## 评测基准

- configs/mol_gen_eval*.yaml
- configs/mol_gen_eval_conditional_qm9_latent.yaml
- tests/test_eval.py

## 文档

- README.md
- GCLDM_719.yaml（conda 环境）
- configs/

## 课题关联

- C007条件生成（QM9 性质条件 3D 分子生成的直接实现与评测）
- C008基准校准（QM9 分子生成评测指标复现）

## 与论文/课题的组合方式

- 与
- 条
- 件
- 生
- 成
- 课
- 题
- （
- C
- 0
- 0
- 7
- ）
- 组
- 合
- ：
- 下
- 载
- 其
-  
- G
- o
- o
- g
- l
- e
-  
- D
- r
- i
- v
- e
-  
- 权
- 重
- ，
- 按
-  
- R
- E
- A
- D
- M
- E
-  
- 参
- 数
- 跑
-  
- m
- o
- l
- _
- g
- e
- n
- _
- e
- v
- a
- l
- _
- c
- o
- n
- d
- i
- t
- i
- o
- n
- a
- l
- _
- q
- m
- 9
- _
- l
- a
- t
- e
- n
- t
- .
- p
- y
-  
- 复
- 现
-  
- a
- l
- p
- h
- a
- /
- C
- v
- /
- m
- u
-  
- 条
- 件
- 生
- 成
- ；
- 其
- 性
- 质
- 分
- 类
- 器
- 引
- 导
- 扩
- 散
- 的
- 方
- 案
- 可
- 作
- 为
- 多
- 端
- 点
- 条
- 件
- 生
- 成
- 的
- 对
- 照
- 基
- 线
- 。
