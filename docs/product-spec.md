# Product specification

## Purpose
Help a compliance analyst make a faster, consistent first pass on a flagged cross-border payment, with the evidence written down, while a person makes every final decision.

## Scope
**In:** payments the company's payment system has flagged (a new receiver, an amount over $10,000, or a receiver or bank in a high-risk country) on the UAE-India and UAE-UK corridors.

**Out (stays fully manual in a pilot):** other corridors; names in other languages or spellings; payments with a politically exposed or government-linked person (ScreenGate always escalates these); payments above a ceiling the head of compliance sets before day one.

## The flow
1. The payment system flags a payment and sends it to ScreenGate.
2. ScreenGate checks the receiver and the receiver's bank against the watchlist, country risk and company policy.
3. ScreenGate recommends one of three outcomes and shows its evidence.
4. A person approves, edits or escalates. Nothing completes without that decision.
5. Holding and releasing the payment happen in the company's own payment system, which is outside this prototype.

## Recommendations
| Recommendation (as shown) | Meaning |
|---|---|
| **Looks clear** (Pass) | No unresolved match or risk signal found |
| **Extra checks needed** (Enhanced Due Diligence) | No name match, but a risk factor such as a high-risk jurisdiction requires more checking |
| **Cannot clear: escalate** (Escalate) | A person above the analyst must handle it |

## Behaviour rules the product follows
- A **confirmed** watchlist match is always escalated, whatever the amount or country.
- If the identity fields needed to confirm or clear a match are **missing**, it escalates.
- If a name matches but the date of birth, nationality and ID **differ**, it can clear the hit and must cite the differing fields.
- A receiver bank in a **Black-tier** jurisdiction needs Extra checks even with no name match.
- A signal outside its scope, such as a politically exposed person, is **escalated for manual handling**; ScreenGate does not assess it.
- It never approves or blocks a payment, and it does not claim to detect fraud.

## What the screen shows
The payment and the payment system's reasons for flagging it; ScreenGate's recommendation next to the payment title; the findings (screening results, cited reasoning, history); then Approve, Edit and Escalate. Escalate asks for a one-line reason. Every AI result is labelled "AI-generated, please verify".

## Two ways to use the demo
- **Recorded examples** (no key): saved real answers for the six test payments, clearly labelled.
- **Live:** the visitor's own AI key, kept only in their browser.

## Non-goals
Holding or releasing money, saved decisions, a sortable queue, customer-set ceilings, a second approver for very large payments, and in-product feedback. These are listed as next scope.

## Data
All names, companies, watchlist entries and payments are synthetic and live in `data/`. The policy the agent applies is in `policies/escalation_policy.md`.
