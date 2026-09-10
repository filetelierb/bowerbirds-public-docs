# Bowerbirds client plugin

This package connects supported AI clients to the local MCP server bundled with Bowerbirds and adds workflow guidance for Buckets, captures, payloads, Scratchpads, Packages, and explicit human input.

## Requirements

- macOS 14 or later
- Bowerbirds at `/Applications/Bowerbirds.app`, or `BOWERBIRDS_CLI` set before the client starts
- a Bowerbirds cloud session created in the app or with `bowerbirds cloud login`

The package includes manifests for Claude Code, Codex, and Cursor. See the [public integration guides](https://github.com/filetelierb/bowerbirds-public-docs/tree/main/integrations) for installation and MCP-only alternatives.

The local MCP server cannot enumerate private Unsorted content or capture the screen without an explicit, visible user authorization flow.
