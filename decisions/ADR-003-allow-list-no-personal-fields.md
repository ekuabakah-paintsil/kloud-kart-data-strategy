# ADR-003: Reporting tables list the fields they may hold and exclude names and contact details

- **Status:** Accepted
- **Date:** 2026-11-11
- **Decision owner:** Kloud Kart Management

## Context

Marketing's 300,000-person customer list is exported as files with no count of the copies. A Data Protection Commission complaint about a deleted customer's data has a 90-day clock. The reporting copy mirrors the whole shop database, so it holds everything. As I understand Act 843, every copy is a place a deletion must reach. Revenue, stock and retention don't need names or contact details.

## Decision

The overnight job builds the reporting tables only from an approved list of fields. Names, phone numbers, emails and addresses are not on it. A new column added to the shop stays out until Nana approves it. Marketing lists leave only through a logged export.

## Alternatives considered

### Alternative A: Let reports read the full copy directly

- **How it would work:** Nana and Finance query the copy's tables, with no separate reporting tables.
- **Why it is attractive:** Nothing to build, no list to keep up to date, every field available for later questions, and the raw data stays to rebuild from.
- **Why rejected:** Every reader sees personal data, so every spreadsheet built from it is a new uncontrolled copy. Two people computing revenue from raw tables recreates the disagreement. The deletion answer would depend on people's care.

### Alternative B: Scramble identifiers instead of excluding them

- **How it would work:** Names and emails become scrambled codes, so rows still link to the same person.
- **Why it is attractive:** Marketing can still segment and count repeat buyers, and it is a common practice.
- **Why rejected:** A code that still points to one person is still personal data, so it must still be found and deleted, and it protects less than leaving the field out. An internal customer number already supports repeat-purchase counts, and Marketing's contact needs go through the logged export.

## Consequences

- **What this buys:** Fewer places hold contact details, and a customer deleted in the shop is gone from reports by the next morning.
- **What this costs:** Reports can't answer questions that need names or contacts, someone must approve each new field, and the copy itself still holds raw personal data.
- **What it costs the client if I am wrong:** If a field leaks through a free-text note holding a phone number or a deleted customer survives in backups or file copies, Kloud Kart can't answer the complaint inside 90 days. Nana then faces a regulator and a board during a funding round, with management time, legal advice and reputation at stake. I can't price that precisely.
- **What would make me revisit this:** A legitimate need for identified data in reports, a leak found in the monthly field check, new fields arriving faster than approval can keep up, or a legal check changing what I assumed about the Act.

## What this survives

The Nigeria pilot adding customers, because the same rule applies. It does not cover backups, whose retention I haven't verified.
