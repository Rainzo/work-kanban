# Proper midmarket segment

Created: March 1, 2023 1:06 PM
Last edited: April 11, 2023 4:14 PM
Owner: Matej Višňovský
Status: Done
Engineer: Michal Smrčina
Priority: high

**Proper midmarket report:** 

- [Tiering report](https://tableau.glami.info/#/views/Providertiering/Providertieringreportlast30days?%3Aiid=1) can be duplicated and used for this task, all filters should remain the same, also the weight adjustment possibility - basically enriched by CR only (add parameter)
    - Exclude columns: Provider tier
    - add CR - if CR is 0.97% use 0.0097 (numeric value)
        - therefore the overall formula for ranking should be:
            
            [Exits parameter]*(SUM([exits]) / TOTAL(SUM([exits]))) +
            [Total items parameter]*[% of Total items] +
            
            [CR parameter]*[CR] +
            [Revenue parameter]*(SUM([revenue_loc_curr]) / TOTAL(SUM([revenue_loc_curr])))
            
- We want to see maximum of 50 providers per GEO ranked by the ranking sum.
- The weights are the same for all metrics(Exits, Total items, CR, Revenue) entering the calculation
- Providers that are on paid at least 70% of the given period (last 30 days as a default)
    - [https://tableau.glami.info/#/views/BDshopretention_16194287488750/Churnedshops](https://tableau.glami.info/#/views/BDshopretention_16194287488750/Churnedshops)
- Possibility to change the timeframe as a filter
- properties to be added:
    - Shop Type value (Klarka)
        - Show filter
    - Key Account (HubSpot)
        - Show filter
    - Competitive product portfolio of lower priced products flag
        - AOV > AVG AOV per GEO
            
            AND 
            
            CR > AVG CR per GEO
            
        - Value 1 if conditions are met, else 0
        - Show filter
    - X% can be defined per GEO, but let’s start with 4% as default value
        - X is used in the [condition](https://www.notion.so/BI-task-Proper-midmarket-670d551927db48c0bcc266fce9eba230?pvs=21) below
        - Show filter

## **Logic**

**Provider status = active**

**AND

Provider has been paid for at least 70% of the time of the given timeframe (start with last 30 days as default)**

- [https://tableau.glami.info/#/views/BDshopretention_16194287488750/Churnedshops](https://tableau.glami.info/#/views/BDshopretention_16194287488750/Churnedshops)

**AND**

`Shop Type`

- Not TOP

**AND**

`Is TOP X% based on ranking combination of (Number of exits, Active items, Revenues, CR)?`

- Yes

**AND**

Overall Rank < 51