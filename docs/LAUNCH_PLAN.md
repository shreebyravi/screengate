# ScreenGate: Launch plan

A lead PM's plan for taking ScreenGate from prototype to a controlled pilot at one payments company.

**Status: nothing here has been run.** Every timeline, target and role is a proposal, and all numbers are projected until a pilot runs. No figure below is a measured result.

## Launch decision

**Conditional go for a small pilot.** It would run only after a formal privacy and legal review, a measured baseline and the requirements below. Until then, ScreenGate stays a prototype on synthetic data.

A real company should also compare building this with buying it, because vendors already describe AI for reviewing sanctions alerts.

## What we are trying to prove

| Question | How we answer it | What would stop us |
|---|---|---|
| Is review time or consistency a real problem here? | Interviews and a baseline of about 20 cases | Time and quality are already good |
| Does it save time without reducing quality? | Pilot compared with baseline | Any missed escalation; no time saved |
| Will analysts trust it appropriately? | Accepted, edited and sampled decisions | They ignore it, or approve without checking |
| Does it add value over current tools? | Build-or-buy comparison | A vendor already meets the need |

## Launch stages and gates

Each stage has a gate. Nobody moves on until the head of compliance signs off on it.

| Stage | Proposed length | What happens | Nothing moves on until |
|---|---|---|---|
| **0. Discovery** | 2-4 weeks | Analyst interviews, current tools, and a baseline on about 20 cases | Problem confirmed; owners named |
| **1. Readiness** | 4-8 weeks | Complete the requirements below; tighten policy Section 3 | Everything marked "before the pilot" is done |
| **2. Pilot, first half** | Weeks 1-3 | 2 analysts, alongside the current process. Every recommendation reviewed | Week 3 go, continue or stop decision |
| **3. Pilot, second half** | Weeks 4-6 | Same setup, covering a monthly payment cycle, up to about 180 flagged payments in total | Success bars met; both analysts want to keep it |
| **4. Controlled rollout** | One step at a time | More analysts or a further corridor, only with evidence | Results hold at each step |

**Out of scope for the pilot (stays manual):** other corridors, names in other languages or spellings, payments above a set ceiling, and politically exposed or government-linked persons, which are always escalated.

## What is required

Status today: **Not started** unless stated.

### Before the pilot

| Area | Requirement | Owner |
|---|---|---|
| Sponsor | Head of compliance agrees scope and owns decisions | Head of compliance |
| Baseline | Time per payment measured on about 20 cases | Compliance officer and PM |
| Privacy and legal | Formal review, covering personal data, cross-border transfer and record-keeping | Privacy and legal |
| Policy | Tighten Section 3 so a shared ID or birth date can't be cleared by one different field, and enforce it in code | Compliance and engineering |
| Watchlist | Trusted list and an approach for lists too large for a prompt | Compliance and engineering |
| Matching | Dedicated matching step, or an approved alternative | Engineering |
| Integration | Flagged payments from the payment system, and an on/off switch | Payment-system owner |
| AI setup | Approved model, region and server-side key handling | AI engineer and IT security |
| Evals | Larger eval set, with true matches and repeated runs. *Started: small synthetic set and stress tests* | PM and compliance |
| Security | Security assessment and independent testing | IT security |
| Audit | Saved decisions, evidence, reasons and approver | Engineering and compliance |
| Vendor | AI vendor and third-party review | Procurement and security |
| Model risk | AI governance or model risk review, where required | Compliance and risk |
| Monitoring | Logs, dashboard and alerts | Engineering and PM |
| Training | Guide for analysts, practice cases and how to disagree | PM and compliance officer |
| Support | Runbook, incident process and manual fallback | Operations and PM |

### Before a wider rollout

| Area | Requirement | Owner |
|---|---|---|
| Evidence | Pilot results against the baseline | PM and head of compliance |
| Business case | Cost, benefit and support model | PM and finance |
| Build or buy | Compare vendors using the same test set | PM, compliance and procurement |
| Controls | Payment ceilings and a second approver for very large payments | PM and compliance |

## Who owns what

| Role | Accountable for |
|---|---|
| **Head of compliance** | Go or no-go decisions, scope and policy changes; can pause at any time |
| **Compliance officer (MLRO), with a deputy** | Every escalation, and the weekly sample review |
| **Two pilot analysts** | Deciding every payment and giving feedback |
| **Lead PM** | Problem, metrics, roadmap, learning loop and communication |
| **Payment-system owner** | What is routed to ScreenGate, and the on/off switch |
| **AI and software engineers** | Reliability, evals, security and monitoring |
| **Privacy and legal** | Reviews and sign-off |

Every role has a named backup.

## Metrics after launch

### North star

**Median analyst time per flagged payment, at the same or better decision quality.**

- **Projected target:** at least 40% lower than the measured baseline.
- **Why this one:** it's the promised value, and it counts only if the quality guardrails hold.

### Review funnel

The funnel shows where the process breaks down.

