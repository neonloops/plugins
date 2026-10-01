# neonloops Workflows

Your recurring work already has a shape: something happens, someone works through
the details, and a result needs to land in the right place. This package helps you
turn that job into an agentic workflow in neonloops, with its sources, output and
human decisions made explicit.

Choose from [67 researched outcome recipes](skills/create-workflow/references/catalog.md)
across sales, marketing, customer service, finance and procurement, people operations,
team operations, documents and contracts, product and IT, and commerce. One
`create-workflow` skill selects the relevant recipe and creates the workflow through
the neonloops MCP. It can also adapt a recipe or build a custom outcome using the
same installation protocol. Connector candidates are verified in your workspace
before use; a listed app is not a promise that every event or action is supported.

## Install in Claude or Codex

Version `0.1.2` is distributed from the public
[neonloops plugin repository](https://github.com/neonloops/plugins). The marketplace
ID is `neonloops-public`; the plugin is `neonloops-workflows`. A neonloops account
and workspace are required. Your host account or organization must allow plugins
and remote connectors.

Direct installation from this repository is separate from approval or discovery in
Claude's or OpenAI's official directories. ChatGPT installation will be documented
after its connector approval; these instructions cover Claude and Codex.

### Claude / Cowork

1. Open **Customize → Plugins → Add → Add marketplace**.
2. Enter `https://github.com/neonloops/plugins`, then sync the marketplace.
3. Open **neonloops Workflows** and install it.
4. Open the plugin's **Connectors** tab, connect neonloops and complete account
   linking. An organization owner may need to allow the connector.
5. Start a new chat and select **Create a neonloops workflow**.

The [Claude plugin guide](https://claude.com/docs/plugins/build) documents repository
installation. If you prefer a personal upload, download
[neonloops-workflows.zip](https://github.com/neonloops/plugins/releases/latest/download/neonloops-workflows.zip)
and choose **Add → Upload plugin**. Upload the plugin ZIP, not GitHub's repository
source ZIP. A personal upload does not track marketplace releases.

### Claude Code

Run these commands in your terminal:

```sh
claude plugin marketplace add neonloops/plugins
claude plugin install neonloops-workflows@neonloops-public
```

Start a new session, then invoke `/neonloops-workflows:create-workflow` with the job
you want repeated. Complete the neonloops server's OAuth flow when prompted. Local
Claude Code installation does not also install the plugin into your claude.ai
account. See [Claude's installation guide](https://code.claude.com/docs/en/plugins/install).

### Codex

Run these commands in a terminal with the current Codex CLI installed:

```sh
codex plugin marketplace add neonloops/plugins
codex plugin add neonloops-workflows@neonloops-public
codex plugin list --marketplace neonloops-public --json
```

The listing should show version `0.1.2` (or a newer release), `installed: true` and
`enabled: true`. Start a new Codex chat, select the skill or use `$create-workflow`,
and finish neonloops account linking. These are the supported
[Codex plugin commands](https://learn.chatgpt.com/docs/developer-commands#codex-plugin).
No package build, Python script or SDK is needed.

### Connect your own workspace

The host handles OAuth. Sign in to neonloops, choose your workspace and review the
requested permissions. Reading your workspace and changing it are separate
capabilities; workflow creation needs the relevant write permission. Never paste an
API token into a prompt. Installing this package does not grant workspace access.

Connections used by a workflow, such as a CRM or email account, are configured in
**neonloops → Connectors**. They are separate from the host's neonloops connection.
The skill checks required actions and events before using them and asks for missing
project, source, trigger, destination or review details. If bundled references or MCP
tools cannot be loaded, it reports the limitation before creating anything.

The skill works through the declared neonloops connector. Workspace content and run
history are stored in neonloops; the workflows you configure may send their inputs
to AI providers and connected apps. The package has no additional data-collection
scripts. Read the [privacy policy](https://neonloops.com/privacy) and
[terms of service](https://neonloops.com/terms) before linking your workspace.

### Update or remove

For **Claude Code**, update the catalog and installed plugin:

```sh
claude plugin marketplace update neonloops-public
claude plugin update neonloops-workflows@neonloops-public
```

To remove it from the default user scope:

```sh
claude plugin uninstall neonloops-workflows@neonloops-public
```

For **Codex**, refresh the catalog, then reinstall from it to replace the cached
package:

```sh
codex plugin marketplace upgrade neonloops-public
codex plugin remove neonloops-workflows@neonloops-public
codex plugin add neonloops-workflows@neonloops-public
codex plugin list --marketplace neonloops-public --json
```

To remove only, run the `codex plugin remove` command. Start a new chat after a
change. These commands affect only `neonloops-workflows@neonloops-public`, leaving
other marketplaces and plugins in place.

For **Claude / Cowork**, manage the installed plugin in **Customize → Plugins**.
Use the host's marketplace refresh and plugin management controls, and check the
version on the plugin details page. For a personal ZIP upload, download the new ZIP
and replace that uploaded copy. See
[Claude plugin management](https://claude.com/docs/plugins/build) for the current
host flow. To stop workspace access as well, revoke the agent from
**neonloops → Settings → Connected agents**. Removing the plugin does not delete
workflows already saved in neonloops or stop their active triggers.

## Ask for the work you want repeated

- “Every Monday at 09:00 Europe/Vienna, prepare a sales pipeline exception digest
  from our open-deals table. Save a private report. Set up a draft first.”
- “When a support inquiry arrives, classify it and route it under our existing
  policy. Send ambiguous cases to review. Use recipe service-01.”
- “Every week, compare supplier renewals with usage and notice deadlines. Prepare
  a decision brief; purchasing decisions stay with me.”
- “Resume the interrupted sales-06 installation in this project. Preserve the
  source table and my edits.”
- “Activate the workflow we just reviewed and verify its schedule. Use the sample
  records and the verification budget I already approved.”

The installer asks only for missing project, source, trigger, destination or review
details. It resolves the current connector actions and events, saves the actual task
instructions inside Agent nodes, validates the graph and reports what remains.
Runtime workspace skills are optional; ordinary installation does not require a
new workspace skill or dangerous skill-write permission.

Agent steps use Claude models because the long-running agent work is built on
Claude's managed agent infrastructure. Model access is handled by neonloops; the
installer does not ask you to supply a model-provider key or configure billing.

## Know what has been proved

The catalog contains **authored adaptations**, not 67 live-tested installations.
Its sources establish documented business patterns, not popularity or customer
demand. There are 42 private-artifact outcomes, 18 connected-app write outcomes and
seven external-send/publication outcomes. Each recipe has a specific sample and
expected result, required inputs and decision boundary.

The installer distinguishes saved draft, structural validation, simulated execution,
real execution and armed trigger. Draft simulation uses real model calls and spend
while neutralizing side effects; it cannot prove delivery, persisted writes, stored
artifacts or reviewer routing. A publish response alone is insufficient: the skill
checks actual trigger health and reports incomplete activation honestly.

Financial and legal recipes prepare evidence for a responsible person. People
recipes coordinate administrative work and preserve human employment decisions.
No recipe authorizes money movement, eligibility decisions, account revocation,
signature acceptance or production changes. Routine internal writes can use the
bounded policy you already authorized; the graph makes exceptions and required
human decisions explicit.

## Package contents

| File                                               | Consumer                                                      |
| -------------------------------------------------- | ------------------------------------------------------------- |
| `plugin.json` + `mcp.json`                         | Portable/OpenAI package; `/api/mcp/openai`                    |
| `.codex-plugin/plugin.json` with inline MCP object | Explicit Codex compatibility; `/api/mcp/openai`               |
| `.claude-plugin/plugin.json` + `.mcp.json`         | Claude/Cowork; `/api/mcp/v1`                                  |
| `skills/create-workflow/`                          | The same skill, catalog, protocols and recipes for every host |
| `LICENSE`                                          | Repository's exact MIT terms                                  |

The [catalog](skills/create-workflow/references/catalog.md) and
[structured catalog with evidence links](skills/create-workflow/references/catalog.json)
are included with the skill. All runtime references are inside this package; no
private source repository or developer checkout is needed. Support and setup:
[neonloops.com/mcp](https://neonloops.com/mcp) · [hi@neonloops.com](mailto:hi@neonloops.com).
