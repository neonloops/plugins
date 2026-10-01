# Recipe contract · 1.0

`catalog.json` is the countable index; `catalog.md` is its human routing view. Each
catalog record links to exactly one recipe document in `recipes/`. IDs count distinct
business outcomes, not app pair permutations. Version 0.1.0 applies to the authored
recipe, independent of any installed workflow's current revision.

Each recipe declares:

- ID, domain, title, version, trigger intent, input facts still to resolve and optional
  runtime-skill policy (`optional`; inline instructions are always required).
- Outcome and ordered source/deterministic/Agent/review/output steps, with the exact
  business-specific Agent task, result fields and proposed action.
- Connector candidates with `unverified` status; tools, events, accounts, data shapes
  and source/destination IDs are resolved at installation time.
- Side-effect class (`artifact_only`, `external_write`, `external_send`) and a specific
  human decision or bounded preauthorized policy. A private artifact can contain
  sensitive information and still needs the declared access boundary.
- A recipe-specific sample, expected result, negative case and evidence to inspect.
- Primary/vendor source URLs and source IDs supporting the pattern. All recipes are
  original authored adaptations; no source establishes neonloops execution, connector
  support, market share, customer demand or popularity.

Shared [installation](installation.md) and [runtime plans](runtime-plans.md) are part
of every recipe. Do not copy only the recipe's heading into an Agent node. Compose
its actual task and data contract into saved node instructions, then map real source
variables and verify its specific result. Optional runtime skill mounting is never
a substitute for persisting essential instructions inline.

Evidence levels are independent: authored → schema inspected → structurally
validated → simulated → executed; trigger activation is separately observed. Package
authorship/structural validation does not raise every recipe to live-tested. Record
workspace-specific evidence in the installation handoff, not by changing a catalog
entry's connector status for all customers.
