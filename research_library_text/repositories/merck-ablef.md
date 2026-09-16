# merck/ablef

- **仓库：** [https://github.com/merck/ablef](https://github.com/merck/ablef)
- **固定 commit：** `97964e4e92f01840465f7c2137c5528d3751fcbc`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** mixed
- **资产记录数：** 0

## 仓库摘要

仓库主要包含 antibody property prediction 的配置、数据预处理、训练和验证代码；未见 bundled data、checkpoint 或独立推理入口，许可证边界也未被静态清单完全澄清。

## 可复用模块与资源

- 未发现可公开描述的结构化资产。
## 使用限制

- 仅做静态清单审计，未运行代码、未安装依赖。
- 未见 tracked bundled data 或 checkpoint。
- `src/DeepNetworks/ALEF.py`、`src/holdout.py` 等仅按路径和命名推断角色，未读内容验证。
- 路径存在不等于可复现或已执行。
- 仓库存在大 blob/promisor 风险与未初始化 submodule 风险。

## 仍未知

- `config/resprop.json` 与 `config/resprop_all.json` 的精确定义无法仅凭清单确认。
- `src/DeepNetworks/ALEF.py` 是否为唯一主模型实现尚未验证。
- `src/holdout.py` 是否同时承担评估指标计算尚未验证。
- 许可证文本是否覆盖全部 tracked code/data/model 仍不明确。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。

## 2026-09-16 复审补充（mass-review 批次）

- **复用度（复审）：** medium —— 预处理/聚类/训练/调参/holdout 代码链完整，但数据与权重均不在仓库；构象系综预处理依赖商业 MOE 或需自行搭建 ImmuneBuilder+OpenMM 开源管线
- **许可证（复审）：** GPL-3.0
- **能力（复审）：** data_loader、training_pipeline、inference、visualization

**课题关联：**

- C004

**与论文/课题的组合方式：**

- 用
- 于
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
- /
- 抗
- 体
- 课
- 题
- 的
- 可
- 开
- 发
- 性
- （
- 热
- 稳
- 定
- 性
- 、
- 聚
- 集
- 倾
- 向
- ）
- 预
- 测
- 环
- 节
- ：
- 先
- 设
- 计
- 后
- 过
- 滤
- ；
- 其
- 『
- 序
- 列
- 语
- 言
- 模
- 型
-  
- +
-  
- 结
- 构
- 系
- 综
- 融
- 合
- 』
- 思
- 路
- 可
- 迁
- 移
- 到
-  
- b
- i
- n
- d
- e
- r
-  
- 多
- 构
- 象
- 建
- 模
- ；
- 注
- 意
-  
- G
- P
- L
- -
- 3
- .
- 0
-  
- 传
- 染
- 性
- 对
- 组
- 合
- 分
- 发
- 的
- 限
- 制
- 。
