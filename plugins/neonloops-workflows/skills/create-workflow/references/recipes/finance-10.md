# Vendor renewal decision brief

- **Recipe:** `finance-10` · version `0.1.0` · Finance and procurement
- **Trigger intent:** Before vendor cancellation or renewal deadlines.
- **Outcome:** Renewal brief with keep, change or investigate options.
- **Runtime plan:** [A](../runtime-plans.md) with [the shared installation protocol](../installation.md).
- **Runtime skill:** optional. Essential task/input/output instructions are saved inline in Agent nodes.
- **Side effects:** `artifact_only`. The outcome describes the intended completed workflow, not a claim that it has run.
- **Status:** authored adaptation; connector/tool/event support unverified until runtime discovery; not live-tested across candidate apps.

## Inputs to resolve

- Contract: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- usage: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- costs: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- price changes: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- alternatives: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- Target workspace/project and selected source record/view/folder IDs, relevant fields and access scope.
- For a schedule: cadence, timezone, look-back/look-ahead window and record cap. For an app event: actual supported event and payload mapping.
- Exact output destination and filename or connected-app target; reviewer/authorized policy where the steps require one.
- A designated safe sample, permitted verification spend, and whether the user requested draft setup or activation.

Reuse facts already supplied. The candidates below are alternatives, not a requirement to connect every app. No matching trigger/action means a recoverable partial setup; offer a supported alternative for the user to choose, never substitute one silently.

## Ordered workflow and saved task

1. Resolve the actual trigger for “Before vendor cancellation or renewal deadlines” and a bounded source scope. Read the selected records and preserve their IDs, timestamps and links.
2. Deterministic preparation: Calculate verified notice deadlines and compare like-for-like cost periods.
3. Agent preparation: Reconcile notice dates and value actually used. Produce `noticeDates, usageEvidence, commercialChanges, decisionOptions, sourceReferences, missingData`. Explain evidence for each conclusion and preserve uncertainty. This node prepares the result and performs no external write.
4. Decision boundary: Human cancels, renews or negotiates; verify extracted dates. This artifact is preparation for that decision; producing it does not approve a later business action.
5. Deterministic output: Save the mapped structured result as a private neonloops artifact through End; do not write to connected business apps.
6. Read actual result/action IDs and compare the sample criteria below. Return partial effects if one ordered action succeeds and another fails.

**Agent output contract:** `noticeDates, usageEvidence, commercialChanges, decisionOptions, sourceReferences, missingData`. Choose appropriate live-schema types for these fields; each list item includes its relevant source identity. Persist step 3, the domain decision boundary, missing-data behavior and the following case-specific rule into the actual `systemPrompt`: “Do not cancel or renew; uncertain extracted dates require human verification.” Map actual upstream/bound variables into `userPrompt`; a recipe link alone is insufficient.

**Connector candidates — unverified:** Google Drive, Google Sheets, Notion, procurement system. Discover actual toolkit names, read/action/trigger schemas and active accounts from MCP. Resolve every source/destination identifier. If public research is needed, use only a runtime tool actually available to the Agent; a host's browser access does not imply recurring runtime access.

**Permission and unattended behavior:** resolve only the capabilities and tool allowlists this graph needs. Keep preparation tools read-only. An Agent with `runtime.connectorPermission:"ask"` may pause on connector access; report it. Set `allow` only for an already authorized appropriately restricted toolset. Required business approvals still apply; no recipe-level text replaces a saved approval/policy node.

## Representative sample and verification

- **Sample input:** A vendor auto-renews in 60 days with 30 days' notice; usage has fallen.
- **Expected result:** Show the notice deadline and evidence-backed keep/change/investigate options.
- **Negative or missing-data case:** Do not cancel or renew; uncertain extracted dates require human verification.
- **Inspect:** source-to-output identity/field mapping, actual calculated values, required result fields, missing-data flags, and the final output/tool-result references. No records in scope must produce an explicit empty result rather than fabricated activity.
- **Proof boundary:** structural validation proves graph shape; draft simulation uses real model spend but neutralizes writes and auto-approves review. Only an authorized real run with inspected results proves the promised artifact/actions. Trigger health is separate and must be checked after publication.

## Pattern evidence

- [Monitor SaaS contract renewals](https://n8n.io/workflows/15496-monitor-saas-contract-renewals-from-google-sheets-and-send-slack-alerts/) — source ID `n8n-saas-renewal`, author_template; inspected as search excerpt.
- [Expense management](https://zapier.com/automations/finance/expense-management) — source ID `zap-expenses`, vendor_guide; inspected as page text.

These sources support the business pattern; this recipe's task plan and boundaries are an original authored adaptation. They do not establish popularity, measured demand, neonloops connector coverage, client loading, or successful execution. Preserve this evidence level when adapting the recipe.
