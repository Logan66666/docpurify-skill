# DocPurify Skill

DocPurify Skill provides a reusable workflow for AI assistants to process documents with DocPurify MCP.

The core skill content lives in [`SKILL.md`](./SKILL.md). Installation differs slightly by client, so this repository keeps one shared skill plus client-specific installation instructions below.

## Codex

Copy this sentence to Codex:

```text
Please install the DocPurify skill from https://docpurify.com/skill/codex , then help me configure DOCPURIFY_MCP_KEY for the DocPurify MCP server.
```

Manual setup notes:

1. Open the installation entry: `https://docpurify.com/skill/codex`
2. Follow the README / repo instructions to add the skill to your Codex setup.
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
2. Follow the README / repo instructions to add the skill to your Claude setup.
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

Then tell your AI assistant to use DocPurify for document processing.

## Repository Layout

- [`SKILL.md`](./SKILL.md): shared core skill definition
- [`references/mcp-guide.md`](./references/mcp-guide.md): detailed MCP usage guide for AI clients

