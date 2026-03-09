# ds-to-md-compiler

将《HyperOS 设计组件规范》等设计系统 PDF 规范，转化为结构化、高信噪比的 Markdown 文档，作为后续代码生成或 Agent 调用的**单点事实来源（SSOT）**。

**Design System PDF to Markdown compiler** — Turns spec PDFs (e.g. HyperOS design component specs) into structured, high-signal Markdown as the **single source of truth (SSOT)** for code generation or Agent use.

---

## 做什么 · What it does

- **输入 Input**：设计组件规范 PDF（如 HyperOS 设计规范） · Design component spec PDFs (e.g. HyperOS).
- **输出 Output**：无损、可检索的 Markdown 组件文档（设计令牌、Props、变体、状态、表格与图表语义化描述等） · Lossless, retrievable Markdown component docs (design tokens, props, variants, states, semantic tables/figures).
- **用途 Use**：供大模型 Chunking 检索、设计稿对照、或下游代码/文档生成 · For LLM chunking retrieval, design reference, or downstream code/docs generation.

## 仓库内容 · Repository layout

| 路径 Path | 说明 Description |
|-----------|------------------|
| `ds-compiler-prompt-v1.md` | 转换用系统指令（管线、视觉/表格规范、中断协议、输出 Schema） · System instruction for conversion (pipeline, visual/table rules, interrupt protocol, output schema). |
| `ds-compiler-prompt-v2.md` | 扩展版规则与输出约定 · Extended rules and output conventions. |
| `output/` | 编译产出的组件文档，如 `标题栏-Navigation-Bar.md` · Compiled component docs (e.g. `标题栏-Navigation-Bar.md`). |
| `AGENTS.md` | 仓库约定、命名与校验方式 · Repo conventions, naming, and validation. |

## 使用方式 · How to use

将上述 prompt 作为 Agent 的系统指令，向其提供 PDF 或页面内容，按管线执行：结构识别 → 资产解析 → 图表重构 → 校验 → Markdown 编译。产出保存到 `output/`，命名格式：`<组件名>-<EnglishName>.md`。

Use the prompts above as the Agent’s system instruction; feed PDF or page content and run the pipeline: structure recognition → asset parsing → chart/table reconstruction → validation → Markdown compile. Save output under `output/` with naming: `<ComponentName>-<EnglishName>.md`.

更多开发与提交流程见 [AGENTS.md](./AGENTS.md).  
For development and contribution flow, see [AGENTS.md](./AGENTS.md).
