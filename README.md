# w3-store

Shopify theme based on **Brooklyn** (`9.0.1`), customized for the w3 storefront.

```
assets/     # CSS, JS, images, fonts
config/     # settings_schema.json, settings_data.json
layout/     # theme.liquid, password.liquid
locales/    # translations
sections/   # Online Store 2.0 / section files
snippets/   # reusable Liquid partials
templates/  # page templates (+ customers/)
```

## Prerequisites

- [Shopify CLI](https://shopify.dev/docs/api/shopify-cli) ≥ 3.x
- A Shopify partner / staff / collaborator account on the target store

```bash
# macOS
brew tap shopify/shopify && brew install shopify-cli
```

## Setup

```bash
cp shopify.theme.toml.example shopify.theme.toml
# edit store / theme IDs as needed
shopify auth login
```

## Local development

Hot-reload preview against a development theme:

```bash
shopify theme dev
# or with a named environment:
shopify theme dev --environment development
```

## Common commands

| Command | What it does |
| --- | --- |
| `shopify theme dev` | Local preview + file sync |
| `shopify theme push` | Upload theme files to a store theme |
| `shopify theme pull` | Download theme files from the store |
| `shopify theme check` | Run Theme Check (Liquid / JSON lint) |
| `shopify theme package` | Zip theme (respects `.shopifyignore`) |
| `shopify theme list` | List themes on the connected store |

Push to a non-live theme (safer default):

```bash
shopify theme push --unpublished
# or target an existing theme:
shopify theme push --theme <THEME_ID>
```

## Notes

- `.shopify/` and `shopify.theme.toml` are gitignored (CLI auth cache + local env config).
- `.shopifyignore` keeps docs/tooling out of `push` / `pull` / `package`.
- Prefer pulling `config/settings_data.json` carefully — it often contains merchant-specific settings you may not want to overwrite from git.

## Docs

- [Shopify CLI for themes](https://shopify.dev/docs/storefronts/themes/tools/cli)
- [Theme environments (`shopify.theme.toml`)](https://shopify.dev/docs/storefronts/themes/tools/cli/environments)
- [Theme architecture](https://shopify.dev/docs/storefronts/themes/architecture)
