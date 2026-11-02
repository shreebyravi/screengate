# ScreenGate: AI product decisions

How building with a large language model (LLM) changes product management, which decisions a PM has to make, what this prototype chose, and what a real implementation would add.

**How to read this:** "This prototype" means something actually done here. "Real implementation" means a proposal that hasn't been built or tested.

## How AI product management differs

| Area | Traditional software | AI product |
|---|---|---|
| **Behaviour** | The same input usually gives the same output | The same input can give different outputs |
| **Requirements** | "When X happens, do Y" | Also: what good looks like, what it must never do, and how often it may be wrong |
| **Testing** | Pass or fail against fixed rules | Evals: sample cases, judged for quality, repeated over time |
| **What gets built** | Screens, logic and data | Those, plus prompts, context, evals and guardrails |
| **Main failure** | A bug, usually repeatable | A confident wrong answer, which can be hard to spot |
| **Cost** | Mostly fixed once built | Can rise with each use of the model |
| **Change** | Mostly changes when the team releases | A model, prompt or policy change can alter behaviour |
| **User interface** | Shows results | Must also show evidence and make it easy to disagree |

## How development changed on this project

| Traditional step | What changed here |
|---|---|
| Write a specification | Also wrote the agent's instructions and policy. One added rule changed the product's behaviour |
| Developers build it | An AI coding assistant wrote the code, working from product decisions, tests and a plan |
| QA checks the build | Writing test cases and judging answers became a core PM job |
| Fix the bug | The T-1016 fix was a change to the instructions, followed by a re-test |
| Review the design | Also asked whether a person could see why the AI said this and disagree |

## Decisions a PM has to make

### 1. Should this use AI at all?

- **Options weighed:** rules only, full automation, or AI that recommends while a person decides.
- **This prototype:** AI recommends and explains. A person decides.
- **Real implementation:** use a dedicated matching tool to find candidates, and AI only for judgement and written reasons.

### 2. How much freedom does the agent get?

- **This prototype:** recommend only. It never approves, blocks or takes action.
- **Real implementation:** any automatic clearing of false alarms would need strong evidence and compliance approval. It isn't proposed here.

### 3. Which model?

- **This prototype:** Claude Sonnet 4.5, set as one value in the code. It wasn't compared against other models.
- **Real implementation:** compare models on the same evals, and check which providers and regions the company approves. Re-test after any model change.

### 4. What does the agent get to see? (context)

- **This prototype:** the payment, profiles, 20-entry watchlist, country risk and policy. Fields not needed, such as payment purpose, aren't sent.
- **Real implementation:** a real watchlist is far too large for a prompt. A matching step or retrieval (RAG) would first find the relevant entries, and it would need its own tests because a retrieval miss could become a missed match.

### 5. How is the answer structured?

- **This prototype:** labelled text fields that the page parses. If they don't parse, the page shows the raw text with a notice.
- **Real implementation:** consider a stricter structured format, so code can validate answers more reliably.

### 6. What counts as good enough? (evals)

- **This prototype:** six cases with expected results written first, one hard case, and a person's verdicts.
- **Real implementation:** many more cases, reviewed by compliance professionals, with zero missed escalations as a release gate.

### 7. What should the product do about variation?

- **This prototype:** six stress tests ran three times each. All 18 final answers matched, but SG-S6's reasoning varied: two runs marked the match Cleared and one Unresolved. The rules are instructions to the AI, not separate code checks.
- **Lesson:** an instruction isn't a guarantee. SpaceBack, a later project, showed this directly.
- **Real implementation:** measure variation over many runs, and enforce hard rules in code. For example, a confirmed match can never display as Looks clear.

### 8. How do we avoid made-up facts?

- **This prototype:** the agent must use only the given context and cite real IDs and sections. T-1016 still showed an overclaimed citation, which was fixed in the instructions.
- **Real implementation:** check automatically that each citation exists, and sample whether it supports the claim.

### 9. How do we handle misuse and bad input?

