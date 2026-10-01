# neonloops plugins

Turn recurring work into an agentic workflow in your neonloops workspace.
**neonloops Workflows** provides one guided setup skill and
[67 outcome recipes](plugins/neonloops-workflows/skills/create-workflow/references/catalog.md)
across nine business domains. Choose the result you need; the skill helps establish
its inputs, connections, trigger and review steps, then builds through the neonloops
connector.

## Install

### Claude / Cowork

Open **Customize → Plugins → Add → Add marketplace**, enter
`https://github.com/neonloops/plugins`, sync, then install **neonloops Workflows**.
Open its **Connectors** tab and connect your own neonloops workspace.

### Codex

With the current Codex CLI installed, run:

```sh
codex plugin marketplace add neonloops/plugins
codex plugin add neonloops-workflows@neonloops-public
```

Open a new Codex chat, select `$create-workflow`, and finish neonloops account
linking when prompted.

### Claude Code

```sh
claude plugin marketplace add neonloops/plugins
claude plugin install neonloops-workflows@neonloops-public
```

Start a new session and use `/neonloops-workflows:create-workflow`.

[Full setup, updates and removal](plugins/neonloops-workflows/README.md#install-in-claude-or-codex)
· [Download plugin ZIP](https://github.com/neonloops/plugins/releases/latest/download/neonloops-workflows.zip)
· [Release history](https://github.com/neonloops/plugins/releases)

The ZIP is an alternative personal upload for Claude. Use the release asset named
`neonloops-workflows.zip`, not GitHub's repository source ZIP. The marketplace ID is
`neonloops-public` and the package author is **neonloops**.

## Try a recurring job

> Every Monday, prepare a sales pipeline exception digest from our open-deals
> table. Save a private report. Set up a draft first.

A neonloops account and workspace are required. The host links to neonloops through
OAuth; business apps used by a workflow are connected separately in neonloops.
Plugin installation does not grant workspace permissions. No local build, Python
script or SDK is required.

These are researched, authored recipes, not 67 live-tested installations. Each
setup checks the connected workspace's available tools and events, asks for missing
inputs, and distinguishes a saved draft from a validated, tested or active workflow.
See the [package details](plugins/neonloops-workflows/README.md#know-what-has-been-proved).

## Distribution

This repository provides direct installation from our public marketplace. Inclusion
in Claude's or OpenAI's official directory is a separate review process; adding
this repository does not mean the plugin has an approved directory listing.
ChatGPT installation is deferred until its connector approval.

Source and recipe contents are licensed under [MIT](LICENSE). Workspace service
use is governed by the [neonloops terms](https://neonloops.com/terms) and
[privacy policy](https://neonloops.com/privacy).

[Setup help](https://neonloops.com/mcp) · [Contact neonloops](mailto:hi@neonloops.com)
