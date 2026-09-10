# Bowerbirds client plugin

This package connects supported AI clients to the Bowerbirds remote MCP door and adds workflow guidance for records, captures, payload URLs and signatures. The client authorizes the connection in your browser: you pick the workspace and the role, and you can revoke it at any time from Bowerbirds' Settings → Developer Tools.

## Requirements

- a Bowerbirds account that owns or administers a workspace
- an MCP client that supports HTTP servers with OAuth (Claude Code, Codex, Cursor)

The package includes manifests for Claude Code, Codex, and Cursor. The published packages live in the `bowerbirds-plugins` repository; marketplace installation becomes available once it is public.

An agent never enumerates private Unsorted content, never captures the screen, and acts with its own token rather than as you.
