# zhengkangjie/esm-aa

- **仓库：** [https://github.com/zhengkangjie/esm-aa](https://github.com/zhengkangjie/esm-aa)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** MIT
- **语言：** Python
- **复用度：** medium —— 权重可下载、推理/表示提取开箱可用，但以推理为主，缺训练与系统 benchmark 管线
- **能力：** inference、data_loader

## 仓库摘要

ESM-AA（ESM-All Atom）：基于 FAIR ESM 代码库扩展的全原子多尺度蛋白语言模型，统一蛋白序列-结构建模，支持表示提取、接触图预测与 ESMFold 折叠。

## 入口脚本

- hubconf.py
- examples/contact_esm_aa.py
- scripts/extract.py
- scripts/fold.py

## 数据加载

- esm/（内含 dataset/数据模块，沿用 facebookresearch/esm 结构）

## 模型权重

- README 提供 ESM-AA 35M + regression 权重 Google Drive 下载链接（scripts/download_weights.sh）

## 评测基准

- examples/contact_esm_aa.py（无监督接触预测示例）
- scripts/atlas/

## 文档

- README.md
- environment.yml
- CODE_OF_CONDUCT.rst

## 课题关联

- C004

## 与论文/课题的组合方式

- 全
- 原
- 子
- 级
- 蛋
- 白
- 表
- 示
- 可
- 作
- 为
-  
- b
- i
- n
- d
- e
- r
- /
- P
- P
- I
- （
- C
- 0
- 0
- 4
- ）
- 或
- 结
- 构
- 感
- 知
- 活
- 性
- 预
- 测
- 的
- 特
- 征
- 骨
- 干
- ，
- 与
-  
- E
- S
- M
- -
- 2
- /
- P
- S
- T
-  
- 表
- 示
- 做
- 对
- 照
- 实
- 验
- ；
- E
- S
- M
- F
- o
- l
- d
-  
- 接
- 口
- 可
- 为
- 无
- 结
- 构
- 蛋
- 白
- 补
- 充
- 结
- 构
- 预
- 测
- 。
