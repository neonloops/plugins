# Document intake and metadata register

- **Recipe:** `documents-01` · version `0.1.0` · Documents and contracts
- **Trigger intent:** When a business document enters an approved folder.
- **Outcome:** Document metadata record with extraction evidence and possible duplicates.
- **Runtime plan:** [B](../runtime-plans.md) with [the shared installation protocol](../installation.md).
- **Runtime skill:** optional. Essential task/input/output instructions are saved inline in Agent nodes.
- **Side effects:** `external_write`. The outcome describes the intended completed workflow, not a claim that it has run.
- **Status:** authored adaptation; connector/tool/event support unverified until runtime discovery; not live-tested across candidate apps.

## Inputs to resolve

- Document: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- taxonomy: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- record schema: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- related records: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- Target workspace/project and selected source record/view/folder IDs, relevant fields and access scope.
- For a schedule: cadence, timezone, look-back/look-ahead window and record cap. For an app event: actual supported event and payload mapping.
- Exact output destination and filename or connected-app target; reviewer/authorized policy where the steps require one.
- A designated safe sample, permitted verification spend, and whether the user requested draft setup or activation.

Reuse facts already supplied. The candidates below are alternatives, not a requirement to connect every app. No matching trigger/action means a recoverable partial setup; offer a supported alternative for the user to choose, never substitute one silently.

The research pattern also names a searchable index. This recipe deliberately implements a metadata register only. If the requested outcome includes search indexing, report `needs index` and require an externally prepared index; do not silently claim this artifact/register satisfies search.

## Ordered workflow and saved task

1. Resolve the actual trigger for “When a business document enters an approved folder” and a bounded source scope. Read the selected records and preserve their IDs, timestamps and links.
2. Deterministic preparation: Compare exact document identities/hashes where available and validate required metadata fields.
3. Agent preparation: Classify purpose, extract useful metadata and identify duplicates. Produce `documentId, extractedMetadata, classification, duplicateCandidates, sourceReferences, missingData`. Explain evidence for each conclusion and preserve uncertainty. This node prepares the result and performs no external write.
4. Decision boundary: No deletion; owner approves ambiguous classifications. Use plan B with the required human decision, or the already authorized bounded policy for routine internal writes. Configure exception handling and preserve the user’s actual authorization.
5. Deterministic output: Create or update the reviewed document metadata record in the selected business register; this does not create or refresh a knowledge index.
6. Read actual result/action IDs and compare the sample criteria below. Return partial effects if one ordered action succeeds and another fails.

**Agent output contract:** `documentId, extractedMetadata, classification, duplicateCandidates, sourceReferences, missingData`. Choose appropriate live-schema types for these fields; each list item includes its relevant source identity. Persist step 3, the domain decision boundary, missing-data behavior and the following case-specific rule into the actual `systemPrompt`: “Do not delete the old file or claim a search index was created.” Map actual upstream/bound variables into `userPrompt`; a recipe link alone is insufficient.

**Connector candidates — unverified:** Google Drive, SharePoint, Dropbox, Airtable. Discover actual toolkit names, read/action/trigger schemas and active accounts from MCP. Resolve every source/destination identifier. If public research is needed, use only a runtime tool actually available to the Agent; a host's browser access does not imply recurring runtime access.

**Permission and unattended behavior:** resolve only the capabilities and tool allowlists this graph needs. Keep preparation tools read-only. An Agent with `runtime.connectorPermission:"ask"` may pause on connector access; report it. Set `allow` only for an already authorized appropriately restricted toolset. Required business approvals still apply; no recipe-level text replaces a saved approval/policy node.

## Representative sample and verification

- **Sample input:** An approved folder receives a document matching an existing title but with a newer date.
- **Expected result:** Create the reviewed metadata record, preserve both source references and flag possible duplication.
- **Negative or missing-data case:** Do not delete the old file or claim a search index was created.
- **Inspect:** source-to-output identity/field mapping, actual calculated values, required result fields, missing-data flags, and the final output/tool-result references. No records in scope must produce an explicit empty result rather than fabricated activity.
- **Proof boundary:** structural validation proves graph shape; draft simulation uses real model spend but neutralizes writes and auto-approves review. Only an authorized real run with inspected results proves the promised artifact/actions. Trigger health is separate and must be checked after publication.

## Pattern evidence

- [Document-control automation](https://www.zapier.com/blog/4-ways-to-improve-document-control-with-automation/) — source ID `zap-document`, vendor_guide; inspected as search excerpt.
- [Four finance customer stories](https://www.make.com/en/blog/success-stories-make-it-in-finance) — source ID `make-finance-cases`, vendor_case_studies; inspected as page text.
- [Contract documentation management](https://zapier.com/automations/legal/contract-management/contract-documentation-management) — source ID `zap-contracts`, vendor_guide; inspected as search excerpt.

These sources support the business pattern; this recipe's task plan and boundaries are an original authored adaptation. They do not establish popularity, measured demand, neonloops connector coverage, client loading, or successful execution. Preserve this evidence level when adapting the recipe.
