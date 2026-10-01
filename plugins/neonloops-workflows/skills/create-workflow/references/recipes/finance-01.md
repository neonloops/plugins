# Invoice intake and review packet

- **Recipe:** `finance-01` · version `0.1.0` · Finance and procurement
- **Trigger intent:** When an invoice document arrives.
- **Outcome:** Structured invoice draft and approval packet.
- **Runtime plan:** [A](../runtime-plans.md) with [the shared installation protocol](../installation.md).
- **Runtime skill:** optional. Essential task/input/output instructions are saved inline in Agent nodes.
- **Side effects:** `artifact_only`. The outcome describes the intended completed workflow, not a claim that it has run.
- **Status:** authored adaptation; connector/tool/event support unverified until runtime discovery; not live-tested across candidate apps.

## Inputs to resolve

- Invoice: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- vendor record: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- purchase order: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- policy: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- Target workspace/project and selected source record/view/folder IDs, relevant fields and access scope.
- For a schedule: cadence, timezone, look-back/look-ahead window and record cap. For an app event: actual supported event and payload mapping.
- Exact output destination and filename or connected-app target; reviewer/authorized policy where the steps require one.
- A designated safe sample, permitted verification spend, and whether the user requested draft setup or activation.

Reuse facts already supplied. The candidates below are alternatives, not a requirement to connect every app. No matching trigger/action means a recoverable partial setup; offer a supported alternative for the user to choose, never substitute one silently.

## Ordered workflow and saved task

1. Resolve the actual invoice-arrival trigger and authorized document/vendor/purchase-order sources. Preserve document identity, version and page/span references.
2. Extraction Agent: read the raw invoice and return invoice/vendor IDs, dates, currency, each line's quantity/unit price/amount, tax, stated total and source spans. Mark unreadable or ambiguous fields; do not calculate authoritative totals or infer tax rules.
3. Deterministic calculation: map the extracted numeric fields into Transform/Set expressions. Apply the supplied currency, rounding and tax policy to calculate line totals and compare the calculated total with the stated total. Ambiguous currency, unreadable numbers or missing rounding policy remain review exceptions. Only explicitly verified pre-extracted input may skip step 2.
4. Explanatory Agent: consume the actual extraction and calculation outputs plus verified vendor/purchase-order data. Return `invoiceFields, purchaseOrderComparison, discrepancies, approvalPacket, sourceReferences, missingData`; explain each discrepancy with the exact computed amount and source location. It cannot replace a calculation with model arithmetic.
5. Accountant review owns tax treatment, posting and payment. Save the mapped review packet as a private neonloops artifact through End; this workflow performs no posting or payment.
6. Inspect the extraction evidence, deterministic expression result and final artifact fields. With source lines 60 and 40, no tax, and stated total 110, the calculated total must be 100 and the discrepancy exactly 10 in the stated currency. Inspect artifact evidence only after an authorized real run; simulation cannot prove storage.

**Agent output contract:** `invoiceFields, purchaseOrderComparison, discrepancies, approvalPacket, sourceReferences, missingData`. Choose appropriate live-schema types for these fields; each list item includes its relevant source identity. Persist the extraction and explanation tasks in their respective Agent nodes, plus the domain decision boundary, missing-data behavior and the following case-specific rule into the actual `systemPrompt`: “Do not post the invoice, choose a tax treatment or initiate payment.” Map actual upstream/bound variables into `userPrompt`; a recipe link alone is insufficient.

**Connector candidates — unverified:** Gmail, Outlook, Google Drive, QuickBooks, Xero. Discover actual toolkit names, read/action/trigger schemas and active accounts from MCP. Resolve every source/destination identifier. If public research is needed, use only a runtime tool actually available to the Agent; a host's browser access does not imply recurring runtime access.

**Permission and unattended behavior:** resolve only the capabilities and tool allowlists this graph needs. Keep preparation tools read-only. An Agent with `runtime.connectorPermission:"ask"` may pause on connector access; report it. Set `allow` only for an already authorized appropriately restricted toolset. Required business approvals still apply; no recipe-level text replaces a saved approval/policy node.

## Required scope and result checks

Extract vendor/invoice ID/date/due date/currency/lines/tax/total with page evidence; deterministic arithmetic checks use the supplied rounding rules; match PO/vendor IDs and show discrepancies.

Boundary check: Duplicate invoice candidate is flagged; ambiguous currency, unreadable field or totals mismatch leaves a review exception. Never infer a tax rule or mark paid/post to ledger.

## Representative sample and verification

- **Sample input:** A source invoice shows lines of 60 and 40, no tax, and a stated total of 110 in one known currency.
- **Expected result:** The deterministic node returns total 100 and discrepancy 10; the explanatory packet cites the source spans, computed result and purchase-order reference.
- **Negative or missing-data case:** Do not post the invoice, choose a tax treatment or initiate payment.
- **Inspect:** source-to-output identity/field mapping, actual calculated values, required result fields, missing-data flags, and the final output/tool-result references. No records in scope must produce an explicit empty result rather than fabricated activity.
- **Proof boundary:** structural validation proves graph shape; draft simulation uses real model spend but neutralizes writes and auto-approves review. Only an authorized real run with inspected results proves the promised artifact/actions. Trigger health is separate and must be checked after publication.

## Pattern evidence

- [Document extraction and approval guided project](https://learn.microsoft.com/en-us/training/modules/guided-project-document-process-model-email-approval-ai-builder/) — source ID `ms-invoice`, official_documentation; inspected as search excerpt.
- [Four finance customer stories](https://www.make.com/en/blog/success-stories-make-it-in-finance) — source ID `make-finance-cases`, vendor_case_studies; inspected as page text.
- [Finance automation](https://zapier.com/automations/finance) — source ID `zap-finance`, vendor_guide; inspected as page text.

These sources support the business pattern; this recipe's task plan and boundaries are an original authored adaptation. They do not establish popularity, measured demand, neonloops connector coverage, client loading, or successful execution. Preserve this evidence level when adapting the recipe.
