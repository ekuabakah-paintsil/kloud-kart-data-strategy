# ADR-005: Operations and Finance sign one definition of revenue before the analytics engineer starts

- **Status:** Accepted
- **Date:** 2026-11-11
- **Decision owner:** Kloud Kart Management

## Context

Nana's revenue and Finance's never match, because each applies its own rules. This is a consistency problem, not a pipeline problem, and cleaning data doesn't fix it. Nobody owns the definition. Agreeing one is cheap and unblocks everything downstream.

## Decision

By 31 January, Nana and Finance sign a one-page definition of revenue, assuming an order counts on the day it ships. The Monday report computes it in one place, and both teams read it.

## Alternatives considered

### Alternative A: Keep both definitions and publish a reconciliation

- **How it would work:** Both rules are computed nightly, and the difference is explained order by order.
- **Why it is attractive:** No negotiation, and each team keeps a rule that suits its purpose. It is quick and it makes the gap visible.
- **Why rejected:** Two figures still reach the board, and every meeting starts with which is right. A consistency problem is fixed by agreeing a definition and computing it once.

### Alternative B: Let the analytics engineer decide after starting

- **How it would work:** The hire writes the definition in Q2 as part of the job.
- **Why it is attractive:** A neutral person settles it, and defining metrics is that role's job.
- **Why rejected:** It is a business choice between Nana and Finance, not a technical one, and waiting costs a quarter of mismatched Mondays.

## Consequences

- **What this buys:** One figure at the board, a one-page definition anyone can read, and an unblocked first task for the analytics engineer.
- **What this costs:** One team's rule changes, Nana and Finance must settle it without a hire to mediate, and past figures may need restating.
- **What it costs the client if I am wrong:** If the signed rule doesn't suit Finance (they report on payment), Finance keeps its own spreadsheet and the board sees two numbers again, so Nana's credibility takes the hit and the Q2 outcome fails.
- **What would make me revisit this:** It isn't signed by 31 January, Finance needs a payment-date view, or returns and cancellations move a quarterly figure materially.

## What this survives

The second hire starting late, and the Nigeria pilot adding orders under the same rule. It does not survive the two teams refusing to sign, which would go to the board.
