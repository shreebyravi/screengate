# ScreenGate: Data guide

All data is synthetic: fabricated names, watchlist entries and payments. No real people, companies or sanctions records are included. Some regions are named Region A, B and C.

## Data files

| File | Rows | Contains | Key columns |
|---|---|---|---|
| `data/transactions.csv` | 15 | Flagged payments | `corridor`, `counterparty_name`, `beneficiary_bank_name`, `amount_usd`, trigger flags, `prior_transaction_history`, `notes` |
| `data/counterparty_profiles.csv` | 21 | Receiver and bank profiles | `dob_or_incorporation_date`, `nationality`, `id_number`, `address` |
| `data/watchlist.csv` | 20 | Fictional sanctioned or high-risk entries | `strong_aliases`, `weak_aliases`, `id_number`, `nationality` |
| `data/jurisdiction_risk_tiers.csv` | 7 | Country risk ratings | `jurisdiction`, `risk_tier` |
| `data/eval_cases.csv` | 6 | Test cases and expected behaviour | `case_id`, `transaction_id`, `expected_behavior` |

The stress case T-1016 lives in `index.html`, separately from the 15 payments in `transactions.csv`.

`data/recorded/stress/` holds the stress-test cases, expected results and three saved answers for each case.

## Policies

| File | Covers |
|---|---|
| `policies/escalation_policy.md` | The 8 sections the agent cites |
| `policies/audit_trail_template.md` | A template for a filed review note |

These are fictional and aren't legal or regulatory guidance.

## Key definitions

| Term | Meaning |
|---|---|
| Flagged payment | The payment system marked it for review because of a new receiver, an amount over $10,000, or a receiver or bank in a high-risk country |
| Confirmed hit | Name and available identity fields match a watchlist entry |
| Unresolved match | Name matches, but identity fields needed to compare are missing |
| Cleared hit | Name matches, but an identity field shows a different party |
| Strong and weak alias | Other names listed for a watchlist entry |
| Looks clear | Shown for a Pass recommendation |
| Extra checks needed | Shown for Enhanced Due Diligence |
| Cannot clear: escalate | Shown for an Escalate recommendation |

## The main examples

| Payment | What it shows |
|---|---|
| T-1001 | A clean payment |
| T-1002 | Same name, different person |
| T-1003 | A confirmed sanctions match |
| T-1004 | Missing identity data |
| T-1005 | Several flags, with a high-risk bank |
| T-1006 | A politically exposed person signal |
| T-1016 | A match only through a weak alias |
