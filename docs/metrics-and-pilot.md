# Metrics and pilot plan

How we would know ScreenGate works, and how a pilot would be run.

## Metrics: north star and guardrails

Everything below is **projected until the pilot runs**. The baseline numbers are measured first; nothing here is a result.

### North star metric
**Median analyst time per flagged payment, at the same or better decision quality.**

- Why this one: it is the value ScreenGate promises (a faster, consistent first pass), and it only counts if quality holds, which the guardrails below enforce.
- Projected target: at least **40% lower** than the baseline, which is measured on about 20 cases before the pilot starts.

### Input metrics (what moves the north star)
| Metric | Meaning | Bar |
|---|---|---|
| Accepted unchanged | Share of recommendations the analyst accepts as they are (a proxy for trust) | at least 80% |
| Edited | Share of recommendations the analyst changes | at most 30% |
| Evidence present | Every recommendation carries cited reasons and evidence | 100% by design; checked in the weekly sample |
| Time to first recommendation | How long ScreenGate takes to produce its answer | measured, no bar set |

### Guardrail metrics (what must not get worse)
| Guardrail | Threshold | If breached |
|---|---|---|
| **Missed escalation**: a payment that should have been escalated but was recommended Pass or Extra checks | **Zero** | Pause the pilot immediately |
| **Payment released without a person's decision** | **Zero** | Pause the pilot immediately |
| Accepted unchanged | Below 80% for a week | Head of compliance reviews the cases and may pause |
| Edited | Above 30% | Product owner reviews the instructions |
| Analyst adoption | Both pilot analysts want to keep it | Anything less means no expansion |
| Personal data | No real personal data before a formal privacy and legal review | Real payments are not used |
| Drift | The six test cases are re-run monthly and after any change to the AI model or instructions | Any regression pauses further use until fixed |

### How it is measured in the pilot
- **Button data:** every Approve, Edit and Escalate is logged against ScreenGate's recommendation, with a one-line reason when an analyst edits or escalates against it.
- **Weekly review:** a sample of decisions is checked by the compliance officer with the analysts; the head of compliance reads the summary.
- **Baseline:** time per payment on about 20 cases before the pilot.
- **Checkpoint:** a go, continue or stop decision at the end of week 3.

The prototype itself saves nothing after a page reload, so this logging belongs to the pilot setup, not the prototype.

## Pilot plan

**Verdict: conditional go.** Run the pilot only after (a) a formal privacy and legal review and (b) a baseline of time per payment measured on about 20 cases. Until then ScreenGate stays a prototype on synthetic data.

### Shape (small, reversible, observed)
- **Who and how long:** 2 compliance analysts at one payments company, 6 weeks (long enough to cover a full monthly payment cycle).
- **Volume:** up to about 180 flagged payments in total, roughly 3 per analyst per working day.
- **How:** it runs alongside the current process. Analysts decide exactly as today, and every recommendation is reviewed.
- **Checkpoint:** a go, continue or stop decision at the end of week 3.

### Roles
| Role | Who | Does |
|---|---|---|
| Operator | The two analysts | Run ScreenGate on each flagged payment and decide |
| Escalation owner | Compliance officer (the MLRO), with a named deputy | Takes every escalation and resolves it |
| Decision owner | Head of compliance | Approves any change to instructions, policy or scope; can pause the pilot |
| Product owner | The product owner | Makes approved changes and re-runs the six tests |

Every role has a named backup. Weekly, in a 30-minute review, a sample of decisions is checked and the answers to two questions are logged: where did ScreenGate waste your time, and where did you not trust it.

### Success
At least 80% of recommendations accepted, zero missed escalations, the projected time saving (at least 40%) confirmed or corrected by measurement, and both analysts wanting to keep it. See the metrics section above.

### Rollback
1. **Pause:** the head of compliance can stop the pilot at any time, and must on any hard-zero breach.
2. **Fall back:** analysts continue manual screening, which never stopped.
3. **Diagnose:** within 1 working day the product owner reports what happened, how many payments were affected and the likely cause.
4. **Decide:** within 2 working days of that note the head of compliance chooses to restart narrower, hold until fixed, or end the pilot. The fix has no fixed deadline; it is done when the failed case and all six tests pass and the decision owner signs off.
5. **Return smaller,** in this order, picking one or more: exclude the failed case type, halve the payment ceiling, limit to one corridor, reduce to one analyst with the compliance officer checking every decision. After a missed escalation, the compliance officer checks every recommendation for the first week back.

The company's payment-system owner applies the narrowing by changing which payments are routed to ScreenGate.
