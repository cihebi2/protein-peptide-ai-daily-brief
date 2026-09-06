# atomgptlab/agapi

- **仓库：** [https://github.com/atomgptlab/agapi](https://github.com/atomgptlab/agapi)
- **固定 commit：** `b367c87d99cec479737592b05883495df920e19e`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 11

## 仓库摘要

仓库是 Apache-2.0 的 AGAPI 材料设计平台代码与文档集合；静态清单可见 agents 的 schema/client/functions/agent 模块、测试与 CI、以及少量示例/图示资源，但未发现训练入口、推理脚本、评估基准或 checkpoint。

## 可复用模块与资源

### datasets

- `agapi/images/Lab6data.dat`
  - 能力：示例材料数据 / 演示输入
  - 用途：看起来像材料数据样例，但仅能从文件名与路径确认存在，未核实来源或许可
  - 复用状态：unknown；类型：unknown
- `agapi/images/POSCAR`
  - 能力：示例结构文件 / 演示输入
  - 用途：看起来像 VASP POSCAR 样例输入，但未读取内容，无法确认是否为可复用数据集
  - 复用状态：unknown；类型：unknown

### evaluation

- `.github/workflows/tests.yml`
  - 能力：CI 测试入口
  - 用途：自动化测试工作流；只能证明存在测试流程，不证明已执行
  - 复用状态：partial；类型：config
- `agapi/tests/test_functions.py`
  - 能力：函数级单元测试
  - 用途：函数相关单元测试资产
  - 复用状态：partial；类型：code_entry
- `agapi/tests/test_agents.pyskip`
  - 能力：agent 测试占位
  - 用途：被标记为 skip 的 agent 测试，说明有测试意图但当前快照未启用
  - 复用状态：partial；类型：unknown
- `agapi/tests/test_functions_long.pyskip`
  - 能力：长测试占位
  - 用途：被标记为 skip 的长测试，占位性评估资产
  - 复用状态：partial；类型：unknown

### reusable_assets

- `agapi/agents/schema.py`
  - 能力：agents 数据结构 / schema 定义
  - 用途：定义 agent 与数据库相关的数据契约，适合作为接口复用起点
  - 复用状态：partial；类型：code_entry
- `agapi/agents/client.py`
  - 能力：agent client 封装
  - 用途：封装 agent/API 访问层，适合作为客户端接口复用起点
  - 复用状态：partial；类型：code_entry
- `agapi/agents/functions.py`
  - 能力：共享函数 / 工具函数
  - 用途：提供复用型 helper 与 tool 函数
  - 复用状态：partial；类型：code_entry
- `agapi/agents/agent.py`
  - 能力：agent 编排
  - 用途：承载 agent 编排逻辑，可能对应主流程封装
  - 复用状态：partial；类型：code_entry
- `setup.py`
  - 能力：packaging / dependency 声明
  - 用途：安装与依赖声明，可用于复用打包配置
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清单审查，未读取文件内容、未安装依赖、未运行代码或测试。
- 未发现训练入口、推理入口或 checkpoint，因此无法证明可复现训练/推理流程。
- agapi/images/Lab6data.dat 与 agapi/images/POSCAR 仅凭路径名判断为示例输入，真实性质与许可未确认。
- 部分测试文件以 .pyskip 结尾，说明测试覆盖可能不完整。

## 仍未知

- README 与 docs 的具体功能说明未逐页核对，API 边界与运行方式仍不完全明确。
- setup.py 仅表明存在依赖声明，未安装依赖，无法判断第三方包兼容性或潜在额外许可证要求。
- agapi/images/ 下的图片、数据样例与文档插图是否来自第三方素材，尚无证据。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
