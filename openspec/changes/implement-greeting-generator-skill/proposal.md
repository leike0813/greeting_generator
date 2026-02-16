## Why

当前仓库只有目标说明，尚未落地为可执行的 Open Agent Skills 包，无法稳定地按规范完成“采集信息 -> 生成候选祝福语 -> 可选写文件”的闭环。现在需要把需求固化为可验证的规格与任务，降低后续实现偏差。

## What Changes

- 在 `greeting-generator` 子目录中实现可执行的 Skill 包结构与主流程说明。
- 增加交互式输入编排能力，覆盖节日信息、用户画像、用途规格、发送对象信息采集。
- 增加发送对象批量输入能力，支持用户通过文件路径提供多对象信息并进行结构化解析。
- 增加候选祝福语生成与渲染能力，确保按对象分组、按数量生成且同组候选具备差异性。
- 增加结果持久化流程，询问用户是否写入文件，并提供默认时间戳文件名。

## Capabilities

### New Capabilities

- `interactive-greeting-session`: 规范化交互问答流程，确保必要输入被采集且可在信息不足时采用默认策略继续执行。
- `recipient-context-ingestion`: 解析单个或批量发送对象信息，支持文本与结构化文件输入，处理缺失字段回退。
- `greeting-render-and-export`: 为每位对象生成多条候选祝福语，按 Markdown 分组输出并支持可选写入文件。

### Modified Capabilities

- None.

## Impact

- 受影响目录：`greeting-generator/`（Skill 包主体）、`examples/`（示例输入可选补充）。
- 受影响接口：Agent 与用户的交互顺序、输入字段约束、输出 Markdown 结构。
- 依赖与工具：可复用现有环境中的 `pyyaml`、`jsonschema`、`pydantic`（如实现解析/校验辅助脚本）。
