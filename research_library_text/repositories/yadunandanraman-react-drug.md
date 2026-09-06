# yadunandanraman/react-drug

- **仓库：** [https://github.com/yadunandanraman/react-drug](https://github.com/yadunandanraman/react-drug)
- **固定 commit：** `940b48039ba250d8e0cc3d8dedf607f69776f86e`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 11

## 仓库摘要

仓库是 MIT 许可的 ReACT-Drug 代码实现仓，静态清单仅见 Python 代码与依赖文件；未发现 bundled data、训练入口、评估结果或 checkpoint。

## 可复用模块与资源

### inference

- `scripts/generate_templates.py`
  - 能力：模板生成 / 推理辅助
  - 用途：生成 reaction templates 或候选模板的脚本
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `main.py`
  - 能力：仓库主入口
  - 用途：主流程入口脚本
  - 复用状态：ready_for_review；类型：code_entry
- `src/__init__.py`
  - 能力：包初始化
  - 用途：Python 包初始化文件
  - 复用状态：ready_for_review；类型：code_entry
- `src/agent.py`
  - 能力：RL 代理核心
  - 用途：代理/策略逻辑模块
  - 复用状态：ready_for_review；类型：code_entry
- `src/chemistry.py`
  - 能力：化学与反应工具
  - 用途：化学/反应辅助逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `src/config.py`
  - 能力：运行时配置
  - 用途：参数与配置定义
  - 复用状态：ready_for_review；类型：config
- `src/docking.py`
  - 能力：对接接口
  - 用途：分子对接相关逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `src/encoders.py`
  - 能力：分子编码
  - 用途：特征/表示编码模块
  - 复用状态：ready_for_review；类型：code_entry
- `src/environment.py`
  - 能力：环境/状态更新
  - 用途：环境动态或打分封装
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils.py`
  - 能力：共享工具函数
  - 用途：通用辅助函数
  - 复用状态：ready_for_review；类型：code_entry
- `requirements.txt`
  - 能力：Python 依赖清单
  - 用途：环境依赖声明
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态清单审查，未执行仓库代码。
- 未安装依赖，requirements.txt 的可用性与完整性未验证。
- 未运行测试或评估流程。
- 未见 bundled data、checkpoint 或训练入口，因此无法验证训练/推理闭环。

## 仍未知

- 各 Python 模块的内部算法细节仅能从文件名判断。
- scripts/generate_templates.py 的具体输出与调用方式未读取源码正文，仍不确定。
- 仓库是否依赖外部下载资源或运行时服务，静态清单无法确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
