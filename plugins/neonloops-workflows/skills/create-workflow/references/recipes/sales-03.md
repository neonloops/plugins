# Meeting preparation brief

- **Recipe:** `sales-03` · version `0.1.0` · Sales
- **Trigger intent:** Before each customer meeting.
- **Outcome:** Private meeting brief with next steps.
- **Runtime plan:** [A](../runtime-plans.md) with [the shared installation protocol](../installation.md).
- **Runtime skill:** optional. Essential task/input/output instructions are saved inline in Agent nodes.
- **Side effects:** `artifact_only`. The outcome describes the intended completed workflow, not a claim that it has run.
- **Status:** authored adaptation; connector/tool/event support unverified until runtime discovery; not live-tested across candidate apps.

## Inputs to resolve

- Calendar: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- CRM history: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- prior emails: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- open issues: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- Target workspace/project and selected source record/view/folder IDs, relevant fields and access scope.
- For a schedule: cadence, timezone, look-back/look-ahead window and record cap. For an app event: actual supported event and payload mapping.
- Exact output destination and filename or connected-app target; reviewer/authorized policy where the steps require one.
- A designated safe sample, permitted verification spend, and whether the user requested draft setup or activation.

Reuse facts already supplied. The candidates below are alternatives, not a requirement to connect every app. No matching trigger/action means a recoverable partial setup; offer a supported alternative for the user to choose, never substitute one silently.

## Ordered workflow and saved task

1. Resolve the actual trigger for “Before each customer meeting” and a bounded source scope. Read the selected records and preserve their IDs, timestamps and links.
2. Deterministic preparation: Select the actual upcoming meeting and authorized attendees; calculate the agreed preparation window.
3. Agent preparation: Reconcile recent commitments and identify meeting questions. Produce `meetingContext, commitments, openIssues, questions, sourceReferences, missingData`. Explain evidence for each conclusion and preserve uncertainty. This node prepares the result and performs no external write.
4. Decision boundary: Keep customer context scoped to authorized attendees. This artifact is preparation for that decision; producing it does not approve a later business action.
5. Deterministic output: Save the mapped structured result as a private neonloops artifact through End; do not write to connected business apps.
6. Read actual result/action IDs and compare the sample criteria below. Return partial effects if one ordered action succeeds and another fails.

**Agent output contract:** `meetingContext, commitments, openIssues, questions, sourceReferences, missingData`. Choose appropriate live-schema types for these fields; each list item includes its relevant source identity. Persist step 3, the domain decision boundary, missing-data behavior and the following case-specific rule into the actual `systemPrompt`: “A private thread outside the permitted attendee context must be excluded.” Map actual upstream/bound variables into `userPrompt`; a recipe link alone is insufficient.

**Connector candidates — unverified:** Google Calendar, Outlook, HubSpot, Salesforce, Gmail. Discover actual toolkit names, read/action/trigger schemas and active accounts from MCP. Resolve every source/destination identifier. If public research is needed, use only a runtime tool actually available to the Agent; a host's browser access does not imply recurring runtime access.

**Permission and unattended behavior:** resolve only the capabilities and tool allowlists this graph needs. Keep preparation tools read-only. An Agent with `runtime.connectorPermission:"ask"` may pause on connector access; report it. Set `allow` only for an already authorized appropriately restricted toolset. Required business approvals still apply; no recipe-level text replaces a saved approval/policy node.

## Required scope and result checks

Bind to one actual meeting ID and timezone; include attendee/account context, unresolved commitments and questions, each linked to the relevant record.

Boundary check: Canceled/rescheduled meeting and ambiguous attendee-to-account match cannot produce a confident stale brief. Missing history is shown explicitly.

## Representative sample and verification

- **Sample input:** Tomorrow's account meeting has an overdue implementation promise and an unresolved support case.
- **Expected result:** The brief surfaces both commitments and proposes a question for each without emailing participants.
- **Negative or missing-data case:** A private thread outside the permitted attendee context must be excluded.
- **Inspect:** source-to-output identity/field mapping, actual calculated values, required result fields, missing-data flags, and the final output/tool-result references. No records in scope must produce an explicit empty result rather than fabricated activity.
- **Proof boundary:** structural validation proves graph shape; draft simulation uses real model spend but neutralizes writes and auto-approves review. Only an authorized real run with inspected results proves the promised artifact/actions. Trigger health is separate and must be checked after publication.

## Pattern evidence

- [Sales automation](https://www.make.com/en/solutions/automate-sales) — source ID `make-sales`, vendor_guide; inspected as search excerpt.
- [Streamline meetings with AI](https://zapier.com/blog/streamline-meetings-with-ai/) — source ID `zap-meetings`, vendor_guide; inspected as search excerpt.

These sources support the business pattern; this recipe's task plan and boundaries are an original authored adaptation. They do not establish popularity, measured demand, neonloops connector coverage, client loading, or successful execution. Preserve this evidence level when adapting the recipe.
