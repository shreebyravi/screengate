# Metrics: north star and guardrails

Everything below is **projected until the pilot runs**. The baseline numbers are measured first; nothing here is a result.

## North star metric
**Median analyst time per flagged payment, at the same or better decision quality.**

- Why this one: it is the value ScreenGate promises (a faster, consistent first pass), and it only counts if quality holds, which the guardrails below enforce.
- Projected target: at least **40% lower** than the baseline, which is measured on about 20 cases before the pilot starts.

## Input metrics (what moves the north star)
| Metric | Meaning | Bar |
|---|---|---|
| Accepted unchanged | Share of recommendations the analyst accepts as they are (a proxy for trust) | at least 80% |
| Edited | Share of recommendations the analyst changes | at most 30% |
| Evidence present | Every recommendation carries cited reasons and evidence | 100% by design; checked in the weekly sample |
| Time to first recommendation | How long ScreenGate takes to produce its answer | measured, no bar set |

## Guardrail metrics (what must not get worse)
| Guardrail | Threshold | If breached |
|---|---|---|
| **Missed escalation**: a payment that should have been escalated but was recommended Pass or Extra checks | **Zero** | Pause the pilot immediately |
| **Payment released without a person's decision** | **Zero** | Pause the pilot immediately |
| Accepted unchanged | Below 80% for a week | Head of compliance reviews the cases and may pause |
| Edited | Above 30% | Product owner reviews the instructions |
| Analyst adoption | Both pilot analysts want to keep it | Anything less means no expansion |
| Personal data | No real personal data before a formal privacy and legal review | Real payments are not used |
| Drift | The six test cases are re-run monthly and after any change to the AI model or instructions | Any regression pauses further use until fixed |

## How it is measured in the pilot
- **Button data:** every Approve, Edit and Escalate is logged against ScreenGate's recommendation, with a one-line reason when an analyst edits or escalates against it.
- **Weekly review:** a sample of decisions is checked by the compliance officer with the analysts; the head of compliance reads the summary.
- **Baseline:** time per payment on about 20 cases before the pilot.
- **Checkpoint:** a go, continue or stop decision at the end of week 3.

The prototype itself saves nothing after a page reload, so this logging belongs to the pilot setup, not the prototype.
