# AlertForge Agent Plugin

The official public integration package for [AlertForge](https://alertforge.ai). It connects compatible AI agents to AlertForge's hosted MCP server for creating coordinated stream branding, animated overlay packs, AI stream alerts, and transparent video assets.

This repository contains only portable plugin metadata and workflow instructions. It does not contain AlertForge application source, customer data, credentials, executable hooks, or install scripts.

## Included components

- A portable [Agent Plugin](https://agent-plugins.org/) manifest
- A Streamable HTTP MCP connection to `https://alertforge.ai/api/mcp`
- A workflow skill that preserves user approval and credit-confirmation checkpoints
- Compatibility metadata for clients that read Claude-style plugin manifests

## Authentication and billing

The three product-information tools are public. Account tools use AlertForge's OAuth 2.1 authorization-code flow with PKCE and require an eligible AlertForge account. Creation uses the account's AlertForge credit balance; the tools quote costs before the corresponding create action.

No credentials are stored in this repository. OAuth-capable clients discover authentication from AlertForge's published metadata.

## Data and network access

The plugin connects only to `https://alertforge.ai`. Depending on the user's request, the hosted service may process:

- prompts and visual direction supplied by the user;
- user-selected reference-image URLs;
- the user's AlertForge projects, asset status, and credit balance; and
- generated images, videos, overlay packages, and signed download links.

The plugin does not read local files, environment variables, SSH keys, browser data, or unrelated repositories. It does not execute local commands or install dependencies.

See the [agent setup guide](https://alertforge.ai/docs/agents), [privacy policy](https://alertforge.ai/privacy), [terms](https://alertforge.ai/terms), and [support page](https://alertforge.ai/support).

## Validation

Validate the JSON files with any JSON Schema-aware editor. Claude Code users can also run:

```sh
claude plugin validate .
```

The hosted MCP server can be checked without authentication by initializing it and listing its tools. Paid creation should only be tested with an authorized AlertForge-owned QA account.

## License

The metadata and instructions in this repository are licensed under the MIT License. The AlertForge service, product source, branding, and generated assets are governed separately by AlertForge's terms.
