# Pixel data quality

Created: May 11, 2021 3:09 PM
Last edited: June 22, 2021 9:35 AM
Status: Done

**Objective:** Help improve PX data quality by creating “Pixel Data Hygiene” monitoring report in Tableau**KRs:**

- KR1: Create a report in Tableau that **helps others increase order pairing** (which is a priority this Q)
- KR2: Create a report that help others to also: identify sudden drops in order, identify missing order values, identify no purchase events, and maybe more
- KR3: Teach everyone how to use this report, collect feedback, improve it, maybe create automatic alerts if it would be helpful for BDs

First thinking on what can be in the report (part of the OKR is to rethink this, change this, etc.):

- **tab “Pairing”**
- PX order pairing and ViewContent (product) pairing
- list of shops and next to the these two percentages, possibility to sort them (default setup is from lowest to highest, so on top are shop with order pairing 0%)
- **tab “Suspicious changes”**
- list of shops with two columns - “% change in orders”, “% change in purchase events”.
- It shows change in between two time periods, maybe by default week on week? But should be possible to change the time periods in filter
- You can also filter what change do you want to see - by default set maybe -70% - all of such shops are suspicious and maybe a change in Pixel happened there
- **tab “No order value”**
- **list of shops with two columns -** Orders and GMV.
- filter shops with more than 0 orders, but 0 GMV. That will show shops without order value
- **Tab “No orders”**
- list of shop with three columns - Exits, Orders, Purchase events.
- By default maybe filter shops with 100+ exitů and 0 orders.
- These are suspicious - maybe they have implemented only Pageview event and no purchase event
- Maybe more tabs and metrics based on ideas here - [https://www.notion.so/glami/Pixel-Monitoring-ideal-case-1cedd9b08d134c53acfc42f7b5bafb77](https://www.notion.so/Pixel-Monitoring-ideal-case-1cedd9b08d134c53acfc42f7b5bafb77?pvs=21)