# Exporting IT to Keboola

Created: July 8, 2022 3:39 PM
Last edited: July 25, 2022 10:15 AM
Owner: Slava Gatin
Status: Done
Software: keboola
Engineer: Slava Gatin
Estimation: up to 2 hours
Priority: highest

## DB:

ON: Mel by jsi je mit k dispozici. (ExitLog, ExitLogFinal, DataProviderOrder + agregace, `DataProviderExpectedCos` and `DataProviderBudget`)

| Relation | Table | Status | Comment |
| --- | --- | --- | --- |
| Category | Tag | OK |  |
|  | TagConnection | ? | Probably not needed |
|  | TagStructure | OK |  |
| Data Provider | Merchant | OK |  |
|  | Merchant2DataProvider | OK |  |
|  | DataProviderEcommerceStatusOk | OK |  |
|  | DataProvider | OK |  |
|  | DataProviderTrackingVatSettings | OK |  |
|  | ExtImportCheckList | OK |  |
|  | DataProviderAutoCosSettings | OK |  |
|  | Item | OK |  |
| Order | DataProviderOrder | OK |  |
| ExitLog | ExitLog | OK |  |
|  | ExitLogFinal | OK |  |
|  | ExitClickSource | OK |  |
|  | Tag | OK |  |
|  | TrackFlag | OK |  |
|  | ContentIdentifier | ? | probably only CZ |
|  | ExitClickCampaign | OK |  |
|  | AdwordsGclid | OK |  |
|  | AdwordsGclidAdGroup | OK |  |
|  | AdwordsGclidCampaignName | OK |  |
|  | ExitLogGclid | OK now | no rows ⇒ started to populate as of @July 15, 2022  |
| Item | Item2Cpc | NO | no rows |
|  | Item2ItemGroup | NO | no rows |
|  | Item2ItemMatching | NO | not found |
|  | Item2SizeVariant |  | increment 5 days |
|  | ItemGroupTag | NO | not found |
|  | ItemHide2Guest | NO | no rows |
|  | ItemPriceHistory | OK |  |
|  | Items2Tag |  | increment 5 days, disabled |
|  | ItemLike | OK |  |

### GA:

Connect Stileo GA (main configs)

### FB:

@Arkadiusz Mokrzycki provided access to all pages, confirm availability

### Channel definitions:

@Jan Matějček, @Arkadiusz Mokrzycki