| Stage | Metric | What it tells you |
|---|---|---|
| **1. Flagged** | Payments flagged by the payment system | Volume reaching ScreenGate |
| **2. Reviewed** | Payments with a recommendation and a person's decision | Whether the flow is completed |
| **3. Accepted or edited** | Recommendations accepted or changed | How useful the recommendations are |
| **4. Escalated** | Payments sent to the compliance officer | Workload for escalation owners |
| **5. Sampled as correct** | Decisions confirmed correct in weekly review | Whether speed is hurting quality |

### Business result

**Is the value greater than the cost?** Compare measured time saved and quality with the total running cost. See the [business case model](BUSINESS_CASE.md).

### Value and adoption metrics

| Metric | How it's calculated | Check | Proposed target |
|---|---|---|---|
| Time per payment | Open to decision | Weekly | At least 40% below baseline |
| Queue age | Time waiting for review | Weekly | No worse than baseline |
| Analyst adoption | Whether both analysts want to keep it | Weekly and week 3 | Both |
| Time spent working around it | Weekly feedback | Weekly | Falling |

### AI quality metrics

| Metric | How it's calculated | Check | Proposed target |
|---|---|---|---|
| Accepted unchanged | Accepted recommendations ÷ all recommendations | Weekly | At least 80% |
| Edited | Changed recommendations ÷ all recommendations | Weekly | At most 30% |
| Evidence present | Recommendations with cited evidence | Weekly sample | 100% |
| Citation accuracy | Citations that exist and support the claim | Weekly sample | No made-up sources |
| False-alarm clearing quality | Correctly cleared same-name cases, in sampled review | Weekly | Set before the pilot |
| Variation | Same safe outcome across repeated test runs | Each release | Hard-limit cases safe on every run |
| Eval pass rate | Six tests and stress tests passing | Each change and monthly | No regressions |

### Reliability and cost metrics

| Metric | Check | Proposed target |
|---|---|---|
| Time to first recommendation | Daily | Measured first; no target set yet |
| AI error rate | Daily | Set before the pilot |
| Cost per payment | Weekly | Clearly below the value of analyst time saved |

### Guardrails

**Hard limits:** any breach pauses the pilot immediately.

| Must always be zero | Why |
|---|---|
| **Missed escalation:** should have escalated, but was recommended Pass or Extra checks | The most serious error |
| **Payment released without a person's decision** | Breaks the core control |
| **Real personal data before the privacy and legal review** | Regulatory risk |
| **Unapproved change to instructions, policy or scope** | Decisions must stay controlled |

**Warning guardrails:**

| Guardrail | Threshold | If breached |
|---|---|---|
| Accepted unchanged | Below 80% for a week | Head of compliance reviews and may pause |
| Edited | Above 30% | Product owner reviews the instructions |
| Very fast approvals | Unusually short review times | Sample those cases for automation bias |
| Drift | Any eval regression | Stop further use until fixed |

## Monitoring routine

| When | What | Who |
|---|---|---|
| Every day | Hard limits, errors and cost | Engineering and PM |
| Every week | 30-minute review: metrics, sampled decisions, and two questions: where did it waste your time, and where did you not trust it? | Analysts, compliance officer and PM |
| Every change | Re-run evals; head of compliance approves | PM and AI engineer |
| Every month | Full eval run, drift review and cost review | PM and engineering |
| End of week 3 | Go, continue or stop | Head of compliance |

## Training and communication

| Audience | What they need | When |
|---|---|---|
| Analysts | Guide, practice cases and how to disagree | Before the pilot |
| Compliance officer | Escalation handling and weekly review | Before the pilot |
| Payment-system owner | Routing and on/off process | Before the pilot |
| Leadership | Weekly summary and week 3 decision | Throughout |

## Rollback

1. **Pause:** the head of compliance can stop the pilot at any time, and must on any hard-limit breach.
2. **Fall back:** analysts continue manual screening, which never stopped.
3. **Diagnose:** within 1 working day, the product owner reports what happened, how many payments were affected and the likely cause.
4. **Decide:** within 2 working days of that note, the head of compliance chooses to restart narrower, hold until fixed, or end the pilot.
5. **Return smaller,** in this order, picking one or more: exclude the failed case type, halve the payment ceiling, limit to one corridor, or reduce to one analyst with the compliance officer checking every decision. After a missed escalation, the compliance officer checks every recommendation for the first week back.

The payment-system owner applies the narrowing by changing which payments are routed to ScreenGate. The fix is done when the failed case and all tests pass, and the decision owner signs off.

## Main launch risks

| Risk | Early sign | Response |
|---|---|---|
| A vendor already meets the need | Discovery and comparison | Buy, or use this plan to evaluate the vendor |
| Analysts over-trust it | Very fast approvals | Sampling, evidence and training |
| Name matching fails on new patterns | Sampled errors | Keep those cases manual; add dedicated matching |
| Review doesn't save time | Flat time per payment | Fix, narrow or stop |
| Privacy review blocks data use | Open issues in review | Change setup, or don't start |

## Decisions needed from the company

1. Who owns the pilot and each named role?
2. What payment ceiling applies?
3. Which watchlist and matching tool should be used?
4. Which data and AI providers are allowed?
5. Should this be built, bought or tested alongside a vendor?
