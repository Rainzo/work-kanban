# Benchmarking GEOs

Created: September 27, 2022 9:23 AM
Last edited: April 3, 2023 9:13 AM
Owner: Ján Kešelák
Status: Done
Software: Tableau, keboola
Engineer: Slava Gatin, Paweł Nowak
Estimation: up to 8 hours
Priority: mid

**Why**
I currently lack a report or view (please let me know if you have some other reports that fulfil this) which would show me in one place, without any filtering on which key metrics geos differ against each other. This would be handy for example now, where we see that Stileo is not performing in the best possible way but we don’t really know where to start.
**What should the report include**
Key metrics in rows, geos in columns.
**Which metrics to include for starters:**

Super Key KPIs:

- Sessions
- Revenues
- Gross Profit
- COS %
- GMV / session

Marketing

- Arbitrage ROI
- CPC arbitrage
- CPC recurring
- Arbitrage COS
- Recurring COS
- % share of recurring on traffic
- % share of recurring on revenue
- % share of search on exits (google search, brand search, bing)
- % share of facebook on exits
- E-commerce conversion rate (or exit rate)
- % share of mobile sessions and exits

Business Development

- BM
- WCM
- Total number of paid shops (out of total number of active shops)
- Total number of paid products (out of total number of active products)
- Paid / Active shop ratio
- Average autocos target

Pixel health check

- Pixel purchase event ID pairing %
- Pixel viewcontent event ID pairing %

Content

- Number of LPs with at least 10 views in last X days
- Total number of active filters with at least X products (not sure if this is doable, would be nice)

---

Many metrics available [here](https://tableau.glami.info/#/views/Countrybenchmarkcomparison/Countrybenchmarkcomparison?:iid=2), investigate the dataset.