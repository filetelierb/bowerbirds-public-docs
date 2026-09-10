---
name: use-bowerbirds
description: Use Bowerbirds when a task needs context from filed Buckets, captures, payloads, Scratchpads, Packages, or an explicit human capture or input request on the user's Mac.
---

# Use Bowerbirds

Bowerbirds is a local-first context workspace. Use its MCP tools to retrieve or add durable context while preserving the user's requested scope.

## Start safely

For a new Bowerbirds workflow, call `get_server_info`, then `list_buckets`. Use `search_items` when the user describes content rather than naming a Bucket.

Read before writing. Do not create, move, update, or remove records unless the user asked for a change. `remove_item` moves a record to recoverable Trash, but it is still a mutation.

## Navigate context

- `list_buckets` and ordinary search intentionally exclude private Unsorted captures. If the needed capture is still Unsorted, ask the user to file it in the app.
- Call `list_item_files` before fetching a payload. Prefer `import_local_file` when another tool already produced a local file path.
- Use Scratchpads for mutable, revisioned working documents. Refresh before retrying an `update_scratchpad` revision conflict.
- Read and validate a Package before replacing it. Source records remain independent of Package documents.

## Human loop

The MCP server cannot silently capture the screen or microphone. When new evidence is necessary, use `request_capture_authorization` or `request_input`, explain why it is needed, then use `await_response`. Treat denial or expiry as a normal outcome and continue with the context already available when possible.

## Operational limits

General MCP payload ingress and egress is limited to 8 MB. `capture_read` returns at most three images. For larger or complete capture sets, use `capture_export` and work from the exported files.

If all tool calls fail authentication, ask the user to open Bowerbirds and sign in. Do not request, print, or expose Keychain credentials.
