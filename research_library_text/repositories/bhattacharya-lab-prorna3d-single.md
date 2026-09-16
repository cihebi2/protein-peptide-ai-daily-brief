# bhattacharya-lab/prorna3d-single

- **仓库：** [https://github.com/bhattacharya-lab/prorna3d-single](https://github.com/bhattacharya-lab/prorna3d-single)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **语言：** Python
- **复用度：** medium —— 推理管线完整（含示例输入 inputs/、数据集划分列表、conda 环境文件），但模型权重需从 Zenodo 自行下载，折叠步骤还需安装 PyRosetta 并自备 ESM2/RNA-FM 嵌入
- **能力：** inference、data_loader、protocol

## 仓库摘要

ProRNA3D-single：基于几何注意力配对蛋白质/RNA生物语言模型(ESM2+RNA-FM)的单序列蛋白质-RNA复合物三维结构预测方法，发表于 Cell Systems 2025。输入两条单体 PDB 与预计算距离图，推理输出蛋白-RNA 相互作用并折叠成复合物结构。

## 入口脚本

- run_predictions.py
- ProRNA3D-single.py
- folding.py
- gen_rst.py
- preprocess_monomers.py

## 数据加载

- dataloader.py

## 模型权重

- ProRNA3D_model/（本地为空，需从 Zenodo 下载 model.pt: https://zenodo.org/records/11477127/files/model.pt）

## 评测基准

- Datasets/test.txt（PDB 曲划分测试集列表）

## 文档

- README.md
- workflow.png
- ProRNA3D-single_environment.yml

## 课题关联

- C004 binder/PPI（蛋白-RNA 复合物结构与界面距离预测，可作 binder 对接评估的结构基座）
- C16 docking（预测复合物折叠可视为几何对接下游）

## 与论文/课题的组合方式

- 结
- 合
- 其
-  
- C
- e
- l
- l
-  
- S
- y
- s
- t
- e
- m
- s
-  
- 2
- 0
- 2
- 5
-  
- 论
- 文
- 复
- 现
- 蛋
- 白
- -
- R
- N
- A
-  
- 复
- 合
- 物
- 预
- 测
- ：
- 下
- 载
-  
- Z
- e
- n
- o
- d
- o
-  
- 权
- 重
- 、
- 跑
-  
- r
- u
- n
- _
- p
- r
- e
- d
- i
- c
- t
- i
- o
- n
- s
- .
- p
- y
-  
- 于
- 内
- 置
-  
- 7
- Z
- L
- Q
- /
- 8
- H
- 0
- S
-  
- 示
- 例
- 即
- 可
- 验
- 证
- 管
- 线
- ；
- 其
- 蛋
- 白
- -
- R
- N
- A
-  
- 界
- 面
- 距
- 离
- 输
- 出
- 可
- 作
- 为
-  
- C
- 0
- 0
- 4
-  
- b
- i
- n
- d
- e
- r
-  
- 课
- 题
- 的
- 复
- 合
- 物
- 构
- 象
- 评
- 估
- 参
- 照
- 。
