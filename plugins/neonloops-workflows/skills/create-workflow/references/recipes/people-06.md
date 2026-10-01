# Departure handoff coordination

- **Recipe:** `people-06` · version `0.1.0` · People operations
- **Trigger intent:** When HR authorizes an employee departure.
- **Outcome:** Assigned offboarding checklist with completion-evidence fields.
- **Runtime plan:** [B](../runtime-plans.md) with [the shared installation protocol](../installation.md).
- **Runtime skill:** optional. Essential task/input/output instructions are saved inline in Agent nodes.
- **Side effects:** `external_write`. The outcome describes the intended completed workflow, not a claim that it has run.
- **Status:** authored adaptation; connector/tool/event support unverified until runtime discovery; not live-tested across candidate apps.

## Inputs to resolve

- Departure date: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- owned work: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- asset and access records: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- Target workspace/project and selected source record/view/folder IDs, relevant fields and access scope.
- For a schedule: cadence, timezone, look-back/look-ahead window and record cap. For an app event: actual supported event and payload mapping.
- Exact output destination and filename or connected-app target; reviewer/authorized policy where the steps require one.
- A designated safe sample, permitted verification spend, and whether the user requested draft setup or activation.

Reuse facts already supplied. The candidates below are alternatives, not a requirement to connect every app. No matching trigger/action means a recoverable partial setup; offer a supported alternative for the user to choose, never substitute one silently.

## Additional evidence prerequisite

A new checklist starts pending. Completion fields may contain only actual source receipts, completed-task records or named owner attestations already available. Creating the checklist does not prove assets returned, accounts revoked or work transferred; later evidence reconciliation needs its own agreed trigger.

## Ordered workflow and saved task

1. Resolve the actual trigger for “When HR authorizes an employee departure” and a bounded source scope. Read the selected records and preserve their IDs, timestamps and links.
2. Deterministic preparation: Resolve authorized departure date and compare documented assets/work with the checklist.
3. Agent preparation: Identify transfer gaps and prepare team-specific checklists. Produce `handoffTasks, assetChecklist, ownershipGaps, completionEvidence, sourceReferences, missingData`. Explain evidence for each conclusion and preserve uncertainty. This node prepares the result and performs no external write.
4. Decision boundary: Human owns termination; no autonomous account deletion or revocation. Use plan B with the required human decision, or the already authorized bounded policy for routine internal writes. Configure exception handling and preserve the user’s actual authorization.
5. Deterministic output: Create authorized offboarding/handoff tasks; read actual task status for completion evidence.
6. Read actual result/action IDs and compare the sample criteria below. Return partial effects if one ordered action succeeds and another fails.

**Agent output contract:** `handoffTasks, assetChecklist, ownershipGaps, completionEvidence, sourceReferences, missingData`. Choose appropriate live-schema types for these fields; each list item includes its relevant source identity. Persist step 3, the domain decision boundary, missing-data behavior and the following case-specific rule into the actual `systemPrompt`: “Do not terminate employment, revoke access or delete accounts.” Map actual upstream/bound variables into `userPrompt`; a recipe link alone is insufficient.

**Connector candidates — unverified:** BambooHR, Workday, Jira Service Management, Asana. Discover actual toolkit names, read/action/trigger schemas and active accounts from MCP. Resolve every source/destination identifier. If public research is needed, use only a runtime tool actually available to the Agent; a host's browser access does not imply recurring runtime access.

**Permission and unattended behavior:** resolve only the capabilities and tool allowlists this graph needs. Keep preparation tools read-only. An Agent with `runtime.connectorPermission:"ask"` may pause on connector access; report it. Set `allow` only for an already authorized appropriately restricted toolset. Required business approvals still apply; no recipe-level text replaces a saved approval/policy node.

## Representative sample and verification

- **Sample input:** A departing employee owns an active customer project with no successor recorded.
- **Expected result:** Create the handoff task and show missing successor; completion requires actual task evidence.
- **Negative or missing-data case:** Do not terminate employment, revoke access or delete accounts.
- **Inspect:** source-to-output identity/field mapping, actual calculated values, required result fields, missing-data flags, and the final output/tool-result references. No records in scope must produce an explicit empty result rather than fabricated activity.
- **Proof boundary:** structural validation proves graph shape; draft simulation uses real model spend but neutralizes writes and auto-approves review. Only an authorized real run with inspected results proves the promised artifact/actions. Trigger health is separate and must be checked after publication.

## Pattern evidence

- [Employee onboarding and offboarding](https://zapier.com/blog/automate-employee-onboarding-offboarding/) — source ID `zap-onoff`, vendor_guide; inspected as search excerpt.
- [HR automation](https://www.make.com/en/solutions/automate-hr) — source ID `make-hr`, vendor_guide; inspected as search excerpt.

These sources support the business pattern; this recipe's task plan and boundaries are an original authored adaptation. They do not establish popularity, measured demand, neonloops connector coverage, client loading, or successful execution. Preserve this evidence level when adapting the recipe.
