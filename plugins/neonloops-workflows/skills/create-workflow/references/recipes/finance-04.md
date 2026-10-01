# Overdue receivable follow-up

- **Recipe:** `finance-04` · version `0.1.0` · Finance and procurement
- **Trigger intent:** Every business day for overdue invoices.
- **Outcome:** Approved reminder email with case context.
- **Runtime plan:** [B](../runtime-plans.md) with [the shared installation protocol](../installation.md).
- **Runtime skill:** optional. Essential task/input/output instructions are saved inline in Agent nodes.
- **Side effects:** `external_send`. The outcome describes the intended completed workflow, not a claim that it has run.
- **Status:** authored adaptation; connector/tool/event support unverified until runtime discovery; not live-tested across candidate apps.

## Inputs to resolve

- Invoice age: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- payment status: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- dispute notes: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- terms: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- Target workspace/project and selected source record/view/folder IDs, relevant fields and access scope.
- For a schedule: cadence, timezone, look-back/look-ahead window and record cap. For an app event: actual supported event and payload mapping.
- Exact output destination and filename or connected-app target; reviewer/authorized policy where the steps require one.
- A designated safe sample, permitted verification spend, and whether the user requested draft setup or activation.

Reuse facts already supplied. The candidates below are alternatives, not a requirement to connect every app. No matching trigger/action means a recoverable partial setup; offer a supported alternative for the user to choose, never substitute one silently.

## Additional evidence prerequisite

Immediately before the approved send, re-read current outstanding balance, payment allocation and dispute status through a verified read action. Compare with the approved amount deterministically; a changed amount/status routes back to review and must not reuse stale approval.

## Ordered workflow and saved task

1. Resolve the actual trigger for “Every business day for overdue invoices” and a bounded source scope. Read the selected records and preserve their IDs, timestamps and links.
2. Deterministic preparation: Compute days overdue and verify current payment/dispute status before generating an action.
3. Agent preparation: Distinguish missing payment from disputed or already-paid cases. Produce `invoiceFacts, paymentChecks, disputeStatus, reminderDraft, sourceReferences, missingData`. Explain evidence for each conclusion and preserve uncertainty. This node prepares the result and performs no external write.
4. Decision boundary: Human approves amount, recipient and wording; no collections threats. Use plan B with the required human decision, or the already authorized bounded policy for routine internal writes. Configure exception handling and preserve the user’s actual authorization.
5. Deterministic output: Send the approved reminder only after current payment/dispute checks and recipient/amount verification.
6. Read actual result/action IDs and compare the sample criteria below. Return partial effects if one ordered action succeeds and another fails.

**Agent output contract:** `invoiceFacts, paymentChecks, disputeStatus, reminderDraft, sourceReferences, missingData`. Choose appropriate live-schema types for these fields; each list item includes its relevant source identity. Persist step 3, the domain decision boundary, missing-data behavior and the following case-specific rule into the actual `systemPrompt`: “Never send a demand for an already-paid or actively disputed amount without review.” Map actual upstream/bound variables into `userPrompt`; a recipe link alone is insufficient.

**Connector candidates — unverified:** QuickBooks, Xero, Stripe, Gmail, Outlook. Discover actual toolkit names, read/action/trigger schemas and active accounts from MCP. Resolve every source/destination identifier. If public research is needed, use only a runtime tool actually available to the Agent; a host's browser access does not imply recurring runtime access.

**Permission and unattended behavior:** resolve only the capabilities and tool allowlists this graph needs. Keep preparation tools read-only. An Agent with `runtime.connectorPermission:"ask"` may pause on connector access; report it. Set `allow` only for an already authorized appropriately restricted toolset. Required business approvals still apply; no recipe-level text replaces a saved approval/policy node.

## Representative sample and verification

- **Sample input:** An invoice is 12 days late but a recent payment may still be unallocated.
- **Expected result:** Hold the reminder for review until allocation is resolved; for a clear unpaid case inspect the approved send result.
- **Negative or missing-data case:** Never send a demand for an already-paid or actively disputed amount without review.
- **Inspect:** source-to-output identity/field mapping, actual calculated values, required result fields, missing-data flags, and the final output/tool-result references. No records in scope must produce an explicit empty result rather than fabricated activity.
- **Proof boundary:** structural validation proves graph shape; draft simulation uses real model spend but neutralizes writes and auto-approves review. Only an authorized real run with inspected results proves the promised artifact/actions. Trigger health is separate and must be checked after publication.

## Pattern evidence

- [Accounts receivable](https://zapier.com/automations/finance/accounts-receivable) — source ID `zap-ar`, vendor_guide; inspected as page text.
- [Finance automation](https://zapier.com/automations/finance) — source ID `zap-finance`, vendor_guide; inspected as page text.

These sources support the business pattern; this recipe's task plan and boundaries are an original authored adaptation. They do not establish popularity, measured demand, neonloops connector coverage, client loading, or successful execution. Preserve this evidence level when adapting the recipe.
