# ds-to-md-compiler

将《HyperOS 设计组件规范》等设计系统 PDF 规范，转化为结构化、高信噪比的 Markdown 文档，作为后续代码生成或 Agent 调用的**单点事实来源（SSOT）**。

## 做什么

- **输入**：设计组件规范 PDF（如 HyperOS 设计规范）
- **输出**：无损、可检索的 Markdown 组件文档（设计令牌、Props、变体、状态、表格与图表语义化描述等）
- **用途**：供大模型 Chunking 检索、设计稿对照、或下游代码/文档生成

## 仓库内容

| 路径 | 说明 |
|------|------|
| `ds-compiler-prompt-v1.md` | 转换用系统指令（管线、视觉/表格规范、中断协议、输出 Schema） |
| `ds-compiler-prompt-v2.md` | 扩展版规则与输出约定 |
| `output/` | 编译产出的组件文档，如 `标题栏-Navigation-Bar.md` |
| `AGENTS.md` | 仓库约定、命名与校验方式 |

## 使用方式

将上述 prompt 作为 Agent 的系统指令，向其提供 PDF 或页面内容，按管线执行：结构识别 → 资产解析 → 图表重构 → 校验 → Markdown 编译。产出保存到 `output/`，命名格式：`<组件名>-<EnglishName>.md`。

更多开发与提交流程见 [AGENTS.md](./AGENTS.md)。