- **This prototype:** trick instructions and a fake clearance claim were escalated in all runs, in a small test.
- **Real implementation:** test whether payment notes or names can manipulate the agent, and get independent security testing.

### 10. How do we keep the human review real?

- **The risk:** people may approve everything once the AI seems good, a problem called automation bias.
- **This prototype:** each result shows evidence and is labelled "AI-generated, please verify".
- **Real implementation:** monitor accepted-unchanged and edit rates, require reasons for disagreement, and review samples weekly.

### 11. What will it cost, and how fast must it be?

- **This prototype:** cost and speed weren't formally measured. Checks took roughly 5 to 20 seconds, as observed. The README says a run costs a few cents.
- **How to estimate:** cost per payment = (input tokens × input price) + (output tokens × output price).
- **Real implementation:** measure both, and compare the cost with the analyst time saved.

### 12. What happens when the AI fails?

- **This prototype:** errors are shown, and nothing happens automatically.
- **Real implementation:** manual screening continues, and failures are logged and alerted.

### 13. What happens after launch?

- **This prototype:** nothing is saved after reload, so monitoring isn't built.
- **Real implementation:** version prompts and models, keep an audit trail, and re-run evals monthly and after any change.

### 14. What data can go to the model?

- **This prototype:** synthetic data only. A visitor's key stays in their browser.
- **Real implementation:** minimise personal data, decide retention and regions, keep keys on a server, and complete a privacy and legal review.

## Trade-offs made here

| Choice | What it gave us | What it cost | In a real implementation |
|---|---|---|---|
| Person decides everything | Accountability | Limits time saved | Reassess only with evidence and approval |
| Whole watchlist in the prompt | Simple and easy to test | Doesn't scale | Matching step or retrieval |
| AI judgement for names | Good written reasoning | Less predictable, and English only | Dedicated matching plus AI reasons |
| One-page app with no backend | Fast and easy to share | No login, saved audit trail or integration | Server, roles and audit trail |
| Recorded examples | Anyone can try it | Not a live check | Keep for demos only |
| Small test set | Quick learning | Weak evidence | Larger, reviewed test set |
| Two corridors | Small and testable | Limited coverage | Add only with evidence |

## Lessons from building it

| What happened | PM lesson |
|---|---|
| A reviewer flagged a missing type of test | Sanctions-clean doesn't mean nothing else needs a person |
| A hard case found a flaw that easy cases missed | Include hard cases, not just tidy ones |
| Pass-through payments were built, then removed | Removing something can make the flow clearer |
| Live testing on a phone found layout problems | Try the real experience |
| Asking whether fines were truly relevant changed the claims | Evidence must support the actual product scope |
| The market scan found similar vendor products | Say so plainly, and don't claim uniqueness |
| A stress test exposed a loose policy rule behind a safe answer | Check why an answer is right, not only whether it matches |

## What a real team would add

| Role | Would own |
|---|---|
| Compliance analysts and officer | Workflow reality, judging answers and escalations |
| Head of compliance | Scope, policy, go or no-go decisions |
| ML or AI engineer | Model calls, evals and monitoring |
| Software engineers | Integrations, security and audit trail |
| Privacy, legal and model risk | Reviews and sign-off |
| PM | Problem, scope, quality bar, autonomy level and learning loop |

## My role in this project

**Shree Byravi** led the product work. An AI coding assistant wrote the code, working from these decisions, tests and plans:

- Chose the problem, user, narrow scope and "a person always decides" model.
- Wrote and judged the test cases, with expected results first.
- Chose realism changes, including showing ScreenGate as a step after a payment system, and removing pass-through payments.
- Pushed for plain language and tested the live site, including on a phone.
- Decided the pilot shape with its roles, metrics, rollback and six-week length.
- Questioned whether the fines cited were truly relevant, which led to more honest claims.

ScreenGate is a personal prototype on synthetic data. No analyst or company has used it, and it isn't production software.
