# alienn233/ROSes-Finder

- **仓库：** [https://github.com/alienn233/ROSes-Finder](https://github.com/alienn233/ROSes-Finder)
- **固定 commit：** `38d36dada68abd056a2b293a0e30e3c6738aa613`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 19

## 仓库摘要

仓库主要提供ROSes-FINDER的预测、评估与序列化模型资产；未见显式训练入口，代码为 MIT，但权重和样例数据的独立许可未明。

## 可复用模块与资源

### checkpoints

- `nn_nclass_model_ac01.pth`
  - 能力：多分类神经网络权重
  - 用途：多分类神经网络推理权重
  - 复用状态：partial；类型：model_weight
- `nn__2class.pkl`
  - 能力：二分类序列化模型
  - 用途：二分类模型的序列化对象，可能供推理或评估复用
  - 复用状态：partial；类型：unknown
- `xgboos_2class.pkl`
  - 能力：二分类 XGBoost 模型
  - 用途：二分类 XGBoost 序列化模型
  - 复用状态：partial；类型：unknown
- `xgboos_Nclass.pkl`
  - 能力：多分类 XGBoost 模型
  - 用途：多分类 XGBoost 序列化模型
  - 复用状态：partial；类型：unknown

### datasets

- `test.fa`
  - 能力：测试输入 FASTA
  - 用途：仓库内的示例/测试序列输入，不见完整训练语料
  - 复用状态：partial；类型：unknown

### evaluation

- `acc_recall.py`
  - 能力：准确率/召回率评估
  - 用途：计算分类评估指标，尤其是 accuracy 与 recall
  - 复用状态：ready_for_review；类型：code_entry
- `two_acc.py`
  - 能力：二分类评估
  - 用途：二分类任务的准确率/相关指标统计
  - 复用状态：ready_for_review；类型：code_entry
- `result.py`
  - 能力：结果汇总
  - 用途：汇总模型输出或生成结果表
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `classify.sh`
  - 能力：分类运行包装
  - 用途：以 shell 方式组织分类/预测流程
  - 复用状态：ready_for_review；类型：code_entry
- `nn_test.py`
  - 能力：单模型测试/推理
  - 用途：NN 模型的测试或预测执行脚本
  - 复用状态：ready_for_review；类型：code_entry
- `N_nn_test.py`
  - 能力：多分类 NN 测试/推理
  - 用途：多类别 NN 模型的测试或预测执行脚本
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `seq2pad.py`
  - 能力：序列预处理/定长填充
  - 用途：把输入序列转换为模型可用的定长表示
  - 复用状态：ready_for_review；类型：code_entry
- `scale.py`
  - 能力：特征缩放/标准化
  - 用途：对输入特征做缩放或归一化预处理
  - 复用状态：ready_for_review；类型：code_entry
- `conv.py`
  - 能力：卷积/特征转换模块
  - 用途：提供卷积相关的共享计算或特征变换逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `N_cnn.py`
  - 能力：CNN 分类器变体
  - 用途：实现不同规模的 CNN 分类器结构
  - 复用状态：ready_for_review；类型：code_entry
- `NNyyy_nn.py`
  - 能力：神经网络分类器变体
  - 用途：实现多种 NN 分类器/特征组合版本
  - 复用状态：ready_for_review；类型：code_entry
- `2classxgb.py`
  - 能力：XGBoost 分类器变体
  - 用途：实现二分类与多分类的 XGBoost 分类流程
  - 复用状态：ready_for_review；类型：code_entry
- `soft_vote.py`
  - 能力：软投票融合
  - 用途：将多个模型输出做 ensemble / soft voting
  - 复用状态：ready_for_review；类型：code_entry
- `extrac.pl`
  - 能力：序列提取工具
  - 用途：从输入中抽取或整理序列数据
  - 复用状态：ready_for_review；类型：unknown

## 使用限制

- 仅做静态审计，未运行仓库代码、测试或训练流程。
- 依赖未安装，无法验证 import、环境配置和实际推理输出。
- 仅能依据文件名和清单判断用途，无法确认模型/数据是否由本仓库生成。
- 无显式训练入口，训练复现性无法从当前冻结清单证明。

## 仍未知

- `test.fa` 是示例输入、验证集还是外部数据集，当前无法确认。
- .pth/.pkl 文件是否为作者自训权重、是否与论文结果一一对应，当前无法确认。
- 是否存在未跟踪的下载数据、预处理参数或隐藏依赖，当前无法确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
