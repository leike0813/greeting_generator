# Greeting Generator Skill

`greeting-generator` 是一个专为 Open Agent Skills 生态设计的 Skill 包。它旨在赋予 Agent 根据用户提供的节日信息、个人画像及发送对象列表，批量生成个性化、得体且富有文采的节日祝福语的能力。

## ✨ 特性

*   **交互式信息采集**: 引导用户提供节日背景、个人风格偏好及祝福语规格。
*   **批量生成**: 支持为多位发送对象一次性生成差异化的祝福语。
*   **灵活输入**: 支持通过对话直接输入对象信息，也支持导入 Markdown/JSON/YAML/TXT 等格式的名单文件。
*   **稳健解析**: 内置 Python 脚本处理各种格式的输入数据，具有较强的容错性。
*   **结果导出**: 支持将生成的祝福语保存为 Markdown 文件。

## 📂 项目结构

```
greeting-generator/
├── greeting-generator/      # Skill 包核心目录
│   ├── SKILL.md             # 核心 Skill 定义与 Prompt Flow
│   ├── scripts/             # 辅助脚本
│   │   └── parse_recipients.py  # 发送对象解析脚本
│   └── schemas/             # 数据校验 Schema
│       └── recipient_schema.json
├── examples/                # 示例输入文件
│   ├── recipients.json
│   ├── recipients.md
│   └── recipients.yaml
└── README.md                # 项目说明文档
```

## 🚀 快速开始

### 前置要求

*   支持 Open Agent Skills 规范的 Agent 运行环境。
*   Python 3.x 环境（用于运行辅助脚本）。

### SKILL.md 使用

将 `greeting-generator/` 目录部署到 Agent 的 Skill 加载路径中。Agent 将依据 `SKILL.md` 中的定义开始工作。

### 辅助脚本测试

你可以单独运行辅助解析脚本来验证你的名单文件是否符合格式：

```bash
# 测试 JSON 输入
python3 greeting-generator/scripts/parse_recipients.py examples/recipients.json

# 测试 YAML 输入
python3 greeting-generator/scripts/parse_recipients.py examples/recipients.yaml

# 测试 Markdown 输入
python3 greeting-generator/scripts/parse_recipients.py examples/recipients.md
```

## 📝 输入格式指南

为了获得最佳体验，建议使用结构化的输入文件。支持以下字段：

| 字段名 (Key) | 必填 | 说明 |
| :--- | :--- | :--- |
| `title` / `称谓` | ✅ | 对发送对象的称呼，如“王叔叔” |
| `relation` / `关系` | ✅ | 与发送对象的关系，如“邻居” |
| `name` / `姓名` | ❌ | 对象真实姓名，若无则使用称谓 |
| `age` / `年龄` | ❌ | 辅助生成更得体的语气 |
| `gender` / `性别` | ❌ | 辅助称呼 |
| `notes` / `注意` | ❌ | 特别需要提到或避讳的点 |

### 示例 (Markdown Table)

```markdown
| 称谓 | 关系 | 注意事项 |
| --- | --- | --- |
| 张总 | 客户 | 强调合作愉快 |
| 奶奶 | 长辈 | 祝身体健康 |
```

## 📄 许可证

MIT License
