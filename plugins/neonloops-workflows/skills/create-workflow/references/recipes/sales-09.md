# Buying-signal follow-up queue

- **Recipe:** `sales-09` · version `0.1.0` · Sales
- **Trigger intent:** When product, website or account signals cross configured rules.
- **Outcome:** Prioritized outreach task with source events.
- **Runtime plan:** [B](../runtime-plans.md) with [the shared installation protocol](../installation.md).
- **Runtime skill:** optional. Essential task/input/output instructions are saved inline in Agent nodes.
- **Side effects:** `external_write`. The outcome describes the intended completed workflow, not a claim that it has run.
- **Status:** authored adaptation; connector/tool/event support unverified until runtime discovery; not live-tested across candidate apps.

## Inputs to resolve

- Usage: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- consented engagement: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- account events: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- CRM owner: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- Target workspace/project and selected source record/view/folder IDs, relevant fields and access scope.
- For a schedule: cadence, timezone, look-back/look-ahead window and record cap. For an app event: actual supported event and payload mapping.
- Exact output destination and filename or connected-app target; reviewer/authorized policy where the steps require one.
- A designated safe sample, permitted verification spend, and whether the user requested draft setup or activation.

Reuse facts already supplied. The candidates below are alternatives, not a requirement to connect every app. No matching trigger/action means a recoverable partial setup; offer a supported alternative for the user to choose, never substitute one silently.

## Ordered workflow and saved task

1. Resolve the actual trigger for “When product, website or account signals cross configured rules” and a bounded source scope. Read the selected records and preserve their IDs, timestamps and links.
2. Deterministic preparation: Apply explicit consent, event-window and threshold rules before building the task.
3. Agent preparation: Combine signals into a reasoned opportunity context. Produce `accountId, signalEvidence, priorityReason, outreachTask, sourceReferences, missingData`. Explain evidence for each conclusion and preserve uncertainty. This node prepares the result and performs no external write.
4. Decision boundary: No sensitive-person inference or unapproved contact. Use plan B with the required human decision, or the already authorized bounded policy for routine internal writes. Configure exception handling and preserve the user’s actual authorization.
5. Deterministic output: Create the authorized outreach task in the selected CRM or task system; do not contact the lead.
6. Read actual result/action IDs and compare the sample criteria below. Return partial effects if one ordered action succeeds and another fails.

**Agent output contract:** `accountId, signalEvidence, priorityReason, outreachTask, sourceReferences, missingData`. Choose appropriate live-schema types for these fields; each list item includes its relevant source identity. Persist step 3, the domain decision boundary, missing-data behavior and the following case-specific rule into the actual `systemPrompt`: “An opted-out contact or stale event cannot qualify for outreach.” Map actual upstream/bound variables into `userPrompt`; a recipe link alone is insufficient.

**Connector candidates — unverified:** HubSpot, Salesforce, Segment, Mixpanel. Discover actual toolkit names, read/action/trigger schemas and active accounts from MCP. Resolve every source/destination identifier. If public research is needed, use only a runtime tool actually available to the Agent; a host's browser access does not imply recurring runtime access.

**Permission and unattended behavior:** resolve only the capabilities and tool allowlists this graph needs. Keep preparation tools read-only. An Agent with `runtime.connectorPermission:"ask"` may pause on connector access; report it. Set `allow` only for an already authorized appropriately restricted toolset. Required business approvals still apply; no recipe-level text replaces a saved approval/policy node.

## Representative sample and verification

- **Sample input:** An opted-in account has three qualifying product events in the agreed week.
- **Expected result:** Create the authorized owner task with those event IDs and a reason tied to the supplied rule.
- **Negative or missing-data case:** An opted-out contact or stale event cannot qualify for outreach.
- **Inspect:** source-to-output identity/field mapping, actual calculated values, required result fields, missing-data flags, and the final output/tool-result references. No records in scope must produce an explicit empty result rather than fabricated activity.
- **Proof boundary:** structural validation proves graph shape; draft simulation uses real model spend but neutralizes writes and auto-approves review. Only an authorized real run with inspected results proves the promised artifact/actions. Trigger health is separate and must be checked after publication.

## Pattern evidence

- [Workflow automation guide](https://www.hubspot.com/products/workflow-automation-guide?department=sales) — source ID `hubspot-guide`, vendor_guide; inspected as page text.
- [Sales automation](https://www.make.com/en/solutions/automate-sales) — source ID `make-sales`, vendor_guide; inspected as search excerpt.

These sources support the business pattern; this recipe's task plan and boundaries are an original authored adaptation. They do not establish popularity, measured demand, neonloops connector coverage, client loading, or successful execution. Preserve this evidence level when adapting the recipe.
