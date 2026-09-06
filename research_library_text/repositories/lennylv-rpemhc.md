# lennylv/RPEMHC

- **仓库：** [https://github.com/lennylv/RPEMHC](https://github.com/lennylv/RPEMHC)
- **固定 commit：** `bb10e5cb76a68094fc0dcb31289a7bdc1b8ad39f`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 41

## 仓库摘要

该仓库围绕 HLA-I/HLA-II 结合亲和力预测，静态清单显示包含模型代码、预处理/训练入口、5-fold checkpoints、多个 benchmark/independent test 数据与结果文件；但未检出 LICENSE，且仅凭静态路径无法证明训练、推断或复现已实际完成。

## 可复用模块与资源

### checkpoints

- `MHCI2020&MHCII2020/result/HLA_I/best_model_CV1.pt`
  - 能力：HLA-I 五折模型权重
  - 用途：第 1 折训练后序列化权重
  - 复用状态：blocked；类型：model_weight
- `MHCI2020&MHCII2020/result/HLA_I/best_model_CV2.pt`
  - 能力：HLA-I 五折模型权重
  - 用途：第 2 折训练后序列化权重
  - 复用状态：blocked；类型：model_weight
- `MHCI2020&MHCII2020/result/HLA_I/best_model_CV3.pt`
  - 能力：HLA-I 五折模型权重
  - 用途：第 3 折训练后序列化权重
  - 复用状态：blocked；类型：model_weight
- `MHCI2020&MHCII2020/result/HLA_I/best_model_CV4.pt`
  - 能力：HLA-I 五折模型权重
  - 用途：第 4 折训练后序列化权重
  - 复用状态：blocked；类型：model_weight
- `MHCI2020&MHCII2020/result/HLA_I/best_model_CV5.pt`
  - 能力：HLA-I 五折模型权重
  - 用途：第 5 折训练后序列化权重
  - 复用状态：blocked；类型：model_weight
- `MHCI2020&MHCII2020/result/HLA_II/best_model_CV1.pt`
  - 能力：HLA-II 五折模型权重
  - 用途：第 1 折训练后序列化权重
  - 复用状态：blocked；类型：model_weight
- `MHCI2020&MHCII2020/result/HLA_II/best_model_CV2.pt`
  - 能力：HLA-II 五折模型权重
  - 用途：第 2 折训练后序列化权重
  - 复用状态：blocked；类型：model_weight
- `MHCI2020&MHCII2020/result/HLA_II/best_model_CV3.pt`
  - 能力：HLA-II 五折模型权重
  - 用途：第 3 折训练后序列化权重
  - 复用状态：blocked；类型：model_weight
- `MHCI2020&MHCII2020/result/HLA_II/best_model_CV4.pt`
  - 能力：HLA-II 五折模型权重
  - 用途：第 4 折训练后序列化权重
  - 复用状态：blocked；类型：model_weight
- `MHCI2020&MHCII2020/result/HLA_II/best_model_CV5.pt`
  - 能力：HLA-II 五折模型权重
  - 用途：第 5 折训练后序列化权重
  - 复用状态：blocked；类型：model_weight

### datasets

- `dataset/data.csv`
  - 能力：核心训练/评估表
  - 用途：主数据表，承载样本与标签
  - 复用状态：blocked；类型：unknown
- `dataset/epitope_benchmark.csv`
  - 能力：benchmark 数据集
  - 用途：外部/基准评测样本集
  - 复用状态：blocked；类型：unknown
- `dataset/indep_test.csv`
  - 能力：独立测试集
  - 用途：独立留出测试评估
  - 复用状态：blocked；类型：unknown
- `MHCI2020&MHCII2020/dataset/HLA_II_data.csv`
  - 能力：HLA-II 数据表
  - 用途：HLA-II 任务输入数据
  - 复用状态：blocked；类型：unknown
- `NetMHCpan3.0/dataset/NetMHCpan_data.csv`
  - 能力：NetMHCpan 格式数据
  - 用途：按 NetMHCpan3.0 任务整理的数据集
  - 复用状态：blocked；类型：unknown
- `dataset/cv_id.txt`
  - 能力：交叉验证划分ID
  - 用途：全局 CV 切分索引/样本ID 列表
  - 复用状态：blocked；类型：unknown
- `MHCI2020&MHCII2020/dataset/HLA_I_cv_id.txt`
  - 能力：HLA-I 划分ID
  - 用途：HLA-I 五折或分组切分索引
  - 复用状态：blocked；类型：unknown
- `MHCI2020&MHCII2020/dataset/HLA_II_cv_id.txt`
  - 能力：HLA-II 划分ID
  - 用途：HLA-II 五折或分组切分索引
  - 复用状态：blocked；类型：unknown
- `dataset/pseudosequence.2016.all.X.dat`
  - 能力：MHC 伪序列资源
  - 用途：伪序列映射/编码参考
  - 复用状态：blocked；类型：unknown

### evaluation

- `ablation.py`
  - 能力：消融实验入口
  - 用途：对比/消融实验驱动
  - 复用状态：blocked；类型：code_entry
- `torch_base/ablation.py`
  - 能力：基础消融逻辑
  - 用途：通用消融分析实现
  - 复用状态：blocked；类型：code_entry
- `MHCI2020&MHCII2020/result/heatmap.py`
  - 能力：结果可视化
  - 用途：热图/性能分布可视化
  - 复用状态：blocked；类型：code_entry
- `result/5cv/readme.md`
  - 能力：5-fold 结果说明
  - 用途：交叉验证结果与说明文档
  - 复用状态：blocked；类型：unknown
- `result/ablation/readme.md`
  - 能力：ablation 结果说明
  - 用途：消融实验结果说明文档
  - 复用状态：blocked；类型：unknown
- `result/lomo/readme.md`
  - 能力：lomo 结果说明
  - 用途：留一/局部评测结果说明文档
  - 复用状态：blocked；类型：unknown
- `MHCI2020&MHCII2020/result/HLAI_group.csv`
  - 能力：HLA-I 分组评测表
  - 用途：HLA-I 分组性能汇总
  - 复用状态：blocked；类型：unknown
- `MHCI2020&MHCII2020/result/HLAII_group.csv`
  - 能力：HLA-II 分组评测表
  - 用途：HLA-II 分组性能汇总
  - 复用状态：blocked；类型：unknown

### inference

- `MHCI2020&MHCII2020/result/HLA_I_5cv_pred.csv`
  - 能力：HLA-I 五折预测输出
  - 用途：批量推断/预测结果缓存
  - 复用状态：blocked；类型：unknown
- `MHCI2020&MHCII2020/result/HLA_II_5cv_pred.csv`
  - 能力：HLA-II 五折预测输出
  - 用途：批量推断/预测结果缓存
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `model.py`
  - 能力：共享模型抽象与主网络定义
  - 用途：主模型封装与复用的核心实现入口
  - 复用状态：blocked；类型：code_entry
- `torch_base/model.py`
  - 能力：基础模块化模型组件
  - 用途：共享的底层网络组件与通用模型实现
  - 复用状态：blocked；类型：code_entry
- `MHCI2020&MHCII2020/hla_I_model.py`
  - 能力：HLA-I 专用模型结构
  - 用途：HLA-I 任务的专用网络定义
  - 复用状态：blocked；类型：code_entry
- `MHCI2020&MHCII2020/hla_II_model.py`
  - 能力：HLA-II 专用模型结构
  - 用途：HLA-II 任务的专用网络定义
  - 复用状态：blocked；类型：code_entry
- `preprocess.py`
  - 能力：共享预处理管线
  - 用途：通用特征清洗、编码或样本预处理
  - 复用状态：blocked；类型：code_entry
- `dataloader.py`
  - 能力：共享数据加载管线
  - 用途：通用训练/验证数据读取与批次构造
  - 复用状态：blocked；类型：code_entry
- `MHCI2020&MHCII2020/preprocess.py`
  - 能力：HLA-I/HLA-II 专用预处理
  - 用途：任务特定的数据预处理与特征构造
  - 复用状态：blocked；类型：code_entry
- `MHCI2020&MHCII2020/dataloader.py`
  - 能力：HLA-I/HLA-II 专用数据加载
  - 用途：任务特定的数据读取与 batch 组织
  - 复用状态：blocked；类型：code_entry
- `NetMHCpan3.0/dataset/process.py`
  - 能力：NetMHCpan 数据处理辅助脚本
  - 用途：将第三方格式数据整理为仓库内部可训练数据
  - 复用状态：blocked；类型：code_entry

### training

- `train.py`
  - 能力：顶层训练入口
  - 用途：驱动主训练流程与实验入口
  - 复用状态：blocked；类型：code_entry
- `torch_base/train.py`
  - 能力：基础训练框架
  - 用途：通用训练循环、优化与保存逻辑
  - 复用状态：blocked；类型：code_entry
- `MHCI2020&MHCII2020/train.py`
  - 能力：HLA-I/HLA-II 训练入口
  - 用途：任务特定训练、交叉验证和模型选择
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码
- dependencies_not_installed
- tests_not_run
- 未发现 LICENSE，无法确认直接复用边界
- path_presence_is_not_reproduction_evidence
- 部分大文件可能仅是快照中的结果/权重，不等于可重复训练产物

## 仍未知

- `NetMHCpan3.0` 子树是否为 vendored_third_party 资源或项目自制整理版，静态清单无法判定
- 多个 CSV/FASTA/.dat 数据文件的来源、授权与预处理链路未被证明
- `.pt` checkpoints 是否由当前仓库中的训练入口生成，无法仅凭路径确认
- 未发现独立 inference 脚本，推断流程只能从预测结果文件间接推测

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
