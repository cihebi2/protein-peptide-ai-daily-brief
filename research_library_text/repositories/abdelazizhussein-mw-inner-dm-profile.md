# abdelazizhussein/mw-inner-dm-profile

- **仓库：** [https://github.com/abdelazizhussein/mw-inner-dm-profile](https://github.com/abdelazizhussein/mw-inner-dm-profile)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python（脚本+Jupyter notebook）
- **复用度：** medium —— 论文图表复现包：npy 数据与绘图/计算脚本齐备、依赖轻量（pip install . 即可），但无训练管线/权重，属结果分析与可视化型仓库；与生物医药课题无关
- **能力：** visualization、data_loader

## 仓库摘要

银河系内区暗物质密度轮廓的天体物理分析仓库（Hussein et al. 2025, arXiv:2501.14868）：基于 Auriga/FIRE-2/TNG-50 流体动力学模拟，给出银河系暗物质密度轮廓的理论预测区间、绝热收缩计算（Appendix D）与 J/D 因子。

## 入口脚本

- AC_Calculation/adiabatic_contraction.py
- AC_Calculation/prep_input.ipynb
- DM_Densities/plot_densities.ipynb
- J_D_factors/plot.ipynb
- MW_Bracketed_Range/plot.ipynb
- q_vs_rho/Figure_6.ipynb

## 数据加载

- 各 notebook 直接加载同目录 .npy 数组（无通用 dataloader）

## 模型权重

- 无模型权重；附结果数据 .npy：DM_Densities/（Auriga/FIRE/TNG-50 halo 密度）、J_D_factors/（J/D 因子上下界）、MW_Bracketed_Range/（预测带）、q_vs_rho/

## 评测基准

- （无）

## 文档

- README.md（目录结构与安装说明）
- AC_Calculation/README.md
- setup.py（astropy/numpy/matplotlib/scipy）

## 课题关联

- （无）

## 与论文/课题的组合方式

- 与
- 课
- 题
- 族
- 无
- 关
- （
- 暗
- 物
- 质
- 天
- 体
- 物
- 理
- ）
- ；
- 仅
- 在
- '
- 论
- 文
- 图
- 表
- 级
- 复
- 现
- 包
- 组
- 织
- 方
- 式
- '
- （
- 数
- 据
- +
- n
- o
- t
- e
- b
- o
- o
- k
-  
- 一
- 一
- 对
- 应
- 论
- 文
- 图
- ）
- 上
- 可
- 作
- 为
- 复
- 现
- 资
- 产
- 打
- 包
- 的
- 参
- 考
- 范
- 式
- 。
