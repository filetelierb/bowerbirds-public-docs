# Bowerbirds public documentation

This repository contains the standalone Mintlify source for the public Bowerbirds documentation. The documentation is derived from the current Bowerbirds app and cloud implementations; internal planning material lives elsewhere and is not part of this repository.

## Preview locally

Install the [Mintlify CLI](https://www.mintlify.com/docs/cli/install), then run:

```sh
mint dev
```

Validate the site before publishing:

```sh
mint validate
mint broken-links
mint a11y
```

The public site is configured by `docs.json`. `.mintignore` defensively excludes internal-vault and documentation-framework paths if they are ever introduced by mistake.

## Client plugins

This repository also distributes a cross-client Bowerbirds plugin from `plugins/bowerbirds`:

- Claude Code discovers it through `.claude-plugin/marketplace.json`.
- Codex discovers it through `.agents/plugins/marketplace.json`.
- Cursor discovers it through `.cursor-plugin/marketplace.json`.
- Antigravity uses the copyable MCP configurations in the public integration guide.

The plugin invokes the CLI bundled with `/Applications/Bowerbirds.app`. Set `BOWERBIRDS_CLI` before starting the client to use a development build instead.
