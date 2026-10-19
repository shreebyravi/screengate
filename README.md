# ScreenGate

An AML sanctions-screening copilot prototype for cross-border B2B payments on the UAE-India and UAE-UK corridors. A Screening Agent recommends Pass, Enhanced Due Diligence, or Escalate with cited reasoning, and a compliance analyst makes the final decision.

**Created by Shree Byravi** as part of the Agentic AI Capstone (Cohort 10). Product design, evaluation, and this prototype are her work.

## What this is

A capstone prototype, piloted under human review. All data is synthetic: fabricated names, watchlist entries, and transactions. No real people, companies, or sanctions records are included.

## License

Licensed under [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/). Credit Shree Byravi, no commercial use, no derivatives.

## Running it

Live demo: https://shreebyravi.github.io/screengate/

Or open `index.html` in a browser. To run payments through the agent, click the "AI key" button and paste your own Anthropic API key. The key stays in your browser and is never stored in this repository or sent to this website.

## Privacy and responsible use

Everything in this prototype is synthetic, and nothing is saved after the page is reloaded. A real pilot would need a formal privacy and legal review first. It would cover, for example:

- UAE: the federal Personal Data Protection Law (Federal Decree-Law 45 of 2021), plus DIFC or ADGM rules if the company sits in those zones.
- UK: UK GDPR and the Data Protection Act 2018.
- India: the Digital Personal Data Protection Act 2023, since Indian receivers' data is involved.
- Cross-border transfer: sending personal data to an AI provider outside these countries, and the provider's data terms.
- Record-keeping: the company's anti-money-laundering retention rules.

ScreenGate only recommends. A person always makes the decision.
