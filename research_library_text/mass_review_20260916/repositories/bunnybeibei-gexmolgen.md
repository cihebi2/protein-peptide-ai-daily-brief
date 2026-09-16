# bunnybeibei/gexmolgen

- **仓库：** [https://github.com/bunnybeibei/gexmolgen](https://github.com/bunnybeibei/gexmolgen)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none（根目录无 LICENSE；hgraph/ 子目录携带上游 hierVAE 的 MIT）
- **语言：** Python
- **复用度：** medium —— 推理/demo 管线完整且有权重下载链接和 AKT2 示例数据，但训练代码明确未上传（README to-do 标注），且需自行拉取 scGPT 仓库与配置环境
- **能力：** inference、data_loader、visualization

## 仓库摘要

GexMolGen：基于基因表达谱（scGPT 编码）跨模态生成 hit-like 小分子的模型（hierVAE 分子图解码），提供 Gradio 交互式生成/筛选/检索 demo。发表于 Briefings in Bioinformatics 2024。

## 入口脚本

- server.py
- functions.py
- utils.py

## 数据加载

- data/data_loader.py
- data/model_loader.py
- hgraph/dataset.py

## 模型权重

- README 提供 Google Drive 权重链接（含预训练 scGPT whole-human 权重）：https://drive.google.com/file/d/1uc7f7qzUjX3e7fSvPxYAzado6jY5myec/view

## 评测基准

- server_test_ctl_AKT2.csv
- server_test_pert_AKT2.csv（AKT2 对照/扰动表达谱，可复现论文 Result 2.3 的 Screen 功能）
- AKT2_ref.csv（AKT2 参考抑制剂）

## 文档

- README.md
- Overview.pdf
- Supplementary_Tables/

## 课题关联

- C007条件生成

## 与论文/课题的组合方式

- 与
- 条
- 件
- 生
- 成
- 类
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
- 用
- 自
- 带
-  
- A
- K
- T
- 2
-  
- 表
- 达
- 谱
- 示
- 例
- 数
- 据
-  
- +
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
- 复
- 现
-  
- S
- c
- r
- e
- e
- n
-  
- 生
- 成
- -
- 相
- 似
- 度
- 排
- 序
- 流
- 程
- ；
- 其
- '
- 生
- 物
- 模
- 态
- →
- 分
- 子
- 模
- 态
- '
- 跨
- 模
- 态
- 条
- 件
- 生
- 成
- 架
- 构
- 可
- 作
- 为
- 条
- 件
- 活
- 性
- 分
- 子
- 生
- 成
- 的
- 对
- 照
- 范
- 式
- 。
