# Customer feedback follow-up

- **Recipe:** `service-09` · version `0.1.0` · Customer service
- **Trigger intent:** When post-support survey feedback arrives.
- **Outcome:** Approved follow-up email and owner task.
- **Runtime plan:** [B](../runtime-plans.md) with [the shared installation protocol](../installation.md).
- **Runtime skill:** optional. Essential task/input/output instructions are saved inline in Agent nodes.
- **Side effects:** `external_send`. The outcome describes the intended completed workflow, not a claim that it has run.
- **Status:** authored adaptation; connector/tool/event support unverified until runtime discovery; not live-tested across candidate apps.

## Inputs to resolve

- Rating: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- comment: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- relevant case: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- contact consent: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- Target workspace/project and selected source record/view/folder IDs, relevant fields and access scope.
- For a schedule: cadence, timezone, look-back/look-ahead window and record cap. For an app event: actual supported event and payload mapping.
- Exact output destination and filename or connected-app target; reviewer/authorized policy where the steps require one.
- A designated safe sample, permitted verification spend, and whether the user requested draft setup or activation.

Reuse facts already supplied. The candidates below are alternatives, not a requirement to connect every app. No matching trigger/action means a recoverable partial setup; offer a supported alternative for the user to choose, never substitute one silently.

## Ordered workflow and saved task

1. Resolve the actual trigger for “When post-support survey feedback arrives” and a bounded source scope. Read the selected records and preserve their IDs, timestamps and links.
2. Deterministic preparation: Resolve survey-to-case linkage, recipient consent and any existing follow-up.
3. Agent preparation: Interpret concern and draft a tailored follow-up. Produce `feedbackConcern, caseContext, draftFollowUp, ownerTask, sourceReferences, missingData`. Explain evidence for each conclusion and preserve uncertainty. This node prepares the result and performs no external write.
4. Decision boundary: Review recipient and message; avoid selective deceptive review solicitation. Use plan B with the required human decision, or the already authorized bounded policy for routine internal writes. Configure exception handling and preserve the user’s actual authorization.
5. Immediate pre-effect check: After the review wait, re-read the confirmed recipient's current consent, opt-out and suppression state from the authoritative source through a discovered supported read tool. Apply the agreed eligibility rule deterministically as required by plan B. Revoked consent, suppression, changed eligibility, an unavailable read or unknown state holds/skips the email. If the recipient or facts affecting the approved message change, return the updated proposal to review. Unchanged eligible recipients keep the existing authorization; a later wait/retry requires a fresh check.
6. Deterministic output: Send only the approved, currently eligible follow-up email, then create the owner task with the case and confirmed send references. A held/skipped send must not create its send-dependent task or imply delivery.
7. Read actual result/action IDs and compare the sample criteria below. Return partial effects if one ordered action succeeds and another fails.

**Agent output contract:** `feedbackConcern, caseContext, draftFollowUp, ownerTask, sourceReferences, missingData`. Choose appropriate live-schema types for these fields; each list item includes its relevant source identity. Persist step 3, the domain decision boundary, missing-data behavior and the following case-specific rule into the actual `systemPrompt`: “Do not solicit public reviews only from happy customers or expose another case's details.” Map actual upstream/bound variables into `userPrompt`; a recipe link alone is insufficient.

**Connector candidates — unverified:** Typeform, SurveyMonkey, HubSpot, Gmail, Zendesk. Discover actual toolkit names, read/action/trigger schemas and active accounts from MCP. Resolve every source/destination identifier. If public research is needed, use only a runtime tool actually available to the Agent; a host's browser access does not imply recurring runtime access.

**Permission and unattended behavior:** resolve only the capabilities and tool allowlists this graph needs. Keep preparation tools read-only. An Agent with `runtime.connectorPermission:"ask"` may pause on connector access; report it. Set `allow` only for an already authorized appropriately restricted toolset. Required business approvals still apply; no recipe-level text replaces a saved approval/policy node.

## Representative sample and verification

- **Sample input:** A low rating cites a delayed response on a resolved case. The recipient has consent when the draft is prepared, then revokes it while human approval is pending; the reviewer subsequently approves the original draft.
- **Expected result:** The post-wait read observes revoked consent and the deterministic gate holds/skips the email and its send-dependent owner task, returning the current evidence and reason with `actionTaken:false`. As a positive control, an unchanged, currently consenting and unsuppressed recipient receives the approved response and authorized owner task; inspect both action results.
- **Negative or missing-data case:** Approval must not override withdrawn consent. Missing/unreadable consent or suppression data also holds/skips the send; a changed recipient or approved payload returns to review. Do not solicit public reviews only from happy customers or expose another case's details.
- **Inspect:** source-to-output identity/field mapping, actual calculated values, required result fields, missing-data flags, and the final output/tool-result references. No records in scope must produce an explicit empty result rather than fabricated activity.
- **Proof boundary:** structural validation proves graph shape; draft simulation uses real model spend but neutralizes writes and auto-approves review. Only an authorized real run with inspected results proves the promised artifact/actions. Trigger health is separate and must be checked after publication.

## Pattern evidence

- [Workflow automation guide](https://www.hubspot.com/products/workflow-automation-guide?department=sales) — source ID `hubspot-guide`, vendor_guide; inspected as page text.
- [Customer support automation](https://zapier.com/automation/customer-automation/customer-support) — source ID `zap-support`, vendor_guide; inspected as page text.

These sources support the business pattern; this recipe's task plan and boundaries are an original authored adaptation. They do not establish popularity, measured demand, neonloops connector coverage, client loading, or successful execution. Preserve this evidence level when adapting the recipe.
