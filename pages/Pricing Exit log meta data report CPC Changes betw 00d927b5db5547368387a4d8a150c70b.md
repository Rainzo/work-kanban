# Pricing Exit log meta data report: CPC Changes between periods

Created: September 23, 2021 11:10 AM
Last edited: February 6, 2023 9:49 PM
Owner: Tibor Kese
Status: Wishlist
Software: Tableau, keboola
Engineer: tomas.dedek@glami.cz
Priority: mid

**Report name: CPC Changes between periods**

- **Rationale**
    - Generally, we want to be able to answer a question why eCPC went down DoD or WoW or MoM. Was it because of change in Default CPC? Or rather change in channel mix (WCM)? Or change in something else?
    - We want to see change in eCPC, and all factors that influence the eCPC calculation, between two periods in time
    - eCPC is calculated like this:
        - for CSS pricing separately
        - for AutoCOS pricing searately
        - for Core pricing: eCPC = default CPC * mobile multiplier * WCM * WPM * BM-for-provider-bidding
            - That's why we look at all these metrics in the columns - to see what out of these metrics had big effect on eCPC change. Other metrics that have effect on eCPC: % of Paid exits, % of mobile exits
- **Rows**
    - Categories (based on tag ids)
- **Columns**
    - Shown in this sheet: [https://docs.google.com/spreadsheets/d/18NWqj4rVoztvt8QJHDJ8K6Kw2szwNeDbZNid4DWkTyA/edit#gid=1143067816](https://docs.google.com/spreadsheets/d/18NWqj4rVoztvt8QJHDJ8K6Kw2szwNeDbZNid4DWkTyA/edit#gid=1143067816)
    - *For each metric below, there should be three columns*
        - *first column is the value of the metric for Period 1*
        - *second column is the value of the metric for Period 2*
        - *third column is the percentage change of the metric between Period 1 and Period 2*
            - if the change is positive, please mark it green, if negative, please mark it red
    - eCPC
    - AutoCOS CPC - add another column under this metric called "Share of AutoCOS exits (Period 2)"
    - CSS CPC - add another column under this metric called "Share of CSS exits (Period 2)"
    - Default CPC - add another column under this metric called "Share of Core exits (Period 2)" - calculated average weighted by exits
    - WCM - weighted source coeff - calculated field with average of source coeff weighted by exits
    - WPM - weighted price multiplier - calculated field with average of price multiplier weighted by exits
    - Base CPC
        - defined as calculated field: Base CPC = Default CPC * source coeff * price multiplier
    - BM-for-provider-bidding - we want to show Bidding multiplier, but only for non-AutoCOS shops. That is Bidding Multiplier, which shows purely bidding by provider(through administration or feed), not bidding by us through AutoCOS
    - Mobile multiplier
    - % of mobile exits
    - % of Paid exits
- **Filters**
    - GEO
    - Period 1 - choose time period from some date to some date
    - Period 2 - choose time period from some date to some date
    - Device
    - Source
    - Providers
    
    Zbývá dokončit:
    
     - **WCM se chová zvláštně** - vybral jsem jen Channel = Google Search. pak by ale měl být stejnej WCM pro všechny kategorie
    
     - Uměli bychom nějak přidat jestli je bidding přes feed nebo přes admin? Myslím tím to, že bys v metrice B?-for-provider-bidding m
    
     - **Sloupec BaseCPC - můžeme ho prosím přidat?** V zadání ho mám, je definován jako calculated field: Base CPC = Default CPC * source coeff * price multiplier
    
     - Kosmetika:
    
    - Timestamp - Asi bych neumožňoval zobrazovat data před 7.12., protože tam budou chybět některý metriky, třeba bidding percentage, a před 20.11. dokonce mnohem víc, tak aby to někoho nemátlo, ne?
    - Přejmenovat celej Workbook na "Pricing Detailed Data" (můžeme dát do Country Managers části), přejmenovat tento report na "CPC Changes between periods"
    - V názvu sloupců bych vždycky to "period A", "period B" a nebo "changes between period" dal do závorky, aby to bylo přehlednější. Tedy název například prvního sloupce nebude "eCPC period A", ale "eCPC (period A)"
    - Názvy sloupců ke je "changes between period" - můžeme to zkrátit tím, že místo slova "changes" použijeme řecký písmeno delta Δ ?
    - "Share of Default exits (period B)" přejmenovat na "Share of Core exits (period B)" - moje chyba, měl jsem chybu v zadání
    - U všech sloupců se změnama - if the change is positive, please mark it green, if negative, please mark it red
    - Vizualizační sloupce nad metrikama podobně jako v reportu Pricing breakdown
    - Pro některý sloupce kde jsou často malý rozdíly, nebo změna je třeba mezi 0 a 1%, tak bych přidal jedno desetinný místo, ať je třeba místo změny "0%" vidět "0.3%" - navrhuju to u těchto sloupců:
    - % of Paid exits (changes between periods)
    - % of Paid exits (period A)
    - % of Paid exits (period B)
    - BM-for-provider-bidding (changes between periods)