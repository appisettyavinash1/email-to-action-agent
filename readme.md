# Autonomous Email-to-Action Agent

Relay is a front-end demo of an autonomous operations agent that converts incoming email into safe, traceable actions.

## Problem Statement

Operational inboxes contain invoices, payment questions, billing disputes, account changes, promotions, and incomplete requests. Reviewing every message manually is slow, while automating uncertain decisions is risky. Relay demonstrates a workflow that classifies emails, selects an appropriate simulated action, and escalates ambiguous messages for human review.

## Features

- Six-item synthetic operational inbox
- Email detail view with sender, message, and timestamp
- One-click sequential agent processing
- Intent classification with confidence scores and reasoning
- Simulated billing-operation actions
- Safe escalation for low-confidence requests
- Processing metrics, audit trail, and resettable demo state

## Tech Stack

- HTML5
- CSS3
- Vanilla JavaScript

No frameworks, packages, backend service, or database are required.

## Architecture

```text
Synthetic email queue → Classification data → Simulated action / human review
                                         ↓
                           Metrics, decision view, and audit trail
```

`app.js` contains the sample emails and predefined decisions. It updates the inbox, decision panel, metrics, and audit trail. `index.html` provides the structure, and `style.css` defines the UI.

## Intent and Actions

| Intent | Example action |
| --- | --- |
| Invoice submission | Log the invoice and route it to Finance |
| Payment query | Draft a payment-status reply |
| Billing dispute | Create a dispute case and assign Billing Support |
| Spam / promotion | Archive the message |
| Account update | Update the billing contact |
| Needs human review | Create a review task without sending a reply |

## Installation

1. Download or clone the project files.
2. Keep `index.html`, `app.js`, and `style.css` in the same folder.
3. Open `index.html` in a modern web browser.

## Environment Variables

None. This static demo has no API keys, server, or environment configuration.

## How to Use

1. Select an email to inspect the original message.
2. Click **Run agent** to process the queue.
3. Review each detected intent, confidence score, reasoning, and simulated action.
4. Inspect the audit trail at the bottom of the page.
5. Click **Reset demo** to return to the initial state.

## Sample Inputs

The included synthetic emails cover an invoice with an invoice ID, amount, and payment terms; an overdue purchase-order payment query; a disputed platform fee; a promotional message; an unclear account-amount question; and a billing-contact update request.

## Ambiguous Email Handling

Relay treats incomplete or unclear requests conservatively. The sample message about an unexpected account amount could be a payment query or billing dispute, but lacks enough detail to choose safely. It is labeled **Needs human review**, given a lower confidence score, and escalated without an automatic customer-facing reply.

## Audit Trail

Each processed email creates a visible audit record with its processing time, sender, detected intent, simulated action or escalation, and confidence score. This makes each decision reviewable within the demo.

## Assumptions

- All inbox data is synthetic and safe to display.
- Intent, confidence, reasoning, and actions are predefined for demonstration purposes.
- High-confidence messages can receive the simulated autonomous actions shown in the UI.
- Low-confidence or ambiguous messages require a human decision.

## Limitations

- This is a UI prototype, not a production email agent.
- It does not connect to an email provider, database, LLM, or business system.
- It does not parse attachments or learn from user feedback.
- Audit records exist only in browser memory and reset when the demo is reset or reloaded.

## Future Improvements

- Connect an inbox provider and secure business-system integrations
- Use an LLM or classifier to infer intent from new messages
- Add configurable confidence thresholds and approval workflows
- Persist audit records in a database
- Support attachments, thread context, and reply drafting
- Add authentication, role-based access, and monitoring
