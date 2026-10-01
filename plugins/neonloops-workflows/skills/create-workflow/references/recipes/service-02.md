# Knowledge-grounded reply preparation

- **Recipe:** `service-02` · version `0.1.0` · Customer service
- **Trigger intent:** When a ticket awaits a response.
- **Outcome:** Draft reply with evidence and escalation reason.
- **Runtime plan:** [A](../runtime-plans.md) with [the shared installation protocol](../installation.md).
- **Runtime skill:** optional. Essential task/input/output instructions are saved inline in Agent nodes.
- **Side effects:** `artifact_only`. The outcome describes the intended completed workflow, not a claim that it has run.
- **Status:** authored adaptation; connector/tool/event support unverified until runtime discovery; not live-tested across candidate apps.

## Inputs to resolve

- Ticket: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- knowledge base: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- account and order context: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- Target workspace/project and selected source record/view/folder IDs, relevant fields and access scope.
- For a schedule: cadence, timezone, look-back/look-ahead window and record cap. For an app event: actual supported event and payload mapping.
- Exact output destination and filename or connected-app target; reviewer/authorized policy where the steps require one.
- A designated safe sample, permitted verification spend, and whether the user requested draft setup or activation.

Reuse facts already supplied. The candidates below are alternatives, not a requirement to connect every app. No matching trigger/action means a recoverable partial setup; offer a supported alternative for the user to choose, never substitute one silently.

Knowledge prerequisite: use approved bounded document/table/Drive reads, or an already prepared index with known source IDs. MCP cannot provision or verify a fresh index; report that prerequisite before claiming grounded retrieval.

## Ordered workflow and saved task

1. Resolve the actual trigger for “When a ticket awaits a response” and a bounded source scope. Read the selected records and preserve their IDs, timestamps and links.
2. Deterministic preparation: Select the approved policy version and relevant account/order records within access scope.
3. Agent preparation: Retrieve applicable guidance and prepare cited response. Produce `draftReply, policyCitations, escalationReason, missingContext, sourceReferences, missingData`. Explain evidence for each conclusion and preserve uncertainty. This node prepares the result and performs no external write.
4. Decision boundary: Never invent policy; agent cannot commit remedies. This artifact is preparation for that decision; producing it does not approve a later business action.
5. Deterministic output: Save the mapped structured result as a private neonloops artifact through End; do not write to connected business apps.
6. Read actual result/action IDs and compare the sample criteria below. Return partial effects if one ordered action succeeds and another fails.

**Agent output contract:** `draftReply, policyCitations, escalationReason, missingContext, sourceReferences, missingData`. Choose appropriate live-schema types for these fields; each list item includes its relevant source identity. Persist step 3, the domain decision boundary, missing-data behavior and the following case-specific rule into the actual `systemPrompt`: “An unavailable index or missing policy cannot become an invented remedy.” Map actual upstream/bound variables into `userPrompt`; a recipe link alone is insufficient.

**Connector candidates — unverified:** Zendesk, Intercom, Notion, Confluence, Shopify. Discover actual toolkit names, read/action/trigger schemas and active accounts from MCP. Resolve every source/destination identifier. If public research is needed, use only a runtime tool actually available to the Agent; a host's browser access does not imply recurring runtime access.

**Permission and unattended behavior:** resolve only the capabilities and tool allowlists this graph needs. Keep preparation tools read-only. An Agent with `runtime.connectorPermission:"ask"` may pause on connector access; report it. Set `allow` only for an already authorized appropriately restricted toolset. Required business approvals still apply; no recipe-level text replaces a saved approval/policy node.

## Required scope and result checks

Answer the actual ticket using applicable article/policy passages; include source/version and unresolved case facts; specify the concrete escalation reason where needed.

Boundary check: Contradictory or outdated policy and insufficient account evidence yield a limited draft or escalation, not a promise of refund/remedy. No customer cross-contamination.

## Representative sample and verification

- **Sample input:** A refund question concerns an order outside the documented return window.
- **Expected result:** Draft the supported policy explanation and escalate any exception; cite the actual clause.
- **Negative or missing-data case:** An unavailable index or missing policy cannot become an invented remedy.
- **Inspect:** source-to-output identity/field mapping, actual calculated values, required result fields, missing-data flags, and the final output/tool-result references. No records in scope must produce an explicit empty result rather than fabricated activity.
- **Proof boundary:** structural validation proves graph shape; draft simulation uses real model spend but neutralizes writes and auto-approves review. Only an authorized real run with inspected results proves the promised artifact/actions. Trigger health is separate and must be checked after publication.

## Pattern evidence

- [Knowledge-grounded IT support](https://n8n.io/workflows/3498-build-an-it-support-assistant-chatbot-leveraging-existing-support-portal/) — source ID `n8n-it-help`, author_template; inspected as search excerpt.
- [Triage and route support tickets](https://n8n.io/workflows/19465-triage-and-route-ai-powered-support-tickets-with-google-gemini-trello-and-gmail/) — source ID `n8n-triage`, author_template; inspected as search excerpt.

These sources support the business pattern; this recipe's task plan and boundaries are an original authored adaptation. They do not establish popularity, measured demand, neonloops connector coverage, client loading, or successful execution. Preserve this evidence level when adapting the recipe.
