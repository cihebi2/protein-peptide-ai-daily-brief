# weilab-biology/deepprosite

- **仓库：** [https://github.com/weilab-biology/deepprosite](https://github.com/weilab-biology/deepprosite)
- **固定 commit：** `b6f6a8aec5128324655e7b638aa0122297a95220`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 22

## 仓库摘要

静态快照显示这是一个 protein binding site prediction 仓库：包含 ProtTrans/GraphTrans/self_attention/DSSP 等模块、infer.py、5-fold ckpt 以及训练/测试 FASTA、PDB 数据；但未见可执行训练/评估配置，数据与第三方预训练模型的独立许可边界也未完全澄清。

## 可复用模块与资源

### checkpoints

- `DeepProSite-main/model/fold0.ckpt`
  - 能力：5-fold 模型权重家族
  - 用途：主模型权重之一；同家族还存在 fold1-4.ckpt，且 output/weights/ 与 output/prediction/ 也有对应副本
  - 复用状态：partial；类型：model_weight
- `DeepProSite-main/pretrained_model/Rostlab/prot_t5_xl_uniref50/readme.txt`
  - 能力：第三方预训练语言模型说明
  - 用途：标识外部 ProtT5 预训练资源与边界提示
  - 复用状态：partial；类型：unknown
- `DeepProSite-main/pretrained_model~c193bc198fa46870605fc174ea638803f5ff7b55`
  - 能力：未确认内容的预训练资源/指针
  - 用途：静态无法确认是实际权重、指针还是占位文件
  - 复用状态：unknown；类型：unknown

### datasets

- `DeepProSite-main/datasets/Train_335.fa`
  - 能力：训练序列集合
  - 用途：训练 FASTA 数据
  - 复用状态：partial；类型：unknown
- `DeepProSite-main/datasets/Test_60.fa`
  - 能力：测试序列集合
  - 用途：测试 FASTA 数据
  - 复用状态：partial；类型：unknown
- `DeepProSite-main/datasets/Test_315.fa`
  - 能力：测试序列集合
  - 用途：测试 FASTA 数据
  - 复用状态：partial；类型：unknown
- `DeepProSite-main/datasets/test_protein.fa`
  - 能力：推理序列集合
  - 用途：推理/测试蛋白序列输入
  - 复用状态：partial；类型：unknown
- `DeepProSite-main/datasets/PRO_test.csv`
  - 能力：测试标签或元数据表
  - 用途：测试集表格/标注元数据
  - 复用状态：partial；类型：unknown
- `DeepProSite-main/datasets/pdb/1v74A.pdb`
  - 能力：结构输入文件
  - 用途：蛋白结构输入示例
  - 复用状态：partial；类型：unknown
- `DeepProSite-main/datasets/pdb/2y9wA.pdb`
  - 能力：结构输入文件
  - 用途：蛋白结构输入示例
  - 复用状态：partial；类型：unknown

### evaluation

- `DeepProSite-main/output/prediction/test.log`
  - 能力：测试/运行日志
  - 用途：静态可见的测试/推理日志，未见独立指标脚本
  - 复用状态：unknown；类型：unknown

### inference

- `DeepProSite-main/output/prediction/submission.csv`
  - 能力：预测输出表
  - 用途：推理结果导出
  - 复用状态：partial；类型：unknown

### reusable_assets

- `DeepProSite-main/main.py`
  - 能力：程序主入口/流程编排
  - 用途：主程序入口，组织数据、特征与模型流程
  - 复用状态：ready_for_review；类型：code_entry
- `DeepProSite-main/GraphTrans.py`
  - 能力：图结构模型模块
  - 用途：图/结构关系相关建模组件
  - 复用状态：ready_for_review；类型：code_entry
- `DeepProSite-main/ProtTrans.py`
  - 能力：ProtTrans 表征处理
  - 用途：处理预训练蛋白语言模型表征
  - 复用状态：ready_for_review；类型：code_entry
- `DeepProSite-main/get_dssp.py`
  - 能力：结构特征提取
  - 用途：提取 DSSP 结构特征
  - 复用状态：ready_for_review；类型：code_entry
- `DeepProSite-main/process_ProtTrans.py`
  - 能力：ProtTrans 特征后处理
  - 用途：整理/转换 ProtTrans 特征缓存
  - 复用状态：ready_for_review；类型：code_entry
- `DeepProSite-main/edge_features.py`
  - 能力：边特征构造
  - 用途：构造图边或邻接相关特征
  - 复用状态：ready_for_review；类型：code_entry
- `DeepProSite-main/self_attention.py`
  - 能力：自注意力模块
  - 用途：提供注意力层实现
  - 复用状态：ready_for_review；类型：code_entry
- `DeepProSite-main/pad_feature.py`
  - 能力：特征 padding/对齐
  - 用途：对输入特征做长度或维度对齐
  - 复用状态：ready_for_review；类型：code_entry
- `DeepProSite-main/utils.py`
  - 能力：通用工具函数
  - 用途：通用辅助函数与共享逻辑
  - 复用状态：ready_for_review；类型：code_entry

### training

- `DeepProSite-main/noam_opt.py`
  - 能力：训练优化器辅助模块
  - 用途：训练阶段的优化器/调度封装
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未运行代码、未安装依赖。
- 未见独立的 config recipe 或明确 training entrypoint，训练复现性受限。
- checkpoint、预测输出与日志均未验证其生成过程。
- 数据集与第三方预训练资源的许可/来源边界未完全澄清。
- 仓库内存在 root 与 DeepProSite-main/ 下重复 helper 文件，可能是打包复制产物。

## 仍未知

- DeepProSite-main/pretrained_model~c193bc198fa46870605fc174ea638803f5ff7b55 的真实内容无法静态确认。
- Train_335/Test_60/Test_315/test_protein/PRO_test 数据的构建来源、切分规则与许可未见说明。
- `output/prediction/*.csv` 和 `*.log` 是否完全对应本次冻结提交，静态上无法验证。
- 是否存在未冻结的外部依赖、脚本参数或环境要求，当前证据不足。
- 训练是否真的使用了上述 ckpt 之外的额外权重或中间产物，无法确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
