# ADR-004: Build a modest reporting warehouse on our own second server, fed by a read replica

- **Status:** Accepted
- **Date:** 2026-11-11
- **Decision owner:** Kloud Kart Management

## Context

The data is about 40 GB, entirely structured, with known questions (revenue, stock, retention). The shop and its database share one box. A second server is pre-approved. The developer wants a cloud warehouse and Finance flinched. Nobody has run a warehouse, and there are two hires.

## Decision

A read replica of the shop's database on the second server, plus agreed reporting tables built from it each night in SQL. No lake, lakehouse or cloud warehouse this year.

## Alternatives considered

### Alternative A: A rented cloud warehouse now

- **How it would work:** A nightly load into a rented warehouse, with all reports reading from there.
- **Why it is attractive:** No server to patch, easy growth for Nigeria, the developer already wants it, and a two-person team doesn't maintain hardware.
- **Why rejected:** Cost grows with use and I have no verified price. It would put a second copy of customer data in a system we don't run, which a deletion must also reach. Its main strength, handling data too big for one server, solves a problem we don't have: at 15 to 20% growth, 40 GB takes roughly 9 to 12 years to reach 200 GB 

### Alternative B: An Operations-only mart first

- **How it would work:** A small set of tables for Nana's questions only, with Finance and Marketing added later.
- **Why it is attractive:** It is the smallest first step and the fastest route to Nana's Monday report.
- **Why rejected:** The root problem is that Operations and Finance compute revenue separately. A mart for one team leaves the other computing its own figure, so the disagreement survives.

## Consequences

- **What this buys:** Reports stop touching the shop, the only new money is tooling, and the two hires can own what they run.
- **What this costs:** One more server to patch and monitor, replication to watch, a second copy of customer data, and the maintenance sits with us.
- **What it costs the client if I am wrong:** If growth outruns one server (example; a Nigeria surge), the overnight job finishes late and Nana has no Monday report until we migrate.
- **What would make me revisit this:** The database nearing 200 GB, the overnight job not finishing by 06:00, Nigeria volume breaking the growth assumption, or the developer unable to set up the copy within about four weeks.

## What this survives

Orders doubling to about 80 GB, and Nigeria as a second country. It does not survive a need for data beyond one server, or machine learning at scale. A new record would then supersede this one.
