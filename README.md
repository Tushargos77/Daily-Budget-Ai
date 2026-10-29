# Daily-Budget-Ai
AI-powered personal finance tracker for India: a live daily spending budget, hybrid rules + LLM transaction categorizer, and a chat assistant over your own data. FastAPI, PostgreSQL, React.
# DailyBudget AI

> An AI-powered personal finance tracker for India that tells you what you can actually spend **today**, and where the rest of your money went.

**Status:** 🚧 In development (Week 0: planning and repo setup)

---

## The Problem

Most people know their monthly salary but have no idea where it disappears. Coffee, quick-commerce, food delivery and random UPI payments add up quietly, and a monthly statement is too late to change anything.

## The Idea

Instead of a monthly view, DailyBudget AI gives you a **daily spending budget** that updates as you spend:

```
daily budget = (income − fixed costs − savings goal − spent so far) ÷ days left in month
```

Overspend on Monday and Tuesday's budget shrinks automatically. Every night, you get a short summary of how the day went.

## Planned Features

- [ ] Auth (signup / login, per-user data isolation)
- [ ] Manual transaction entry
- [ ] Bank / UPI statement import (CSV)
- [ ] Daily budget engine
- [ ] Hybrid transaction categorizer (rules first, LLM fallback)
- [ ] Dashboard: category breakdown, recent transactions, detected subscriptions
- [ ] Chat over your own data ("How much did I spend on delivery apps in October?") using guarded text-to-SQL
- [ ] Nightly summary by email
- [ ] "Delete my data" option

## Tech Stack

| Layer | Technology |
|---|---|
| Backend | Python, FastAPI, SQLAlchemy, Pydantic |
| Database | PostgreSQL (Neon) |
| Frontend | React + Vite |
| AI | LLM API for categorization fallback and natural-language queries |
| Deployment | Render (backend), Vercel (frontend) |

## Architecture (planned)

```
React dashboard  →  FastAPI  →  PostgreSQL
                       │
                       ├── Budget engine
                       ├── Categorizer (rules → LLM fallback)
                       └── Text-to-SQL assistant (read-only, per-user, validated)
```

## Evaluation (to be filled in)

The categorizer will be tested on a hand-labelled set of transactions.

| Method | Accuracy |
|---|---|
| Rules only | TBD |
| Rules + LLM fallback | TBD |

## Privacy and Security

- Each user can only access their own transactions.
- Raw statements and transaction details are not written to logs.
- The text-to-SQL assistant runs read-only, restricted to the current user's rows, and every query is validated before execution.
- Users can delete all their data.

## Scope and Limitations

- **No live bank connection.** Connecting to bank accounts in India requires the Account Aggregator framework and regulatory approval, so this project uses statement upload and manual entry instead.
- No payments, no mobile app, single currency (INR).

## Getting Started

> Setup instructions will be added as the backend and frontend are built.

```bash
git clone https://github.com/Tushargos77/daily-budget-ai.git
cd daily-budget-ai
```

## Roadmap

| Week | Goal |
|---|---|
| 1 | Backend foundation: auth, schema, transactions API, budget engine |
| 2 | Statement import and hybrid categorizer, with accuracy evaluation |
| 3 | React dashboard and chat over your data |
| 4 | Nightly summary, deployment, privacy pass, documentation |

## Author

**Tushar Prasad Goswami**
B.Tech ECE, Asansol Engineering College
[GitHub](https://github.com/Tushargos77) · [LinkedIn](https://linkedin.com/in/tushar-prasad-goswami-164334278)
