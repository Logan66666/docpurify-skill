[English](./README.md) | [简体中文](./README.zh-CN.md)

# DocPurify Skill

DocPurify Skill helps AI assistants turn uploaded PDF, Office documents, text files, and images into cleaner, more structured Markdown through DocPurify MCP.

Unlike generic OCR-to-Markdown workflows, DocPurify focuses on document readiness for AI and knowledge workflows: structure-aware extraction, optional full-text AI calibration, cleaner content normalization, and image-aware post-processing.

## Why DocPurify

- Supports PDF, DOCX, PPTX, TXT / Markdown, and image files
- Preserves headings, reading order, and TOC structure more reliably
- Adds optional AI-based structure and full-text review passes
- Cleans noisy content such as OCR drift, spacing issues, and irrelevant image descriptions
- Works well for downstream prompting, RAG ingestion, and internal knowledge workflows

## Official Links

- Website: https://docpurify.com
- Get your MCP API key: https://docpurify.com/mcp
- MCP setup guide: https://docpurify.com/docs/mcp-guide

## Quick Install

The core skill content lives in [`SKILL.md`](./SKILL.md). Installation differs slightly by client, so this repository keeps one shared skill plus client-specific installation instructions below.

## Codex

Copy this sentence to Codex:

```text
Please install the DocPurify skill from https://docpurify.com/skill/codex , then help me configure DOCPURIFY_MCP_KEY for the DocPurify MCP server.
```

Manual setup notes:

1. Open the installation entry: `https://docpurify.com/skill/codex`
2. Follow the repository instructions to add the skill to your Codex setup.
3. Configure the DocPurify MCP server with:

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

Copy this sentence to Claude:

```text
Please install the DocPurify skill from https://docpurify.com/skill/claude , then help me configure DOCPURIFY_MCP_KEY for the DocPurify MCP server.
```

Manual setup notes:

1. Open the installation entry: `https://docpurify.com/skill/claude`
2. Follow the repository instructions to add the skill to your Claude setup.
3. Configure the same DocPurify MCP server and API key.

## Generic MCP

If your AI client supports MCP but not local skills, configure the MCP server directly:

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

Then ask your AI assistant to use DocPurify for document processing.

## Repository Layout

- [`SKILL.md`](./SKILL.md): shared core skill definition
