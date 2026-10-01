# Public review response queue

- **Recipe:** `commerce-05` · version `0.1.0` · Commerce
- **Trigger intent:** When a product or store review arrives.
- **Outcome:** Approved public response and internal case.
- **Runtime plan:** [B](../runtime-plans.md) with [the shared installation protocol](../installation.md).
- **Runtime skill:** optional. Essential task/input/output instructions are saved inline in Agent nodes.
- **Side effects:** `external_send`. The outcome describes the intended completed workflow, not a claim that it has run.
- **Status:** authored adaptation; connector/tool/event support unverified until runtime discovery; not live-tested across candidate apps.

## Inputs to resolve

- Review: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- order context: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- service policy: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- prior replies: resolve the actual authorized source, policy/version, or value; do not infer missing facts.
- Target workspace/project and selected source record/view/folder IDs, relevant fields and access scope.
- For a schedule: cadence, timezone, look-back/look-ahead window and record cap. For an app event: actual supported event and payload mapping.
- Exact output destination and filename or connected-app target; reviewer/authorized policy where the steps require one.
- A designated safe sample, permitted verification spend, and whether the user requested draft setup or activation.

Reuse facts already supplied. The candidates below are alternatives, not a requirement to connect every app. No matching trigger/action means a recoverable partial setup; offer a supported alternative for the user to choose, never substitute one silently.

## Ordered workflow and saved task

1. Resolve the actual trigger for “When a product or store review arrives” and a bounded source scope. Read the selected records and preserve their IDs, timestamps and links.
2. Deterministic preparation: Resolve the review identity and approved public destination; strip private order details.
3. Agent preparation: Understand complaint and draft a context-sensitive response. Produce `reviewConcern, publicDraft, privateCaseContext, actionReferences, sourceReferences, missingData`. Explain evidence for each conclusion and preserve uncertainty. This node prepares the result and performs no external write.
4. Decision boundary: Approve response; never expose private order details. Use plan B with the required human decision, or the already authorized bounded policy for routine internal writes. Configure exception handling and preserve the user’s actual authorization.
5. Deterministic output: Publish the reviewed public response, then create the authorized internal case with private context in its private fields.
6. Read actual result/action IDs and compare the sample criteria below. Return partial effects if one ordered action succeeds and another fails.

**Agent output contract:** `reviewConcern, publicDraft, privateCaseContext, actionReferences, sourceReferences, missingData`. Choose appropriate live-schema types for these fields; each list item includes its relevant source identity. Persist step 3, the domain decision boundary, missing-data behavior and the following case-specific rule into the actual `systemPrompt`: “Do not reveal private details, offer an unapproved refund or fabricate a review.” Map actual upstream/bound variables into `userPrompt`; a recipe link alone is insufficient.

**Connector candidates — unverified:** Google Business Profile, Shopify, WooCommerce, Zendesk. Discover actual toolkit names, read/action/trigger schemas and active accounts from MCP. Resolve every source/destination identifier. If public research is needed, use only a runtime tool actually available to the Agent; a host's browser access does not imply recurring runtime access.

**Permission and unattended behavior:** resolve only the capabilities and tool allowlists this graph needs. Keep preparation tools read-only. An Agent with `runtime.connectorPermission:"ask"` may pause on connector access; report it. Set `allow` only for an already authorized appropriately restricted toolset. Required business approvals still apply; no recipe-level text replaces a saved approval/policy node.

## Representative sample and verification

- **Sample input:** A review complains about late delivery and linked order data contains a private address.
- **Expected result:** Publish only the approved public response without the address and create the scoped internal case.
- **Negative or missing-data case:** Do not reveal private details, offer an unapproved refund or fabricate a review.
- **Inspect:** source-to-output identity/field mapping, actual calculated values, required result fields, missing-data flags, and the final output/tool-result references. No records in scope must produce an explicit empty result rather than fabricated activity.
- **Proof boundary:** structural validation proves graph shape; draft simulation uses real model spend but neutralizes writes and auto-approves review. Only an authorized real run with inspected results proves the promised artifact/actions. Trigger health is separate and must be checked after publication.

## Evidence scope

The cited review template documents review analysis, a register and internal summaries. Public response publication is this recipe’s proposed extension, not a directly documented feature of that template. Resolve an actual public-reply action for the chosen review platform; if absent, offer a reply-draft variant for the user to choose rather than silently changing the output.

Google’s [official review reply documentation](https://developers.google.com/my-business/content/review-data) is supplemental primary evidence (`google-review-replies`) specifically for **Google location reviews**. It does not establish a WooCommerce/Shopify reply API or neonloops connector support. Treat Google Business Profile as an additional unverified candidate only for that source type.

## Pattern evidence

- [Analyze product reviews](https://n8n.io/workflows/12066-analyze-woocommerce-product-reviews-with-gpt-4-airtable-and-slack-summaries/) — source ID `n8n-reviews`, author_template; inspected as search excerpt.
- [Shopify Flow](https://www.shopify.com/flow) — source ID `shopify-flow`, official_product_guide; inspected as search excerpt.

These sources support the business pattern; this recipe's task plan and boundaries are an original authored adaptation. They do not establish popularity, measured demand, neonloops connector coverage, client loading, or successful execution. Preserve this evidence level when adapting the recipe.
