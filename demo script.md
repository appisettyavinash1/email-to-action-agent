# 5-minute demo script

## 0:00 - 0:30: The problem

"This is Relay, an autonomous email-to-action agent. It processes an operational inbox, identifies the message intent, takes a safe next action, and records exactly what happened."

## 0:30 - 1:15: The approach

"The agent works in four stages: ingest the email, classify the intent, apply an action policy, and write an audit record. High-confidence, low-risk cases are actioned autonomously. Ambiguous cases are escalated instead of guessed."

## 1:15 - 2:15: Run the queue

1. Click **Run agent**.
2. Point out that the top metrics increment as each message is processed.
3. Explain that the right-side panel shows the current decision and the bottom table is the audit trail.

Say: "The prototype has six synthetic messages and handles every one. Five are actioned autonomously, while one is intentionally sent for human review."

## 2:15 - 3:30: Show distinct decisions

Click these processed messages and briefly describe their outcome:

- **Invoice INV-2048**: classified as invoice submission and logged in accounts payable.
- **PO-880 payment**: classified as payment query and a payment-status reply is drafted.
- **Disputed charge**: classified as billing dispute and a case is opened.
- **Growth toolkit**: classified as spam and archived.

## 3:30 - 4:20: Show the safety guardrail

Click **Need help with the amount on our account**.

Say: "This is deliberately ambiguous: it could be a payment query or a dispute, but it has no invoice ID, amount, or requested resolution. The confidence is 62%, so policy prevents an external automated reply and creates a human-review task."

## 4:20 - 5:00: Close with production path

"This front-end proof of concept uses transparent deterministic decisions so it is easy to run offline. In production, I would swap in a structured LLM classifier, validate output against a schema, apply a confidence-and-risk policy gate, invoke AP/ticketing/CRM integrations, and write an append-only audit event for every step."

Mention the key trade-off: "I optimized for reproducibility and explainability in the assessment, while preserving the right architecture and safety boundary for a production agent."
