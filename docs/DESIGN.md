# ScreenGate: Design

How the agent and workflow behave.

## Agent role

A Screening Agent that checks the receiver and the receiver's bank on a flagged payment against the watchlist, country risk and policy. It recommends one of three outcomes, with cited reasons, for a compliance analyst to decide.

## Today, and with ScreenGate

**Today:**
1. The payment system flags a payment and queues it.
2. The analyst reads the details.
3. The analyst compares the receiver and bank against the watchlist by hand.
4. If a name matches, the analyst checks identity fields.
5. The analyst checks country risk and policy.
6. The analyst decides and writes a note, escalating if needed.

**With ScreenGate:**
1. The payment system flags a payment. This is mocked in the demo.
2. The payment arrives in ScreenGate and is checked.
3. A notification says it's waiting for review.
4. The analyst opens it and sees why it was flagged, the recommendation, findings and reasons.
5. The analyst approves, edits or escalates. Escalate asks for a one-line reason.
6. The result is recorded for the session. Holding or releasing money stays in the company's payment system.

## Agent loop

- **Observe:** the payment, receiver and bank profiles, watchlist, country risk and policy.
- **Decide:** whether a name match is confirmed, unresolved or cleared, and which recommendation applies.
- **Act:** write a labelled recommendation with citations. It takes no action with consequences.
- **Check:** the page parses the fields and shows raw text with a notice if they don't parse. A person reviews the reasoning.

## Inputs

| Input | Source | Notes |
|---|---|---|
| Payment | Payment record | ID, corridor, receiver, bank, amount, jurisdictions, flags, history and notes |
| Profiles | `data/counterparty_profiles.csv` | Identity fields for receiver and bank |
| Watchlist | `data/watchlist.csv` | 20 fictional entries |
| Country risk | `data/jurisdiction_risk_tiers.csv` | 7 rows, rated Clear, Grey or Black |
| Policy | `policies/escalation_policy.md` | 8 citable sections |

Payment reference, purpose, value date and invented payment-instruction details appear on screen, but they aren't sent to the AI.

## Output

Labelled fields, one per line: `TRANSACTION_ID`, `CORRIDOR`, `TRIGGER_CRITERIA_MET`, `COUNTERPARTY_SCREENING_RESULT`, `BENEFICIARY_BANK_SCREENING_RESULT`, `CITATIONS`, `CITED_REASONING`, `PRIOR_TRANSACTION_HISTORY`, `RECOMMENDED_DECISION` and `WHY`.

An escalation begins with "REFUSED" and the policy section. See [AGENT_INSTRUCTIONS.md](AGENT_INSTRUCTIONS.md).

## Escalation rules

| Situation | Agent recommends |
|---|---|
| Confirmed watchlist hit (Section 1) | Escalate |
| Unresolved identity match (Section 2) | Escalate |
| Name matches, but an identity field differs (Section 3) | Can clear, citing the field |
| Missing required data (Section 4) | Escalate |
| Adverse media or legal signals (Section 5) | Escalate, without assessing them |
| Outside scope, such as a politically exposed person (Section 6) | Escalate for manual handling |
| Black-tier jurisdiction with no name match (Section 7) | Extra checks |
| Not confident a hit is genuinely cleared | Escalate |

## Memory

No memory across payments. Every payment is screened fresh, and prior history is context only, never a reason to skip a check. Decisions aren't saved after a page reload.

## Human approval

A person approves, edits or escalates every payment. The AI's output is a recommendation only (policy Section 8).

## Screens

| Screen | Shows |
|---|---|
| First screen | How a payment moves through the process |
| Queue | Four clickable boxes (All, Waiting for review, Approved, Escalated), and the payment list |
| Payment detail | Why it was flagged, the recommendation, findings, decision area and history |
| How well it works | Tests, improvement, known limits and next scope |
| Recorded view | A banner, with each saved answer labelled |
| Phone layout | One payment at a time, with Back buttons |
