# Signature completion and record closure

- **Recipe:** `documents-04` · version `0.1.0` · Documents and contracts
- **Trigger intent:** When an agreement is signed or expires unsigned.
- **Outcome:** Executed agreement register and follow-up tasks.
- **Runtime plan:** [B](../runtime-plans.md) with [the shared installation protocol](../installation.md).
- **Runtime skill:** optional. Essential task/input/output instructions are saved inline in Agent nodes.
- **Side effects:** `external_write`. The outcome describes the intended completed workflow, not a claim that it has run.
- **Status:** authored adaptation; connector/tool/event support unverified until runtime discovery; not live-tested across candidate apps.

## Inputs to resolve

- Envelope status: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- agreement: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- parties: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- CRM record: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- Target workspace/project and selected source record/view/folder IDs, relevant fields and access scope.
- For a schedule: cadence, timezone, look-back/look-ahead window and record cap. For an app event: actual supported event and payload mapping.
- Exact output destination and filename or connected-app target; reviewer/authorized policy where the steps require one.
- A designated safe sample, permitted verification spend, and whether the user requested draft setup or activation.

Reuse facts already supplied. The candidates below are alternatives, not a requirement to connect every app. No matching trigger/action means a recoverable partial setup; offer a supported alternative for the user to choose, never substitute one silently.

## Ordered workflow and saved task

1. Resolve the actual trigger for “When an agreement is signed or expires unsigned” and a bounded source scope. Read the selected records and preserve their IDs, timestamps and links.
2. Deterministic preparation: Match actual signature status and document identity to the requested agreement.
3. Agent preparation: Reconcile executed document with requested terms and missing files. Produce `envelopeStatus, agreementReferences, registerFields, followupTasks, sourceReferences, missingData`. Explain evidence for each conclusion and preserve uncertainty. This node prepares the result and performs no external write.
4. Decision boundary: No signature, terms change or inferred legal validity. Use plan B with the required human decision, or the already authorized bounded policy for routine internal writes. Configure exception handling and preserve the user’s actual authorization.
5. Deterministic output: Write the observed agreement status/references into the authorized register, then create required follow-up tasks.
6. Read actual result/action IDs and compare the sample criteria below. Return partial effects if one ordered action succeeds and another fails.

**Agent output contract:** `envelopeStatus, agreementReferences, registerFields, followupTasks, sourceReferences, missingData`. Choose appropriate live-schema types for these fields; each list item includes its relevant source identity. Persist step 3, the domain decision boundary, missing-data behavior and the following case-specific rule into the actual `systemPrompt`: “Do not infer signature validity, sign anything or alter terms.” Map actual upstream/bound variables into `userPrompt`; a recipe link alone is insufficient.

**Connector candidates — unverified:** DocuSign, Google Drive, SharePoint, HubSpot. Discover actual toolkit names, read/action/trigger schemas and active accounts from MCP. Resolve every source/destination identifier. If public research is needed, use only a runtime tool actually available to the Agent; a host's browser access does not imply recurring runtime access.

**Permission and unattended behavior:** resolve only the capabilities and tool allowlists this graph needs. Keep preparation tools read-only. An Agent with `runtime.connectorPermission:"ask"` may pause on connector access; report it. Set `allow` only for an already authorized appropriately restricted toolset. Required business approvals still apply; no recipe-level text replaces a saved approval/policy node.

## Representative sample and verification

- **Sample input:** An envelope is completed but the expected final document is inaccessible.
- **Expected result:** Record the observed status and create a missing-document follow-up, without claiming file closure.
- **Negative or missing-data case:** Do not infer signature validity, sign anything or alter terms.
- **Inspect:** source-to-output identity/field mapping, actual calculated values, required result fields, missing-data flags, and the final output/tool-result references. No records in scope must produce an explicit empty result rather than fabricated activity.
- **Proof boundary:** structural validation proves graph shape; draft simulation uses real model spend but neutralizes writes and auto-approves review. Only an authorized real run with inspected results proves the promised artifact/actions. Trigger health is separate and must be checked after publication.

## Pattern evidence

- [Contract documentation management](https://zapier.com/automations/legal/contract-management/contract-documentation-management) — source ID `zap-contracts`, vendor_guide; inspected as search excerpt.
- [Contract draft and signature workflow](https://n8n.io/workflows/11849-generate-ai-powered-contracts-with-openai-e-signature-gmail-and-sheets/) — source ID `n8n-contract-draft`, author_template; inspected as search excerpt.

These sources support the business pattern; this recipe's task plan and boundaries are an original authored adaptation. They do not establish popularity, measured demand, neonloops connector coverage, client loading, or successful execution. Preserve this evidence level when adapting the recipe.
