# Support quality and trend review

- **Recipe:** `service-04` · version `0.1.0` · Customer service
- **Trigger intent:** Every week.
- **Outcome:** Quality report with ticket evidence.
- **Runtime plan:** [A](../runtime-plans.md) with [the shared installation protocol](../installation.md).
- **Runtime skill:** optional. Essential task/input/output instructions are saved inline in Agent nodes.
- **Side effects:** `artifact_only`. The outcome describes the intended completed workflow, not a claim that it has run.
- **Status:** authored adaptation; connector/tool/event support unverified until runtime discovery; not live-tested across candidate apps.

## Inputs to resolve

- Resolved tickets: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- review rubric: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- sampled transcripts: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- Target workspace/project and selected source record/view/folder IDs, relevant fields and access scope.
- For a schedule: cadence, timezone, look-back/look-ahead window and record cap. For an app event: actual supported event and payload mapping.
- Exact output destination and filename or connected-app target; reviewer/authorized policy where the steps require one.
- A designated safe sample, permitted verification spend, and whether the user requested draft setup or activation.

Reuse facts already supplied. The candidates below are alternatives, not a requirement to connect every app. No matching trigger/action means a recoverable partial setup; offer a supported alternative for the user to choose, never substitute one silently.

## Ordered workflow and saved task

1. Resolve the actual trigger for “Every week” and a bounded source scope. Read the selected records and preserve their IDs, timestamps and links.
2. Deterministic preparation: Use the agreed sample and count distinct case IDs rather than individual messages.
3. Agent preparation: Find recurring failures and explain review findings. Produce `themes, rubricFindings, supportingTickets, reviewLimitations, sourceReferences, missingData`. Explain evidence for each conclusion and preserve uncertainty. This node prepares the result and performs no external write.
4. Decision boundary: Human evaluates staff; no automatic disciplinary decisions. This artifact is preparation for that decision; producing it does not approve a later business action.
5. Deterministic output: Save the mapped structured result as a private neonloops artifact through End; do not write to connected business apps.
6. Read actual result/action IDs and compare the sample criteria below. Return partial effects if one ordered action succeeds and another fails.

**Agent output contract:** `themes, rubricFindings, supportingTickets, reviewLimitations, sourceReferences, missingData`. Choose appropriate live-schema types for these fields; each list item includes its relevant source identity. Persist step 3, the domain decision boundary, missing-data behavior and the following case-specific rule into the actual `systemPrompt`: “Do not turn agent commentary into an employee rating or disciplinary decision.” Map actual upstream/bound variables into `userPrompt`; a recipe link alone is insufficient.

**Connector candidates — unverified:** Zendesk, Intercom, Google Sheets, Notion. Discover actual toolkit names, read/action/trigger schemas and active accounts from MCP. Resolve every source/destination identifier. If public research is needed, use only a runtime tool actually available to the Agent; a host's browser access does not imply recurring runtime access.

**Permission and unattended behavior:** resolve only the capabilities and tool allowlists this graph needs. Keep preparation tools read-only. An Agent with `runtime.connectorPermission:"ask"` may pause on connector access; report it. Set `allow` only for an already authorized appropriately restricted toolset. Required business approvals still apply; no recipe-level text replaces a saved approval/policy node.

## Required scope and result checks

State sampling method/window, ticket denominator, supplied rubric and finding counts; each quality finding links to transcript evidence and each theme to supporting cases.

Boundary check: One sentiment label is not a rubric failure; unavailable transcript cannot receive a quality score. Sample findings are not represented as whole-population rates.

## Representative sample and verification

- **Sample input:** Five sampled cases include two repeated handoff failures in the same case.
- **Expected result:** Report the issue with correct case counts and cite the sampled evidence.
- **Negative or missing-data case:** Do not turn agent commentary into an employee rating or disciplinary decision.
- **Inspect:** source-to-output identity/field mapping, actual calculated values, required result fields, missing-data flags, and the final output/tool-result references. No records in scope must produce an explicit empty result rather than fabricated activity.
- **Proof boundary:** structural validation proves graph shape; draft simulation uses real model spend but neutralizes writes and auto-approves review. Only an authorized real run with inspected results proves the promised artifact/actions. Trigger health is separate and must be checked after publication.

## Evidence scope

The cited templates document ticket classification and sentiment. Rubric-based quality review is this recipe’s proposed extension; no claimed accuracy, time saving or compliance benefit is inherited from a template.

## Pattern evidence

- [Customer support automation](https://zapier.com/automation/customer-automation/customer-support) — source ID `zap-support`, vendor_guide; inspected as page text.
- [Categorize support tickets and report](https://n8n.io/workflows/4447-categorize-support-tickets-with-gemini-ai-typeform-and-google-sheets-reporting/) — source ID `n8n-ticket-report`, author_template; inspected as search excerpt.

These sources support the business pattern; this recipe's task plan and boundaries are an original authored adaptation. They do not establish popularity, measured demand, neonloops connector coverage, client loading, or successful execution. Preserve this evidence level when adapting the recipe.
