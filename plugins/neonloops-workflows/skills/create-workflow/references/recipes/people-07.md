# Leave-request approval routing

- **Recipe:** `people-07` · version `0.1.0` · People operations
- **Trigger intent:** When an employee submits leave.
- **Outcome:** Approval packet and recorded approver decision.
- **Runtime plan:** [B](../runtime-plans.md) with [the shared installation protocol](../installation.md).
- **Runtime skill:** optional. Essential task/input/output instructions are saved inline in Agent nodes.
- **Side effects:** `external_write`. The outcome describes the intended completed workflow, not a claim that it has run.
- **Status:** authored adaptation; connector/tool/event support unverified until runtime discovery; not live-tested across candidate apps.

## Inputs to resolve

- Request: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- policy: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- work calendar: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- designated approver: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- Target workspace/project and selected source record/view/folder IDs, relevant fields and access scope.
- For a schedule: cadence, timezone, look-back/look-ahead window and record cap. For an app event: actual supported event and payload mapping.
- Exact output destination and filename or connected-app target; reviewer/authorized policy where the steps require one.
- A designated safe sample, permitted verification spend, and whether the user requested draft setup or activation.

Reuse facts already supplied. The candidates below are alternatives, not a requirement to connect every app. No matching trigger/action means a recoverable partial setup; offer a supported alternative for the user to choose, never substitute one silently.

## Actual decision persistence

During preparation, `approverDecision` and `decisionRecord` are pending. Apply plan B’s decision-record variant: both actual Approval branches write only the manager’s observed decision to the permitted record, then End reports that write result. A rejected request performs no approved leave action but still records the human rejection. Timeout is a distinct timed-out/pending-review state, never a fabricated manager decision.

## Ordered workflow and saved task

1. Resolve the actual trigger for “When an employee submits leave” and a bounded source scope. Read the selected records and preserve their IDs, timestamps and links.
2. Deterministic preparation: Calculate requested dates/days with the approved work calendar and leave policy.
3. Agent preparation: Explain missing details and coverage conflicts. Produce `requestFacts, coverageConflicts, approverDecision, decisionRecord, sourceReferences, missingData`. Explain evidence for each conclusion and preserve uncertainty. This node prepares the result and performs no external write.
4. Decision boundary: Manager decides; disclose minimum necessary employee data. Use plan B with the required human decision, or the already authorized bounded policy for routine internal writes. Configure exception handling and preserve the user’s actual authorization.
5. Deterministic output: Route the leave packet to the designated manager, then record only their actual decision in the permitted record.
6. Read actual result/action IDs and compare the sample criteria below. Return partial effects if one ordered action succeeds and another fails.

**Agent output contract:** `requestFacts, coverageConflicts, approverDecision, decisionRecord, sourceReferences, missingData`. Choose appropriate live-schema types for these fields; each list item includes its relevant source identity. Persist step 3, the domain decision boundary, missing-data behavior and the following case-specific rule into the actual `systemPrompt`: “Do not infer medical reasons or grant/deny leave automatically.” Map actual upstream/bound variables into `userPrompt`; a recipe link alone is insufficient.

**Connector candidates — unverified:** Microsoft Forms, SharePoint, Teams, BambooHR. Discover actual toolkit names, read/action/trigger schemas and active accounts from MCP. Resolve every source/destination identifier. If public research is needed, use only a runtime tool actually available to the Agent; a host's browser access does not imply recurring runtime access.

**Permission and unattended behavior:** resolve only the capabilities and tool allowlists this graph needs. Keep preparation tools read-only. An Agent with `runtime.connectorPermission:"ask"` may pause on connector access; report it. Set `allow` only for an already authorized appropriately restricted toolset. Required business approvals still apply; no recipe-level text replaces a saved approval/policy node.

## Representative sample and verification

- **Sample input:** A request overlaps a team coverage rule; the manager has not decided.
- **Expected result:** Present the conflict, then record only the manager's actual approval/rejection result.
- **Negative or missing-data case:** Do not infer medical reasons or grant/deny leave automatically.
- **Inspect:** source-to-output identity/field mapping, actual calculated values, required result fields, missing-data flags, and the final output/tool-result references. No records in scope must produce an explicit empty result rather than fabricated activity.
- **Proof boundary:** structural validation proves graph shape; draft simulation uses real model spend but neutralizes writes and auto-approves review. Only an authorized real run with inspected results proves the promised artifact/actions. Trigger health is separate and must be checked after publication.

## Pattern evidence

- [Create and test approval workflow](https://learn.microsoft.com/en-us/power-automate/modern-approvals) — source ID `ms-approval`, official_documentation; inspected as search excerpt.
- [HR automation ideas](https://zapier.com/blog/human-resources-automation/) — source ID `zap-hr`, vendor_guide; inspected as page text.

These sources support the business pattern; this recipe's task plan and boundaries are an original authored adaptation. They do not establish popularity, measured demand, neonloops connector coverage, client loading, or successful execution. Preserve this evidence level when adapting the recipe.
