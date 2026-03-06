# MCP 服务配置说明

> 本目录存放 AI IDE（Windsurf / Cursor 等）的 MCP Server 配置模板。
> 配置文件：[mcp-servers.json](./mcp-servers.json)

---

## Context7

| 项目 | 说明 |
|------|------|
| **用途** | 为 AI 提供**最新的第三方库官方文档**，解决 LLM 训练数据过时导致的 API 幻觉问题 |
| **包名** | `@upstash/context7-mcp` |
| **来源** | [GitHub](https://github.com/upstash/context7) · [官网](https://context7.com) |
| **API Key** | 可选。免费使用有速率限制，注册 [context7.com/dashboard](https://context7.com/dashboard) 可获取 Key 提升额度 |

**典型场景**：当你在 Prompt 中提到某个库（如 Next.js、Prisma），Context7 会自动拉取该库的最新文档注入上下文，确保 AI 生成的代码与当前版本一致。

---

## Exa

| 项目 | 说明 |
|------|------|
| **用途** | 为 AI 提供**实时 Web 搜索与网页抓取**能力 |
| **包名** | `exa-mcp-server` |
| **来源** | [GitHub](https://github.com/exa-labs/exa-mcp-server) · [官网](https://exa.ai) |
| **API Key** | **必需**。在 [exa.ai](https://exa.ai) 注册获取 |

**核心能力**：
- **Web 搜索**：基于语义的实时搜索，结果质量优于传统关键词搜索
- **网页抓取**：抓取指定 URL 的页面内容，支持实时爬取
- **可配置**：可自定义返回结果数量、启用/禁用特定搜索工具

**典型场景**：查找最新的技术方案、获取实时信息、抓取特定文档页面内容。

---

## Ace Tool

| 项目 | 说明 |
|------|------|
| **用途** | **代码库索引与语义搜索**，增强 AI 对项目代码的理解能力 |
| **包名** | `ace-tool`（全局安装） |
| **来源** | [GitHub](https://github.com/eastxiaodong/ace-tool) |
| **Token** | **必需**。通过 [ACE Relay](https://acemcp.heroman.wtf/) 获取 |

**核心能力**：
- **代码索引**：自动收集、索引项目文件，支持增量更新
- **语义搜索**：基于语义理解的代码检索，比关键词 grep 更智能
- **Prompt 增强**：根据当前上下文自动注入相关代码片段，提升 AI 回答准确度

**典型场景**：大型项目中快速定位相关代码、理解跨模块依赖关系、为 AI 补充项目上下文。

---

## 配置方式

1. 复制 `mcp-servers.json` 的内容
2. 将占位符替换为你的真实密钥：
   - `<your-exa-api-key>` → Exa API Key
   - `<your-ace-token>` → Ace Tool Token
3. 粘贴到你的 AI IDE 对应配置文件中：
   - **Windsurf**：`~/.codeium/windsurf/mcp_config.json`
   - **Cursor**：`~/.cursor/mcp.json`

> ⚠️ **安全提醒**：永远不要将包含真实 API Key 的配置文件提交到 Git 仓库。
