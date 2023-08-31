# Add columns to “Providers with channels” report

Created: January 25, 2023 8:49 AM
Last edited: March 17, 2023 4:32 PM
Owner: Silvia Lešková
Status: Done
Engineer: Paweł Nowak
Priority: mid

[https://tableau.glami.info/#/views/ChannelsCategories/Providerswithchannelscategories?:iid=1](https://tableau.glami.info/#/views/ChannelsCategories/Providerswithchannelscategories?:iid=1)

Please add columns:

- **% of Total Revenue** - between Revenue and GMV
- **% of Total GMV** - between GMV and COS

Please add these 4columns at the end:

- **Exits YoY**
- **Revenue YoY**
- **GMV YoY**
- **COS YoY**
- all comparing the selected date period with same date period a year before (year-on-year comparison)
- all will be a percentage difference, for example if Exits are 150.000 this year and were 100.000 last year, the column Exits YoY will be “+50%”
- If value is higher than 0, then make it **green** please
- If value is lower than 0, then make it **red** please

### From Silvia:

- these metrics would be nice to see in the report:
- % of Total Revenue (between Revenue and GMV)
- % of Total GMV (between GMV and COS),
- exit YoY,
- Revenue YoY,
- GMV YoY
- COS YoY,
- AOV YoY
- % shop CR
- CPC-out YoY
- this will be showed as percentage difference (e.g. +50% yoy) if it will be more than 0 will be green if less than red
- comparison on **category** would be very useful, if it is a complication for the base report of providers, I think it could work also separately just also with filter for the channels and same KPIs metrics compared. Harry suggested maybe it could work similarly as basis of [this](https://tableau.glami.info/#/views/ChannelsCategories/Categorieswithchannelsandproviders?:iid=2) that has a longer LBW or same format as [this](https://tableau.glami.info/#/views/ProviderPerformanceReport/Periodcomparison-Top30graphs?:iid=1) with channel source filter.
- time stamp - it would be great if it is possible as adjustable periods (instead of fixed yoy) to compare MoM or WoW
- the best place for this report could be in CMs folder