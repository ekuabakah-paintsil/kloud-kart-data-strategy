# Improvement beyond the brief: Customer data register and deletion tracker

## The problem it solves

Kloud Kart currently has an open complaint with the Data Protection Commission about a deleted customer’s data. The brief says Marketing exports the customer list with no tracking of how many copies exist. The reports and Finance’s spreadsheets may hold customer details as well, but the brief does not say. As a result of this, I assume Kloud Kart cannot show the Commission that a deleted customer’s data is gone from every copy.

The brief treats the Data Protection Act and the 90 days as constraints, but it gives no way to meet them. It did not ask how Nana answers this complaint, or the next request like it. Until she can, every new deletion request is another possible complaint, and the compliance outcomes in the roadmap for Q1 and Q2 have no starting point.

## What I built

I built a spreadsheet, `Kloud_Kart_Customer_Data_Register.xlsx`, that Nana can open without any help. It is filled with invented data only. It has five tabs:

1. **Summary** 

This has eight questions with a number beside each, such as “Deletion requests overdue” and “Customer-list files past their delete-by date”. Six of the eight numbers turn green at zero and red above it, and the other two are for information only. Each has one line saying what to do. Nana only needs this tab on a Monday morning.

2. **Where data lives** 

This lists every place that could hold customer details: the shop database, the planned live copy, the Monday report, Finance’s spreadsheets, Marketing’s exports, the customer service log, backups, any marketing messaging tool, and the register itself. Each row names its owner, what it holds, how to delete a customer from it, and how long that takes. Owners confirm their row and re-check it every 90 days, and the sheet flags any that are overdue.

3. **Deletion requests**

 This has one row per request. The deadline and the days left work themselves out from the date received. There is a column for each place on tab 2, marked Done or Not held. The status moves from Open to Due soon, Overdue, “Cleared, confirm” and finally Closed, once Nana has confirmed that the customer no longer appears in her report.

4. **Exports log** 

Marketing adds a row each time a customer list leaves the shop as a file. The sheet sets a delete-by date and flags files kept too long.

5. **How to use** 

This explains each tab in plain words, plus the four settings: the days allowed per request, the warning period, how long Marketing may keep an export, and how often places are re-checked.

The open complaint is already entered as the first request, with a placeholder for the customer number and the date the 90 days started. The sheet holds customer numbers only, never names or phone numbers. A customer number still points to one person, hence the register is listed on tab 2 as a place to clear. The “How to use” tab tells Nana to remove the customer number once a request is closed, so the request keeps its own number and dates and she can still show a dated record.

## What it is worth to Nana

Nana can answer the Commission on time. She can hand over a written list of every place the customer’s data was held and when each was cleared, instead of a guess.

It also cuts the slowest part of the complaint. My diagnosis estimates 40 to 120 hours of senior time to answer it, and I assume that hunting for where the data sits is the slowest part of that. If the register removes about half of that time (my assumption), that is 20 to 60 hours saved on this request, and each later request starts from a list.

Nana can also see the next request through herself. One tab tells her whether anything is overdue, without asking the developer. The Q1 list and the Q2 export log in the roadmap start from this sheet, so the Data Engineer spends their first weeks fixing gaps rather than hunting for them. If the Commission asks how Kloud Kart handles requests, she can show a dated record, which is a much stronger position than having no record at all.

## What it cost

It took about 2 hours to build, in a spreadsheet tool Kloud Kart already uses, so there is no new cost. To run, it adds about 15 minutes per deletion request to record each step, on top of the time each owner spends clearing their own place, which has to happen anyway. Each export takes Marketing about a minute to log, and each owner spends a few minutes every 90 days re-checking their row. These are my estimates.

The risk is that the register is only as good as Marketing’s logging. An export that never reaches the log is invisible. The Q2 outcome in the roadmap covers this by checking the log against the files on hand.

**Still to confirm**: 

Each owner must confirm their row on “Where data lives”, and until then the Summary shows them as not confirmed. The 90-day deadline in the sheet is the outer limit and matches the complaint, while the roadmap’s seven days is the target for the reports, and the time limit for routine requests needs confirming. The 30-day limit on keeping exports is an assumption, to be agreed with Marketing’s lead. Whether Marketing uses a separate email or SMS tool is also unconfirmed (row P8).

