# DocPurify MCP Guide

## Server configuration

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

## Available tools

- `get_workspace_overview`
  Read workspace status, credits, active jobs, and recent jobs.

- `submit_document_for_processing(file_id, processing_options?)`
  Start processing an uploaded file. Requires a `file_id` from the DocPurify web app.

- `list_document_jobs(limit?, status_filter?)`
  List recent jobs.

- `get_document_job(document_job_id)`
  Read job status, progress, current stage, and whether `result_ready` is true.

- `get_document_result(document_job_id)`
  Fetch Markdown output, artifacts, download links, and result metadata.

- `cancel_document_job(document_job_id)`
  Cancel a running or queued job when allowed.

- `delete_document_job(document_job_id)`
  Delete a completed, failed, or cancelled job after it is no longer needed.

## Recommended usage pattern

1. Call `get_workspace_overview`
2. Confirm the user has a `file_id`
3. Call `submit_document_for_processing`
4. Poll with `get_document_job`
5. Read results with `get_document_result`
6. Optionally delete the finished job

## Important constraints

- Local file paths are not valid for `submit_document_for_processing`
- `file_id` must come from the DocPurify web app upload flow
- Only call `get_document_result` after `result_ready` becomes `true`
- Download links may expire, so surface TTL-related details when relevant

## Common errors

- `MCP_KEY_INVALID` / `MCP_KEY_REVOKED`
  Ask the user to create or rotate the API key on the DocPurify MCP page.

- `DOCUMENT_JOB_NOT_FOUND`
  Confirm the `document_job_id` or `file_id` belongs to the current workspace.

- `ACCESS_DENIED`
  The key cannot access the referenced resource.

- `DOCUMENT_JOB_NOT_CANCELLABLE`
  The job is already terminal or otherwise cannot be cancelled.

- `DOCUMENT_JOB_NOT_DELETABLE`
  Wait until the job reaches a terminal state before deletion.
