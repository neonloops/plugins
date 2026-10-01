# Bug intake and duplicate review

- **Recipe:** `product-02` · version `0.1.0` · Product and IT
- **Trigger intent:** When a structured bug report arrives.
- **Outcome:** New issue or linked duplicate with supporting context.
- **Runtime plan:** [B](../runtime-plans.md) with [the shared installation protocol](../installation.md).
- **Runtime skill:** optional. Essential task/input/output instructions are saved inline in Agent nodes.
- **Side effects:** `external_write`. The outcome describes the intended completed workflow, not a claim that it has run.
- **Status:** authored adaptation; connector/tool/event support unverified until runtime discovery; not live-tested across candidate apps.

## Inputs to resolve

- Report: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- reproduction details: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- existing issues: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- Target workspace/project and selected source record/view/folder IDs, relevant fields and access scope.
- For a schedule: cadence, timezone, look-back/look-ahead window and record cap. For an app event: actual supported event and payload mapping.
- Exact output destination and filename or connected-app target; reviewer/authorized policy where the steps require one.
- A designated safe sample, permitted verification spend, and whether the user requested draft setup or activation.

Reuse facts already supplied. The candidates below are alternatives, not a requirement to connect every app. No matching trigger/action means a recoverable partial setup; offer a supported alternative for the user to choose, never substitute one silently.

## Ordered workflow and saved task

1. Resolve the actual trigger for “When a structured bug report arrives” and a bounded source scope. Read the selected records and preserve their IDs, timestamps and links.
2. Deterministic preparation: Compare exact issue IDs and reproduction/environment facts before linking duplicates.
3. Agent preparation: Compare symptoms and identify missing reproducibility evidence. Produce `reproductionFacts, duplicateEvidence, issuePayload, missingSteps, sourceReferences, missingData`. Explain evidence for each conclusion and preserve uncertainty. This node prepares the result and performs no external write.
4. Decision boundary: No automatic code changes, merges or deployment. Use plan B with the required human decision, or the already authorized bounded policy for routine internal writes. Configure exception handling and preserve the user’s actual authorization.
5. Deterministic output: Create the authorized issue, or link a verified duplicate according to the agreed decision; do not close or delete issues implicitly.
6. Read actual result/action IDs and compare the sample criteria below. Return partial effects if one ordered action succeeds and another fails.

**Agent output contract:** `reproductionFacts, duplicateEvidence, issuePayload, missingSteps, sourceReferences, missingData`. Choose appropriate live-schema types for these fields; each list item includes its relevant source identity. Persist step 3, the domain decision boundary, missing-data behavior and the following case-specific rule into the actual `systemPrompt`: “Do not close an issue as duplicate from title similarity alone or change code.” Map actual upstream/bound variables into `userPrompt`; a recipe link alone is insufficient.

**Connector candidates — unverified:** Jotform, GitHub, Jira, Linear. Discover actual toolkit names, read/action/trigger schemas and active accounts from MCP. Resolve every source/destination identifier. If public research is needed, use only a runtime tool actually available to the Agent; a host's browser access does not imply recurring runtime access.

**Permission and unattended behavior:** resolve only the capabilities and tool allowlists this graph needs. Keep preparation tools read-only. An Agent with `runtime.connectorPermission:"ask"` may pause on connector access; report it. Set `allow` only for an already authorized appropriately restricted toolset. Required business approvals still apply; no recipe-level text replaces a saved approval/policy node.

## Representative sample and verification

- **Sample input:** A report resembles an open issue but occurs in a different environment.
- **Expected result:** Create the authorized issue or reviewable link with the environment distinction intact.
- **Negative or missing-data case:** Do not close an issue as duplicate from title similarity alone or change code.
- **Inspect:** source-to-output identity/field mapping, actual calculated values, required result fields, missing-data flags, and the final output/tool-result references. No records in scope must produce an explicit empty result rather than fabricated activity.
- **Proof boundary:** structural validation proves graph shape; draft simulation uses real model spend but neutralizes writes and auto-approves review. Only an authorized real run with inspected results proves the promised artifact/actions. Trigger health is separate and must be checked after publication.

## Pattern evidence

- [Bug report intake and deduplication](https://n8n.io/workflows/9655-automate-bug-reports-with-gemini-ai-jotform-to-github-with-telegram-alerts/) — source ID `n8n-bugs`, author_template; inspected as search excerpt.
- [Jira automation template library](https://www.atlassian.com/software/jira/automation-template-library) — source ID `atlassian-templates`, official_template_library; inspected as search excerpt.

These sources support the business pattern; this recipe's task plan and boundaries are an original authored adaptation. They do not establish popularity, measured demand, neonloops connector coverage, client loading, or successful execution. Preserve this evidence level when adapting the recipe.
