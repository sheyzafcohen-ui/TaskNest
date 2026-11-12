# TaskNest – Automated Support Ticket Router

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sheyzafcohen-ui/TaskNest/blob/main/TaskNest.ipynb)

TaskNest is a deterministic customer support ticket router built with Python regular expressions and pandas. It runs locally or in Google Colab without LLMs, external APIs, API keys, or extra installation commands.

## Routing rules

| Category | Example matched keywords | Team | Customer reply |
| --- | --- | --- | --- |
| Billing | payment, invoice, refund, subscription, charge | Billing | Thank you for reaching out. Your inquiry has been routed to our Billing team, and a specialist will review your account shortly. |
| Technical | technical, issue, crash, error, login, password | Tech | Thank you for contacting us. We have forwarded your issue to our Tech team, and an engineer will assist you soon. |
| General | feature requests, general questions, thank-you messages, or no billing/technical matches | General | Thank you for your message. Your inquiry has been assigned to our General team, and we will get back to you shortly. |

The classifier counts configured keyword matches with case-insensitive word-boundary matching. The higher score wins; Technical wins non-zero ties. The notebook processes ten example tickets, displays the results and team totals, and exports `tasknest_routed_tickets.csv`.

## Output schema

| Column | Description |
| --- | --- |
| `ticket` | Original customer inquiry |
| `category` | `billing`, `technical`, or `general` |
| `team` | `Billing`, `Tech`, or `General` |
| `reply` | Fixed response associated with the assigned team |
