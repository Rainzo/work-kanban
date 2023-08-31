# KPIs by price level - update with filter for PM

Created: October 5, 2021 12:28 PM
Last edited: November 1, 2021 11:03 AM
Owner: Tibor Kese
Status: Done
Software: Tableau, keboola
Engineer: tomas.dedek@glami.cz, Slava Gatin
Estimation: week
Priority: high

- **We can build on this report:** [https://tableau.glami.info/#/views/KPIsbypricelevel/KPIsbypriceFINAL_2?:iid=1](https://tableau.glami.info/#/views/KPIsbypricelevel/KPIsbypriceFINAL_2?:iid=1)
    - Rows = price ranges
    - Columns = same as in table
    - All current filters stay
- **Rationale:**
    - This report will serve for recalculation of optimal values of price coeffs
    - Also, This report will serve for CMs to use regularly and potentially change price multiplicators based on it
- **Create new filter for price multiplicators - "PM in range"**
    - PM in range 1
        - Example CZ: 1
    - PM in range 2
        - Example CZ: 1,12
    - PM range 3
        - Example CZ: 1,3
    - PM in range 4
        - Example CZ: 1,45
    - PM in range 5
        - Example CZ: 1,6
    - It should we possible to change the PM. When we change value in filter for price multiplicator, then the CPC will change and therefore COS column in table will change. All other columns should be unaffected.
        - In other words, we are reclaculating CPC and costs and COS and Base COS, while other metrics stay unchanged.
    - Comment to ranges:
        - All countries except HU, TR and GR have the sam range in CZK, even though they have different currencies - the reason is if you apply the exchange rate, the ranges are almost the same, so it is ok to calculate with the same ranges in CZK
        - In HU and TR the ranges are not in CZK, but in local currencies. The reason is that the ranges in CZK are very different from the rest (probably because big exchange rate differences since the ranges were originally set few years back). But even though you show the ranges in local currencies, in the mechanics of the report they are in CZK anyway, you translate it with the current exchange rate, right?
        - In GR we have only 3 ranges because thats how it historically was set
- **Add new filter for AutoCOS**
    - We want to calculate coeffs only on non-AutoCOS data - so we need ability to unfilter AutoCOS shops
- **Add new filter "Paid/Free"**, where you could choose between:
    - All (default)
    - Paid only
    - Free only
- **Add filter for Tracked exits only:**
    - you can select either "All" (default) or "Tracked only"
- **Add column AOV** (in between column CR and column COS)
- **Add column Base COS** (in between column AOV and column COS)
- **Create a second table below the first table**
    - We want to have two exact same tables below each other
    - The first one will be called "Old price multiplicators"
        - It will show the data always with the old price mltiplicators
        - In other words, it will not react to the filters "PM in range"
    - The second one will be called "New price multiplicators"
        - It will show the data always with the price mltiplicators as chosen in the filters "PM in range"
    
- **Add a new tab afterwords with category level**
    - where you would copy the report, but show all the data per category - exactly the same logic as in this report (this was also just a copy of the first tab, but showing the data per category) - [https://tableau.glami.info/#/views/KPIsbypricelevel/KPIsbypriceandcategory?:iid=1](https://tableau.glami.info/#/views/KPIsbypricelevel/KPIsbypriceandcategory?:iid=1)

Current price ranges and price multiplicators are defined in country config, example from CZ:

![Untitled](KPIs%20by%20price%20level%20-%20update%20with%20filter%20for%20PM%20c1110c64a9444448a3d5075a89a923a6/Untitled.png)