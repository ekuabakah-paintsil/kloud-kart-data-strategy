# ADR-002: Hire the data engineer first and the analytics engineer second

- **Status:** Accepted
- **Date:** 2026-11-11
- **Decision owner:** Kloud Kart Management

## Context

The board budgeted two data hires, not three. One PHP/MySQL developer carries everything, and nobody else has run a warehouse. The Monday extract slows the shop, and a 90-day complaint clock is running. Nana's most visible pain is that her numbers never match Finance's.

## Decision

The data engineer starts in Q1 and the analytics engineer in Q2. Nana and Finance sign the revenue definition in Q1, before the second hire.

## Alternatives considered

### Alternative A: Analytics engineer first

- **How it would work:** They start in Q1, write the definitions and build the Monday report in 90 days. The existing developer sets up the replica.
- **Why it is attractive:** It attacks the loudest symptom first. Agreeing a definition is cheap and unblocks everything, so Nana sees matching numbers a quarter sooner. The replica is a standard MySQL feature he may already know.
- **Why rejected:** We can't verify his replication experience. The ordering rule says stop the bleeding first, and the slowdown and the complaint are the data engineer's work. The analytics engineer would otherwise run reports on the shop's machine. The definition doesn't need the hire, since Nana and Finance can sign it in January.

## Consequences

- **What this buys:** The costly and deadline-bound risks are retired first, knowledge spreads beyond one developer, and the analytics engineer arrives to a safe place and a signed definition.
- **What this costs:** Nana waits about a quarter longer for a report built by a dedicated hire. In Q1 nobody owns the metrics layer, and Nana and Finance settle the definition themselves.
- **What it costs the client if I am wrong:** If the developer could have set up the copy alone, Nana loses a quarter of Monday rebuilds by hand and presents mismatched figures to the board in Q1.
- **What would make me revisit this:** The developer shows he can stand up the replica within about four weeks, the definition isn't signed by 31 January, or the data engineer can't start in Q1.

## What this survives

Either hire starting a month late, since the dates shift by the delay. It does not survive both hires being late, or the data engineer leaving in the first six months with no written notes.
