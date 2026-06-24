[English](./README.md) | [简体中文](./README.zh-CN.md)

# DocPurify Skill

DocPurify Skill 让 AI 助手通过 DocPurify MCP，把已上传的 PDF、Office 文档、文本文件和图片转换成更干净、更适合 AI 使用的 Markdown。

和泛化的 OCR 转 Markdown 工具相比，DocPurify 更强调面向 AI 与知识库流程的结果质量：结构感知抽取、可选的全文 AI 校准、更干净的正文归一化，以及图片相关内容的后处理。

## 为什么选 DocPurify

- 支持 PDF、DOCX、PPTX、TXT / Markdown 和图片文件
- 更稳地保留标题层级、阅读顺序和目录结构
- 支持可选的 AI 结构复核与全文内容复核
- 能清理 OCR 跑偏、空格换行噪声、无关图片描述等脏内容
- 更适合后续提示词、RAG 入库和内部知识处理流程

## 官方链接

- 官网：https://docpurify.com
- 申请 MCP API key：https://docpurify.com/mcp
- MCP 接入指南：https://docpurify.com/zh/docs/mcp-guide

## 快速安装

核心 skill 内容放在 [`SKILL.md`](./SKILL.md)。不同客户端的安装方式略有差异，所以本仓库保留一份共享 skill，并在下面分别提供安装说明。

## Codex

把下面这句话复制给 Codex：

```text
Please install the DocPurify skill from https://docpurify.com/skill/codex , then help me configure DOCPURIFY_MCP_KEY for the DocPurify MCP server.
```

手动安装说明：

1. 打开安装入口：`https://docpurify.com/skill/codex`
2. 按仓库说明把 skill 加到你的 Codex 环境里
3. 配置 DocPurify MCP server：

```json
{
  "mcpServers": {
    "docpurify": {
      "command": "npx",
      "args": ["-y", "@docpurify/mcp-server"],
      "env": {
        "DOCPURIFY_MCP_KEY": "your-api-key-here"
      }
    }
  }
}
```

## Claude

把下面这句话复制给 Claude：

```text
Please install the DocPurify skill from https://docpurify.com/skill/claude , then help me configure DOCPURIFY_MCP_KEY for the DocPurify MCP server.
```

手动安装说明：

1. 打开安装入口：`https://docpurify.com/skill/claude`
2. 按仓库说明把 skill 加到你的 Claude 环境里
3. 配置同一套 DocPurify MCP server 和 API key

## 通用 MCP

如果你的 AI 客户端支持 MCP，但不支持本地 skill，可以直接配置 MCP server：

```json
{
  "mcpServers": {
    "docpurify": {
      "command": "npx",
      "args": ["-y", "@docpurify/mcp-server"],
      "env": {
        "DOCPURIFY_MCP_KEY": "your-api-key-here"
      }
    }
  }
}
```

然后告诉 AI 助手使用 DocPurify 处理文档即可。

## 仓库结构

- [`SKILL.md`](./SKILL.md)：共享的核心 skill 定义
