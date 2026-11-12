# ADR-001: Refresh reporting daily, with live stock as the single exception

- **Status:** Accepted
- **Date:** 2026-11-11
- **Decision owner:** Kloud Kart Management

## Context

Investors asked for "real-time analytics" after a board member saw a dashboard at another company. That came from a pitch meeting, not a requirements process. The brief says stock counts cannot go stale, because that is how Kloud Kart oversells, and everything else can refresh daily. Nana compares one week with another. The team is two hires who also have to keep a shop up.

## Decision

Everything Nana, Finance and Marketing read refreshes overnight. Stock stays in the live database, where the shop and Nana's reorder view read it directly. We build no streaming platform and no second copy of stock.

## Alternatives considered

### Alternative A: Stream stock changes to the reporting side

- **How it would work:** Every stock change becomes an event, and a consumer updates a reporting figure within seconds.
- **Why it is attractive:** It gives seconds-level freshness, it extends to a second stock location in Nigeria, and a managed service means nobody patches brokers. It also answers the investors in their own words.
- **Why rejected:** The requirement is "not stale", and reading the live table meets it. A stream adds a producer, a broker, a consumer and partitions, plus failure modes batch doesn't have: a duplicated event takes stock down twice. It also adds an on-call burden for two people, and nobody here has run one.

### Alternative B: Copy stock into the reporting layer every few minutes

- **How it would work:** A small scheduled job refreshes a stock table on the second server.
- **Why it is attractive:** Stock sits beside the other reports, reporting never touches the shop, and it needs no new platform.
- **Why rejected:** It creates two paths to one number. Reorder decisions need counts that are correct now, so any lag on the copy turns into oversold orders.

## Consequences

- **What this buys:** A plain answer for investors, no platform to run, and one stock number.
- **What this costs:** The live database serves two kinds of stock reader. The data engineer must cap how often and how much the reorder view reads. We do not deliver a "real-time dashboard".
- **What it costs the client if I am wrong:** If the live read is too heavy at peak, checkout slows in selling hours, which is the Monday problem again. If the stale count actually lives in the shop's own code, oversells and their refunds and support time continue and Nana explains them to the board.
- **What would make me revisit this:** Oversold orders per month don't fall within two quarters of the Q3 report; the stock lookup measurably slows checkout; Nigeria adds a second stock location; or someone shows a decision that loses money when an hour late.

## What this survives

Order volume doubling, and the Nigeria pilot reporting daily. It does not survive a genuine need for second-level stock across two countries. Change capture on the stock table would then be the first thing to cost, and a new record would supersede this one.
