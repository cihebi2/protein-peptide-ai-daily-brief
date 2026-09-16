# 56kd/mulitmodaldepressiondetection

- **仓库：** [https://github.com/56kd/mulitmodaldepressiondetection](https://github.com/56kd/mulitmodaldepressiondetection)
- **审计批次：** mass-review-20260916
- **分析边界：** 仅静态审计；未执行代码、未训练、未复现。
- **许可证：** none
- **语言：** Python
- **复用度：** medium —— 代码覆盖单模态到多模态融合全链路并附转录文本与已提取特征 zip、折划分与预测输出；但原始音频数据集需自行获取（受限），且仓库无 LICENSE、依赖 OpenSMILE 外部工具
- **能力：** training_pipeline、inference、data_loader、visualization

## 仓库摘要

多模态抑郁检测项目：音频（OpenSMILE 特征）+ 文本（BERT/TF-IDF）双通道，含 9 种音频模型（CNN/LSTM/Transformer 等）、5 种文本模型与决策级/特征级融合（Bayesian/GMU/Stacking 等），按 Interview/Reading 两任务做折交叉验证。

## 入口脚本

- extract_audio.py
- extractBERT.py
- extract_tfidf.py
- AudioModels/HybridCNNLSTM.py（等 9 个音频模型）
- TextModels/BERT.py（等 5 个文本模型）
- DecisionLevelFusion/（Bayesian.py/GMU.py/Stacking.py 等 7 种融合）
- FeatureLevelFusion/CNNLSTMBERT.py

## 数据加载

- extract_audio.py
- extract_tfidf.py
- extractBERT.py

## 模型权重

- 无独立权重文件；特征包已附：BERT-Interview.zip、BERT-Reading.zip、TF-IDF-*.zip；原始音频数据（受限数据集）需自备

## 评测基准

- metrics.py
- FoldLists/InterviewFolds.csv
- FoldLists/ReadingFolds.csv
- audio_it_predictions.txt / text_rt_predictions.txt 等 4 份预测输出
- UnitTests/

## 文档

- README.md（组件与数据说明）
- Figures/*.drawio（各模型架构图源）

## 课题关联

- （无）

## 与论文/课题的组合方式

- 与
- 生
- 物
- 医
- 药
- 课
- 题
- 族
- 无
- 直
- 接
- 关
- 联
- ；
- 其
- 决
- 策
- 级
- /
- 特
- 征
- 级
- 多
- 模
- 态
- 融
- 合
- 矩
- 阵
- （
- 1
- 1
-  
- 种
- 融
- 合
- 算
- 法
- ）
- 可
- 作
- 为
- 多
- 端
- 点
- /
- 多
- 模
- 态
- 信
- 息
- 融
- 合
- （
- C
- 0
- 0
- 3
- ）
- 的
- 工
- 程
- 参
- 照
- ，
- 但
- 属
- 间
- 接
- 方
- 法
- 借
- 鉴
- 。
