# Add filter providers to AutoCOS KPIs flexible date

Created: February 17, 2022 4:00 PM
Last edited: March 11, 2022 10:23 AM
Owner: Tibor Kese
Status: Done
Engineer: Slava Gatin
Priority: high

[https://tableau.glami.info/#/views/AutoCOSSmartCOSguarantee/AutoCOSKPIsflexibledate](https://tableau.glami.info/#/views/AutoCOSSmartCOSguarantee/AutoCOSKPIsflexibledate)

- We would like to put one filter here "Providers"
- By default all providers would be selected
- But you could untick some providers in order to see the KPIs without some specific providers
- Reasoning: The typical use case is to see Average COS target without some few big shops, e.g. AboutYou, because their COS traget is infuencing the ovral nuber a lot, and we would like to see the COS target and the trend without them

Slack discussion:

TomTom:

hey Tibor, it takes a bit time as the dataset is aggregated on GEO and date only. But I think we also have similar dataset on provider level. I will check and let you know if I manage to adjust it by tomorrow or if it requires more time.

hey Tibor, what if we adjust the version with flexible days - we add all the metrics you have in the monthly version + provider filter. I mean all the metric except returned revenue and the metrics around this value cause this is only available on GEO level.

It seems that the flexible version only needs BM to be added otherwise it has everything (except returned revenue), no?

Tibor:

I think that sounds good