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
