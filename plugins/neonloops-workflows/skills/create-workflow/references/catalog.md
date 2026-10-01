# Workflow catalog

67 authored recipes across 9 business domains. Count distinct recurring outcomes, not app pairs. Sources document patterns, not popularity or measured customer demand. Every connector candidate is unverified until the connected workspace’s live catalog confirms its tools/events.

Read only a selected recipe plus the shared installation protocol. If no recipe fits exactly, adapt or compose one with the same protocol and label it custom/unverified. Do not quietly replace the requested output with an artifact or claim a custom composition has been tested.

All recipes support inline Agent instructions; workspace skill creation is optional. “Artifact” means a private neonloops result file. “Write” changes a business app; “send” delivers customer/public content. The recipe names the required human decision or authorized policy. The catalog describes intended outcomes, not completed runs.

| Domain                                              | Recipes | Typical requests                                                     |
| --------------------------------------------------- | ------: | -------------------------------------------------------------------- |
| [Sales](#sales)                                     |      10 | lead briefs, meeting preparation, pipeline exceptions, handoffs      |
| [Marketing](#marketing)                             |       9 | research, content briefs, campaign commentary, approved distribution |
| [Customer service](#customer-service)               |      10 | triage, grounded replies, escalations, onboarding, renewals          |
| [Finance and procurement](#finance-and-procurement) |      10 | invoice review, reconciliation, close, supplier comparisons          |
| [People operations](#people-operations)             |       8 | factual intake, interview logistics, onboarding and handoff tasks    |
| [Team operations](#team-operations)                 |       7 | agenda, meeting actions, status reports, KPI exceptions              |
| [Documents and contracts](#documents-and-contracts) |       4 | metadata registers, contract review packets, signature records       |
| [Product and IT](#product-and-it)                   |       3 | feedback synthesis, bug intake, incident write-ups                   |
| [Commerce](#commerce)                               |       6 | stock exceptions, fulfillment, listings, review responses            |

## Choose between related outcomes

If two recipes would own the same object and result, extend the existing installation instead of creating a duplicate. Ask about the business objective only if it remains ambiguous. Naming/markers are not concurrency-safe uniqueness.

| Family               | Related recipes                                                                                                         | Selection boundary                                                                                                                                                    |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| meeting-followup     | [sales-04](recipes/sales-04.md), [operations-03](recipes/operations-03.md)                                              | Sales follow-up owns a prospect email plus CRM commitments; meeting actions own internal minutes/tasks.                                                               |
| customer-delivery    | [sales-10](recipes/sales-10.md), [service-06](recipes/service-06.md)                                                    | Sales handoff transfers signed promises to delivery; onboarding coordinates customer milestones after ownership is accepted.                                          |
| content-distribution | [marketing-05](recipes/marketing-05.md), [marketing-09](recipes/marketing-09.md)                                        | Repurposing adapts an approved source asset; launch preparation owns release facts, audience approvals and publishing tasks.                                          |
| inquiry-triage       | [service-01](recipes/service-01.md), [operations-02](recipes/operations-02.md)                                          | Support triage changes ticket routing under policy; shared-inbox triage produces a private draft queue without mailbox changes.                                       |
| periodic-metrics     | [marketing-06](recipes/marketing-06.md), [finance-07](recipes/finance-07.md), [operations-07](recipes/operations-07.md) | Campaign narrative uses attribution/KPI definitions; budget watch uses approved spend thresholds; operational exceptions use service/process metrics and owner rules. |
| policy-response      | [service-02](recipes/service-02.md), [people-08](recipes/people-08.md)                                                  | Support reply preparation applies customer/service policy; employee questions apply HR policy with individual rights and benefits escalated to HR.                    |

## Sales

| Recipe                                                                            | Trigger                                                         | Result                                           | Effects  |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------ | -------- |
| [sales-01 · Inbound lead qualification and proposed routing](recipes/sales-01.md) | When a new inquiry arrives                                      | Qualified lead brief and proposed owner          | artifact |
| [sales-02 · Account research refresh](recipes/sales-02.md)                        | When a target account is added or material news appears         | Dated account dossier with source links          | artifact |
| [sales-03 · Meeting preparation brief](recipes/sales-03.md)                       | Before each customer meeting                                    | Private meeting brief with next steps            | artifact |
| [sales-04 · Sales call follow-up package](recipes/sales-04.md)                    | When a sales transcript is ready                                | Approved follow-up email and logged CRM note     | send     |
| [sales-05 · Stalled-deal intervention](recipes/sales-05.md)                       | Every weekday for inactive open deals                           | Owner task with supporting deal evidence         | write    |
| [sales-06 · Pipeline and forecast commentary](recipes/sales-06.md)                | Every week before forecast review                               | Pipeline report with risk and data-gap sections  | artifact |
| [sales-07 · CRM quality repair proposals](recipes/sales-07.md)                    | Every week or after a bulk import                               | Review queue with proposed field changes         | artifact |
| [sales-08 · Quote and proposal preparation](recipes/sales-08.md)                  | When a qualified opportunity requests a quote                   | Draft proposal and quote for commercial approval | artifact |
| [sales-09 · Buying-signal follow-up queue](recipes/sales-09.md)                   | When product, website or account signals cross configured rules | Prioritized outreach task with source events     | write    |
| [sales-10 · Sales-to-delivery handoff](recipes/sales-10.md)                       | When a deal is marked won                                       | Delivery project and handoff brief               | write    |

## Marketing

| Recipe                                                                         | Trigger                                             | Result                                                | Effects  |
| ------------------------------------------------------------------------------ | --------------------------------------------------- | ----------------------------------------------------- | -------- |
| [marketing-01 · Competitive-change briefing](recipes/marketing-01.md)          | Every week or when watched pages change             | Competitive update with implications and sources      | artifact |
| [marketing-02 · SEO performance and repair brief](recipes/marketing-02.md)     | Every week                                          | SEO priorities with affected URLs and data            | artifact |
| [marketing-03 · Content opportunity and brief queue](recipes/marketing-03.md)  | Every planning cycle                                | Ranked content briefs in editorial backlog            | write    |
| [marketing-04 · Long-form content draft](recipes/marketing-04.md)              | When an approved brief is ready                     | Reviewable article in draft storage                   | artifact |
| [marketing-05 · Content repurposing and distribution](recipes/marketing-05.md) | When a source asset is approved                     | Approved scheduled channel posts                      | send     |
| [marketing-06 · Campaign performance narrative](recipes/marketing-06.md)       | Every week and at campaign close                    | Campaign report with uncertainty and next experiments | artifact |
| [marketing-07 · Lead nurture and re-engagement](recipes/marketing-07.md)       | When opted-in lead behavior meets campaign criteria | Approved lifecycle email sequence                     | send     |
| [marketing-08 · Brand and factual review queue](recipes/marketing-08.md)       | When a campaign draft is submitted                  | Annotated review report and revised draft             | artifact |
| [marketing-09 · Launch communications package](recipes/marketing-09.md)        | When a release or campaign is approved for launch   | Approved announcement drafts and publishing tasks     | write    |

## Customer service

| Recipe                                                                     | Trigger                                           | Result                                             | Effects  |
| -------------------------------------------------------------------------- | ------------------------------------------------- | -------------------------------------------------- | -------- |
| [service-01 · Support intake triage](recipes/service-01.md)                | When an inquiry arrives                           | Tagged ticket assigned to the correct queue        | write    |
| [service-02 · Knowledge-grounded reply preparation](recipes/service-02.md) | When a ticket awaits a response                   | Draft reply with evidence and escalation reason    | artifact |
| [service-03 · SLA and escalation watch](recipes/service-03.md)             | On a recurring check before service deadlines     | Escalation task or internal message                | write    |
| [service-04 · Support quality and trend review](recipes/service-04.md)     | Every week                                        | Quality report with ticket evidence                | artifact |
| [service-05 · Knowledge-base gap drafts](recipes/service-05.md)            | Every week or after repeated unanswered questions | Article proposals linked to source cases           | artifact |
| [service-06 · Customer onboarding coordination](recipes/service-06.md)     | When a new customer contract starts               | Customer project with personalized next-step tasks | write    |
| [service-07 · Onboarding stall recovery](recipes/service-07.md)            | Every weekday for incomplete milestones           | Owner intervention brief and outreach draft        | artifact |
| [service-08 · Renewal readiness brief](recipes/service-08.md)              | At configured intervals before customer renewal   | Renewal brief with questions and next actions      | artifact |
| [service-09 · Customer feedback follow-up](recipes/service-09.md)          | When post-support survey feedback arrives         | Approved follow-up email and owner task            | send     |
| [service-10 · Dispute case evidence pack](recipes/service-10.md)           | When a payment dispute or complaint opens         | Draft case evidence package                        | artifact |

## Finance and procurement

| Recipe                                                                 | Trigger                                         | Result                                                  | Effects  |
| ---------------------------------------------------------------------- | ----------------------------------------------- | ------------------------------------------------------- | -------- |
| [finance-01 · Invoice intake and review packet](recipes/finance-01.md) | When an invoice document arrives                | Structured invoice draft and approval packet            | artifact |
| [finance-02 · Expense review preparation](recipes/finance-02.md)       | When an employee submits expenses               | Expense-review packet with missing evidence             | artifact |
| [finance-03 · Reconciliation exception report](recipes/finance-03.md)  | On new statement or weekly close cycle          | Matched records and unresolved-exception report         | artifact |
| [finance-04 · Overdue receivable follow-up](recipes/finance-04.md)     | Every business day for overdue invoices         | Approved reminder email with case context               | send     |
| [finance-05 · Financial close readiness](recipes/finance-05.md)        | Before each monthly close deadline              | Close-readiness brief with evidence links               | artifact |
| [finance-06 · Management variance commentary](recipes/finance-06.md)   | After each reporting-period refresh             | Draft management commentary with calculation references | artifact |
| [finance-07 · Budget anomaly watch](recipes/finance-07.md)             | On scheduled spend refresh                      | Exception brief for budget owner                        | artifact |
| [finance-08 · Supplier quote comparison](recipes/finance-08.md)        | When quote deadline arrives                     | Supplier comparison matrix with caveats                 | artifact |
| [finance-09 · Purchase request review](recipes/finance-09.md)          | When a purchase request is submitted            | Purchase-review packet routed to approver               | write    |
| [finance-10 · Vendor renewal decision brief](recipes/finance-10.md)    | Before vendor cancellation or renewal deadlines | Renewal brief with keep, change or investigate options  | artifact |

## People operations

| Recipe                                                                        | Trigger                                     | Result                                                         | Effects  |
| ----------------------------------------------------------------------------- | ------------------------------------------- | -------------------------------------------------------------- | -------- |
| [people-01 · Hiring materials preparation](recipes/people-01.md)              | When an approved role opens                 | Job-description and interview-kit drafts                       | artifact |
| [people-02 · Candidate facts intake](recipes/people-02.md)                    | When an application arrives                 | Structured factual dossier and missing-document checklist      | artifact |
| [people-03 · Interview scheduling coordination](recipes/people-03.md)         | When a recruiter advances an applicant      | Approved interview invitations                                 | send     |
| [people-04 · Interview feedback completion and summary](recipes/people-04.md) | After an interview and at feedback deadline | Feedback-completeness brief and summary                        | artifact |
| [people-05 · New-hire onboarding coordination](recipes/people-05.md)          | When an accepted start date is recorded     | Assigned onboarding checklist                                  | write    |
| [people-06 · Departure handoff coordination](recipes/people-06.md)            | When HR authorizes an employee departure    | Assigned offboarding checklist with completion-evidence fields | write    |
| [people-07 · Leave-request approval routing](recipes/people-07.md)            | When an employee submits leave              | Approval packet and recorded approver decision                 | write    |
| [people-08 · Employee policy question drafts](recipes/people-08.md)           | When an employee submits a policy question  | Cited draft answer or HR escalation                            | artifact |

## Team operations

| Recipe                                                                            | Trigger                                | Result                                        | Effects  |
| --------------------------------------------------------------------------------- | -------------------------------------- | --------------------------------------------- | -------- |
| [operations-01 · Morning work briefing](recipes/operations-01.md)                 | Every workday morning                  | Private agenda and action brief               | artifact |
| [operations-02 · Shared inbox triage and draft queue](recipes/operations-02.md)   | When new shared-inbox mail arrives     | Prioritized message and reply-draft queue     | artifact |
| [operations-03 · Meeting decisions and action tracking](recipes/operations-03.md) | When a meeting transcript is available | Approved notes and assigned follow-up tasks   | write    |
| [operations-04 · Project intake scoping](recipes/operations-04.md)                | When a project request is submitted    | Draft project brief and work breakdown        | artifact |
| [operations-05 · Stakeholder project status report](recipes/operations-05.md)     | Every week before stakeholder review   | Status brief with source links                | artifact |
| [operations-06 · Overdue-work escalation](recipes/operations-06.md)               | Every day for work past due            | Escalation task or internal notification      | write    |
| [operations-07 · Operational KPI exception briefing](recipes/operations-07.md)    | On each scheduled dashboard refresh    | Exception report with investigation questions | artifact |

## Documents and contracts

| Recipe                                                                            | Trigger                                            | Result                                                                    | Effects  |
| --------------------------------------------------------------------------------- | -------------------------------------------------- | ------------------------------------------------------------------------- | -------- |
| [documents-01 · Document intake and metadata register](recipes/documents-01.md)   | When a business document enters an approved folder | Document metadata record with extraction evidence and possible duplicates | write    |
| [documents-02 · Contract clause review preparation](recipes/documents-02.md)      | When a contract draft is submitted                 | Reviewer packet of deviations and open questions                          | artifact |
| [documents-03 · Approved-template contract packet](recipes/documents-03.md)       | When a contract request is complete                | Draft contract packet for review                                          | artifact |
| [documents-04 · Signature completion and record closure](recipes/documents-04.md) | When an agreement is signed or expires unsigned    | Executed agreement register and follow-up tasks                           | write    |

## Product and IT

| Recipe                                                                | Trigger                              | Result                                                | Effects  |
| --------------------------------------------------------------------- | ------------------------------------ | ----------------------------------------------------- | -------- |
| [product-01 · Product feedback synthesis](recipes/product-01.md)      | Every product planning cycle         | Evidence-linked opportunity report                    | artifact |
| [product-02 · Bug intake and duplicate review](recipes/product-02.md) | When a structured bug report arrives | New issue or linked duplicate with supporting context | write    |
| [product-03 · Incident postmortem preparation](recipes/product-03.md) | When an incident is closed           | Draft postmortem and proposed follow-up actions       | artifact |

## Commerce

| Recipe                                                                          | Trigger                                        | Result                                            | Effects  |
| ------------------------------------------------------------------------------- | ---------------------------------------------- | ------------------------------------------------- | -------- |
| [commerce-01 · Stock exception and replenishment brief](recipes/commerce-01.md) | On stock threshold events and weekly review    | Stock-exception report and draft reorder proposal | artifact |
| [commerce-02 · Fulfillment exception coordination](recipes/commerce-02.md)      | Every day or when fulfillment stalls           | Expedite task and customer-update draft           | write    |
| [commerce-03 · Order anomaly review packet](recipes/commerce-03.md)             | When configured order-risk rules flag an order | Merchant review packet with missing evidence      | artifact |
| [commerce-04 · Product listing preparation](recipes/commerce-04.md)             | When approved product data changes             | Reviewable product-listing draft                  | artifact |
| [commerce-05 · Public review response queue](recipes/commerce-05.md)            | When a product or store review arrives         | Approved public response and internal case        | send     |
| [commerce-06 · Repeat-customer retention opportunities](recipes/commerce-06.md) | Every week after purchase activity refresh     | Retention opportunity brief and campaign drafts   | artifact |

[Installation protocol](installation.md) · [Runtime plans](runtime-plans.md) · [Recipe contract](recipe-contract.md) · [Machine-readable index](catalog.json)
