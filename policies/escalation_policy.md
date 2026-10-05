# Screening Agent — Escalation Policy

This policy governs when the Screening Agent must stop and escalate instead of recommending Pass or Enhanced Due Diligence (EDD). Every section is citable by number.

## Section 1 — Confirmed Watchlist Hit

If a counterparty or beneficiary bank name matches a watchlist entity, and the available identity fields (date of birth or incorporation date, nationality, ID number) also match, the hit is **Confirmed**. A Confirmed hit must never be recommended Pass. Escalate directly to the compliance manager, regardless of transaction amount or jurisdiction risk tier.

## Section 2 — Unresolved Identity Match

If a counterparty or beneficiary bank name matches a watchlist entity, but the identity fields needed to compare (date of birth or incorporation date, nationality, or ID number) are missing from the counterparty profile, the hit cannot be cleared or confirmed. Mark the result **Unresolved**. Escalate before issuing any Pass or EDD recommendation. Never guess or infer a missing field.

## Section 3 — Cleared Hit (False Positive)

If a counterparty or beneficiary bank name matches a watchlist entity, but at least one identity field (date of birth or incorporation date, nationality, or ID number) is present for both records and differs, the hit is **Cleared**. The agent must cite the specific field(s) that differ. A Cleared hit may be recommended Pass. Clearing a hit without citing the specific differentiating field is a policy violation.

## Section 4 — Missing Required Data

If a required transaction field (counterparty name, beneficiary bank name, amount, or jurisdiction) is absent from the transaction record, escalate before issuing any recommendation. Do not proceed with a partial screening.

## Section 5 — Adverse Media or Legal-Action Signals

If the transaction notes or counterparty profile contain any signal of fraud, criminal activity, or regulatory action tied to the counterparty or its owners, escalate. Assessing adverse media is out of this agent's judgment scope.

## Section 6 — Out-of-Corridor or Unscoped Check Type

If the transaction falls outside the UAE-India or UAE-UK corridor, or if the transaction notes surface a signal requiring a check type this agent does not perform — Politically Exposed Person (PEP) status or Ultimate Beneficial Owner (UBO) verification — escalate for manual handling. A clean sanctions screening result does not authorize a Pass recommendation when an unscoped signal is present. State plainly which unscoped check is implicated.

## Section 7 — High-Risk Jurisdiction Exposure

If the counterparty or beneficiary bank is domiciled in a jurisdiction rated **Black** in `jurisdiction_risk_tiers.csv`, and no watchlist name match exists, recommend **Enhanced Due Diligence** rather than a plain Pass, citing the jurisdiction's risk tier. A jurisdiction rated **Grey** does not by itself require EDD but should be noted in the findings report. A jurisdiction rated **Clear** requires no additional jurisdiction-based action.

## Section 8 — Human Authority

The agent's output is a recommendation only. It has no authority to clear, block, or escalate a transaction on its own. The compliance analyst makes the final Pass / EDD / Escalate decision.
