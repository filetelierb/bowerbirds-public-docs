---
name: use-bowerbirds
description: Use Bowerbirds when a task needs context from filed Buckets — annotated captures, notes, recordings — or should file, move, trash or sign records in a Bowerbirds workspace through the bowerbirds MCP server.
---

# Use Bowerbirds

Bowerbirds is where people file annotated screenshots (captures), notes, dictations and screen recordings for their agents. You reach a workspace through the `bowerbirds` MCP server; the first call opens an approval page in the person's browser. You act as your own token, never as the person.

## Start safely

Call `list_directories` and `list_items` on the Bucket the person named (`slug`; a workspace token names the Bucket on every call). Read before writing: do not file, move or trash records unless the person asked for that change.

## Records

- A capture's `content` is a numbered list of comments about the picture; `get_capture` also answers `comments` parsed out. Its payloads are `annotated.png` (the picture with the pins), `raw.png` and `session.json`.
- Payload bytes never come through MCP. Every payload `url` is short-lived (15 minutes) and self-authenticating: fetch it with a plain HTTP GET and no header.
- `list_items` filters: `kind` (one or several), `path` (+ `exact`), `since`, `signed`; pages with `limit` and `cursor`.

## Signatures

Every record answers `signed` for your token. `list_items` with `signed: false` is your queue; call `sign_items` when a record is handled and only then. Other tokens' marks are invisible to you.

## Writing

`add_capture` files a record and answers one upload URL per declared payload (`{name, mimeType, size, role}`); PUT the bytes with exactly the listed `Content-Type` and `Content-Length` within 15 minutes. `move_items` and `trash_items` follow the app's rules; nothing deletes for good.

## Limits

You cannot read the Trash, read another workspace, mint credentials, or reach a Bucket that takes submissions through a publishable web key only. Report a refusal rather than retrying it. If every call fails authentication, ask the person to connect again; never ask for or print a token.
