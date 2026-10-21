# Pilot plan

**Verdict: conditional go.** Run the pilot only after (a) a formal privacy and legal review and (b) a baseline of time per payment measured on about 20 cases. Until then ScreenGate stays a prototype on synthetic data.

## Shape (small, reversible, observed)
- **Who and how long:** 2 compliance analysts at one payments company, 6 weeks (long enough to cover a full monthly payment cycle).
- **Volume:** up to about 180 flagged payments in total, roughly 3 per analyst per working day.
- **How:** it runs alongside the current process. Analysts decide exactly as today, and every recommendation is reviewed.
- **Checkpoint:** a go, continue or stop decision at the end of week 3.

## Roles
| Role | Who | Does |
|---|---|---|
| Operator | The two analysts | Run ScreenGate on each flagged payment and decide |
| Escalation owner | Compliance officer (the MLRO), with a named deputy | Takes every escalation and resolves it |
| Decision owner | Head of compliance | Approves any change to instructions, policy or scope; can pause the pilot |
| Product owner | The product owner | Makes approved changes and re-runs the six tests |

Every role has a named backup. Weekly, in a 30-minute review, a sample of decisions is checked and the answers to two questions are logged: where did ScreenGate waste your time, and where did you not trust it.

## Success
At least 80% of recommendations accepted, zero missed escalations, the projected time saving (at least 40%) confirmed or corrected by measurement, and both analysts wanting to keep it. See [metrics.md](metrics.md).

## Rollback
1. **Pause:** the head of compliance can stop the pilot at any time, and must on any hard-zero breach.
2. **Fall back:** analysts continue manual screening, which never stopped.
3. **Diagnose:** within 1 working day the product owner reports what happened, how many payments were affected and the likely cause.
4. **Decide:** within 2 working days of that note the head of compliance chooses to restart narrower, hold until fixed, or end the pilot. The fix has no fixed deadline; it is done when the failed case and all six tests pass and the decision owner signs off.
5. **Return smaller,** in this order, picking one or more: exclude the failed case type, halve the payment ceiling, limit to one corridor, reduce to one analyst with the compliance officer checking every decision. After a missed escalation, the compliance officer checks every recommendation for the first week back.

The company's payment-system owner applies the narrowing by changing which payments are routed to ScreenGate.
