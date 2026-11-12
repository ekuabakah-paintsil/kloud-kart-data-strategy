**SITUATION DIAGNOSIS**

The root causes costed and ranked by business risk in descending order are as follows:

1. **No record of who copies customer data, or where the copies go**
   
Because of this, there are multiple copies of untracked customer data containing sensitive customer information. Customer data leaves the database in exports that nobody logs, owns or sets an expiry date on, so Kloud Kart cannot say how many copies of a customer’s data exist or where they are held. This is very costly as it exposes Kloud Kart to possible penalties under the Data Protection Act, 2012 (Act 843). As of now, Kloud Kart has 90 days to respond to a Data Protection Commission complaint about a deleted customer’s data. Answering it will take an estimated 40 to 120 hours of senior time, which is GHS 4,800 to GHS 14,400 at GHS 120 an hour. That figure is only the minimum, because legal advice and any penalty come on top of it and I have not priced them. The larger cost is the damage to Nana’s credibility with the regulator and the board.

2. **Monday CSV exports slow down the live shop**
   
The export and the customers’ orders use the same machine, so they compete for it. As a result, there is a drop in sales during those slow hours, as customers struggle to place their orders and some who start the process do not return to complete it. This causes a direct loss of sales to Kloud Kart. Each slowdown loses about 25 orders (250 orders an hour × 0.5 hour × 20% who leave). At 24 slowdowns a year that is about 600 orders, or GHS 120,000 in sales at GHS 200 an order.

3. **No standardised revenue definition**
   
There is currently no agreed standardized definition on how to calculate “revenue”, and because of this, Nana’s Monday numbers are different from Finance’s numbers. The cost to Kloud Kart is wasted labour. Nana and Finance spend hours calculating revenue manually only to end up with different figures. Nana spends about 4 hours a week, Finance about 3, and the two spend another 2 together trying to explain the gap. Over 50 weeks that is 450 hours, or GHS 54,000 at GHS 120 an hour, about eleven working weeks a year.

4. **One developer with no data engineering support**
   
The only developer works in PHP and MySQL. Nobody on the team has run a warehouse or written Python professionally, so all data work falls on him on top of keeping the live shop running. As a result of this, every export and every data request waits for him, and each one competes with his work on the shop. Should this one developer leave, data work would stop until a replacement is found and has learned the system, and the upkeep of the live shop would be at risk as well. The cost to Kloud Kart is about three months of stalled data work, at his monthly cost, a month, plus any sales lost while fixes wait.

5. **Stock information is not reliably kept current**
   
When the count is out of date, goods that have sold out still show as available on the live shop, and the customer buys something Kloud Kart does not have. The brief says this is how the company oversells, but it does not say how often it happens. The cost to Kloud Kart is having to refund all affected customers, the support time spent on them, and the loss of sales as well. At 40 oversold orders a month and GHS 100 each, that is GHS 48,000 a year.

**Why I ranked them in this order**

The risks are ranked according to their potential impact on the business and the urgency with which management should address them.
1. **Customer data governance and compliance:** Potential regulatory and reputational consequences.

2. **Production database slowdown:** Direct impact on the live shopping experience and potential sales.

3. **Inconsistent revenue reporting:** Affects financial confidence and management decisions.

4. **Dependence on one developer:** Creates operational risk and delays if the developer is unavailable.

5. **Outdated stock information:** Can lead to overselling, refunds and customer dissatisfaction.
The ranking reflects business risk, not simply the estimated cedi value of each issue. Some figures represent potential exposure rather than confirmed losses.

**Assumptions**

The brief does not provide actual figures for every issue. The following assumptions were used to estimate possible costs:
  | Area | Assumption |
|---|---|
| Average orders | 250 orders per hour, based on 4,000 orders across 16 hours |
| Average order value | GHS 200 |
| Website slowdown | 30 minutes, with 20% of affected customers leaving |
| Slowdown frequency | Twice a month |
| Staff hourly cost | GHS 120 |
| Stock discrepancies | 40 affected orders monthly, valued at GHS 100 each |
| Developer replacement | Three months of disruption |

These estimates should be treated as indicative figures, not confirmed company losses.

**Questions I would have asked Nana**

1) Who is responsible for managing customer data, and what processes are currently in place for responding to data requests and regulatory complaints?

2) What happened during the last Monday export slowdown, and how frequently does it occur?

3) How do Nana and Finance currently define revenue, and which figures does management rely on?

4) Who handles customer data requests, and how long does it take to locate and remove a customer's information?

5) When was the last stock discrepancy recorded, and how frequently do customers order items that are unavailable?


