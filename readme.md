# Relay - Autonomous Email-to-Action Agent

Relay is a complete, dependency-free demo for **Problem 10: Autonomous Email-to-Action Agent** in the Supervity FDE assessment.

It simulates an operational inbox and demonstrates an agent that:

- classifies messages into six distinct intents (including invoice submission, payment query, billing dispute, spam, account update, and human review);
- takes a suitable action for every intent;
- routes an ambiguous billing message to a human instead of guessing;
- exposes the classification reasoning, confidence, action, and timestamp in an audit trail.

## Run locally

No installation is required. Open `index.html` in a browser.

For a local web server (optional):

```bash
npx serve .
```

Then open the URL shown in the terminal.

## Architecture and decisions

This is a front-end prototype intentionally built without a backend or external API dependency, so it is fully reproducible in a short assessment window. `app.js` holds deterministic synthetic inbox data and an explicit policy/result for each email. In a production system, the same interface would be backed by:

1. an email ingestion worker;
2. an LLM/rules classifier that returns structured JSON (`intent`, `confidence`, `reasoning`);
3. a policy gate that permits low-risk actions and escalates uncertain or high-impact decisions;
4. integrations for AP, ticketing, CRM, and outbound email;
5. append-only audit storage with actor, evidence, decision, action, and timestamp.

The important safety choice is shown in the ambiguous email from Priya Nair: its low confidence and missing details trigger a human-review task, not an autonomous reply or financial action.

## Suggested 5-minute demo flow

1. Start on the reset state and introduce the inbox and success metrics.
2. Click **Run agent** and point out the live queue, selected email, and audit records.
3. Select the invoice, payment query, dispute, and spam emails to show four different classifications and actions.
4. Select **Need help with the amount on our account** to demonstrate the ambiguous case and safe human fallback.
5. Close on the audit trail: every action has a timestamp, intent, action, and confidence.

## Trade-off

The UI uses transparent, deterministic decisions instead of a live LLM. This makes the assessment easy to run and evaluate offline. A production version would replace the seed decision logic with an LLM plus a validation schema and retain the same human-review guardrail for low-confidence messages.
