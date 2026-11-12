# Kloud Kart data strategy

A data strategy for Kloud Kart, an Accra e-commerce company: what to build first, who to hire, and why. Written for the DE01 lab (Foundations of Data Engineering and Data Science).

**Author:** Ekua Micah Abakah-Paintsil
**Status:** Work in progress

## The situation

Kloud Kart is three years old and ships about 4,000 orders a day, with a pilot in Nigeria. Orders, inventory and customer accounts all sit in one database on the same machine as the live shop, about 40GB in total. The Head of Operations rebuilds Monday's numbers by hand from exports, and Finance's figures never match hers. Marketing's customer list is copied with no record of the copies. Twice last month a Monday export slowed the shop to a crawl. The company has just raised funding, the board has budgeted two data hires, and a customer complaint about deleted data has a 90-day deadline.

The task is not to design the perfect system. It is to decide what a company this size should build first, and to defend that decision.

## What is in this repository

| File | What it is | Status |
|---|---|---|
| `Situation Diagnosis.md` | Five root causes, costed and ranked by business risk, with the questions I would have asked the client | Done |
| `Recommendation.md` | The architecture and processing position, who to hire, and what it costs to run (two pages) | Done |
| `roadmap.md` | A one-page, 12-month plan in four quarters, written as outcomes the client can check herself | Done |
| `decisions/` | Five decision records, each with a real rejected alternative | Done |
| `improvement.md` | One improvement beyond the brief, built | In progress |
| `deck/` | The board presentation | In progress |

## The recommendation in brief

- **Build a modest reporting warehouse** on the second server that is already approved, fed by a live copy of the shop's database. Reports run from the copy, so the Monday export no longer touches the shop. A lake, a lakehouse and a rented cloud warehouse were considered and set aside.
- **Daily refresh for everything, with stock as the one exception.** Stock stays in the live database and is read there. No streaming platform is needed anywhere.
- **Keep personal data out of the reports.** The reporting tables hold only an approved list of fields. Names, phone numbers, emails and addresses are left out.
- **Hire the data engineer first and the analytics engineer second.** The first stops what is costing money or carrying a deadline now. The second needs a safe place to work and a revenue definition that Operations and Finance have already agreed.

## The five root causes

1. There is no record of who copies customer data, or where the copies go.
2. A data export runs on the same machine as the live shop, so it slows the shop.
3. There is no agreed definition of revenue, so Operations' and Finance's numbers differ.
4. All data work depends on one developer with no data engineering support.
5. Stock information is not reliably kept current.

## The 12-month roadmap

| Quarter | Outcome the client can check herself |
|---|---|
| Q1 | The complaint is answered, one revenue definition is signed, and Monday's report opens with no export and no slowdown |
| Q2 | Operations and Finance quote the same revenue figure, and a test deletion is traced everywhere |
| Q3 | Each Monday brings a "checked" or "do not use" message, and the report shows Nigeria and oversold orders |
| Q4 | A forecasting trial ends in stop or go, and the board reviews three numbers |

## Decision records

| Record | Decision |
|---|---|
| ADR-001 | Refresh reporting daily, with live stock as the single exception |
| ADR-002 | Hire the data engineer first and the analytics engineer second |
| ADR-003 | Reporting tables list the fields they may hold and exclude names and contact details |
| ADR-004 | Build a modest reporting warehouse on our own second server, fed by a read replica |
| ADR-005 | Operations and Finance sign one definition of revenue before the analytics engineer starts |

## What this work could not verify

The brief gives no figures for order value, staff cost or how often overselling happens, so the costs in the diagnosis use stated assumptions. Also unverified: whether the shop reads stock live, whether stock counts are late or wrong, how deletions and backups work, whether Kloud Kart is registered with the Data Protection Commission, and current prices. Statements about Ghana's Data Protection Act, 2012 (Act 843) are my understanding and not legal advice.

## Notes

- Kloud Kart is a case study. No real customer data was used or is stored here.
- An assistant was used to polish the English and explain concepts for easy understanding
