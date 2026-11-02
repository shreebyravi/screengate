# ScreenGate: Backlog

User stories for the next scope, with acceptance criteria. **Priorities are provisional.** No real users have confirmed them, and no engineering team has estimated them.

**Priority:** Must = needed for that stage. Should = important, but the stage can run without it. Could = useful later.

## Before a pilot

| ID | Story | Acceptance criteria | Priority |
|---|---|---|---|
| B-1 | As a compliance officer, a shared ID or birth date can't be cleared by one different field | Policy Section 3 updated; a code check stops a Looks clear result; SG-S6-style tests pass on repeated runs | Must |
| B-2 | As an analyst, flagged payments arrive from the payment system | Only flagged payments appear; failures are visible; an on/off switch exists | Must |
| B-3 | As a compliance lead, a trusted watchlist is used, and a large list works | Approved source, with update date shown; a matching step finds candidates before the AI runs | Must |
| B-4 | As an auditor, I can see saved decisions and evidence | Recommendation, evidence, decision, reason, person and time are stored and can't be silently changed | Must |
| B-5 | As an IT owner, keys and AI calls run on a server | No key in the browser; calls logged; only approved data is sent | Must |
| B-6 | As a product owner, each prompt and model version is tracked | Each result records its versions; a change can't be released without an eval run | Must |
| B-7 | As a head of compliance, I set a payment ceiling | Payments above it stay manual; only approved people can change it | Must |
| B-8 | As a PM, I can measure time per payment and how often recommendations are accepted | Open and decision times are saved; weekly report matches the launch plan | Must |
| B-9 | As an analyst, I give a reason when I disagree | Reasons are required when editing or escalating against a recommendation, and appear in weekly review | Should |
| B-10 | As an analyst, I sort and filter the queue | Sort by risk or arrival; filter by status | Should |

## After the pilot

| ID | Story | Acceptance criteria | Priority |
|---|---|---|---|
| B-11 | As a compliance officer, very large payments need a second approver | Above an agreed amount, two different people must approve | Should |
| B-12 | As a compliance team, names in other languages are handled | Tested on agreed languages and spellings; unsupported cases stay manual | Should |
| B-13 | As a buyer, I can compare this with vendor tools | Same test set; results reviewed by compliance | Should |
| B-14 | As a compliance team, a further corridor can be added | Added only with evidence, and tested before release | Could |

## Known issues in the prototype

| ID | Issue | Priority |
|---|---|---|
| B-15 | Name matching relies on AI judgement alone | Must before a pilot; covered by B-3 |
| B-16 | Decisions reset after a page reload | Must before a pilot; covered by B-4 |
| B-17 | Stress tests ran separately from the app, in small numbers | Must before a pilot |
