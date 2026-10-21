# Users and problem

## The problem, in one paragraph
When a company sends money across borders, its payment system flags some payments for a sanctions check: a new receiver, a large amount, or a high-risk country. A person then has to decide whether the payment can go ahead. Today that means comparing the receiver and their bank against watchlists, reading their profile, checking country risk and applying company policy, one payment at a time. That is slow, it varies from person to person when the team is busy, and the reasoning is hard to show afterwards. Getting it wrong has a real cost: regulators fine firms whose screening controls fail.

## Who it is for

| Segment | Role in the flow | What they need | What worries them |
|---|---|---|---|
| **Compliance analyst** (primary user) | Reviews every flagged payment and decides: approve, edit or escalate | A fast first pass, the evidence behind it, the same standard every time | Clearing a payment that should have been stopped; being unable to explain why they cleared it |
| **Compliance officer / MLRO** (escalation owner) | Takes the escalated payments and resolves them | Escalations that arrive with clear reasons and cited evidence | Surprises, thin explanations, missing audit trail |
| **Head of compliance** (decision owner) | Approves any change to ScreenGate's instructions, policy or scope; can pause it | Control, a clear record, evidence it behaves as designed | An unreviewed change; an AI acting without a person's decision |
| **Payment-system owner** | Decides which payments are routed to ScreenGate | Predictable volume and a simple on/off switch | Extra load, unclear ownership when something goes wrong |
| **Privacy and legal** | Reviews before any real data is used | Clear data flows and limits | Personal data going somewhere unreviewed |

The people whose payments are being checked are affected but are not users.

## What the analyst is trying to get done
- Decide quickly and correctly whether a flagged payment can go ahead.
- Be able to show why, if asked later.
- Escalate the true matches every time, and not waste time on false alarms such as the same name belonging to a different person.

## How it works today vs with ScreenGate

**Today:** payment flagged, then the analyst compares names, profiles, country risk and policy by hand, then decides, then writes a note.

**With ScreenGate:** payment flagged, then ScreenGate does the first pass and writes down what it found and why, then the analyst reads the reasons, then the analyst decides. ScreenGate never approves or blocks anything.

## Where it helps, and where it does not
- It helps with the **alert review step**: consistency, speed, and written evidence.
- It does **not** fix list coverage (it uses the watchlist it is given), customer due diligence, transaction monitoring or regulatory reporting.

## Evidence status (stated honestly)
This document comes from the product design and the six test cases. It does not contain results from interviews with real analysts. The following are **assumptions the pilot is built to test**:
- Analysts spend meaningful time per flagged payment (a baseline will be measured on about 20 cases before the pilot).
- Analysts will trust the reasons enough to use them (measured by how often recommendations are accepted unchanged).
- A first pass cuts review time by at least 40% (projected, not measured).

## How the pilot checks these assumptions
Two analysts, six weeks, about 180 flagged payments, running alongside the current process. Success is at least 80% of recommendations accepted, zero missed escalations, and both analysts wanting to keep it.
