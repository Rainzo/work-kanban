# Keboola optimisation + migration

Created: July 12, 2022 9:09 AM
Last edited: May 10, 2023 11:54 AM
Owner: Slava Gatin
Status: To-do
Software: keboola
Estimation: more than a week
Priority: highest

- Cutting the spend before negotiating the contract renewal:
    
    ![image (2).png](Keboola%20optimisation%20+%20migration%206d0fbb0a6c244451b75c4c20f00568b7/image_(2).png)
    
    1. Telemetry data - build extended report to understand where the most spend is occurring
    - [x]  Done
    
- Migration to New Queue + reorganisation of transformations and writers

## Optimising writers

### Big Query incremental

- **autocos_providers_channels** →
    - [x]  create PK + update it in the storage AND in the output mapping in transformation
    - [x]  set it in writer config
- **pricing_variants** →
    - [x]  rewrite it with modified autocos_providers_channels
    - [x]  Create PK + update it in the storage AND in the output mapping in transformation
    - [x]  update BQ writer with PK
- **premium and sport reports** →
    - [x]  no usage last 7 months → asked Lenka if i can disable datasets
    - [x]  created Monthly bucket + monthly BQ writer ⇒ added both to Monthly orchestration. Exitlog_aggregated queries are commented are outputs are deleted
- **paid vs free exits**, [this report](https://tableau.glami.info/#/workbooks/316/views) - unused →
    - [x]  asked PM team if i can disable the dataset
    - [x]  deleted writer + commented queries in exit_log_aggregated
- **auto_cos_kpi_providers** →
    - [x]  add PK (create in Transformation)
    - [x]  cut to less months (asked BEX) -cut to last 13 months!
    - [x]  update writer config
- **kpis_by_price_ranges** → deleted (no connected workbooks)

---

Run time decreased from 2h45m to 45m.

### TDE Main

- exit_log_autocos_channels (1 & main later update)→
    - [x]  create PK + set it in the output mapping settings + push through BQ
    - [x]  replace dataset in [tableau](https://tableau.glami.info/#/datasources/112735/connectedWorkbooks)
    - [x]  delete TDE writer
- [exitlog_gads](https://tableau.glami.info/#/datasources/115265/connectedWorkbooks) →
    - [x]  push through BQ and replace dataset
    - [x]  delete TDE
- [exits_by_brands](https://tableau.glami.info/#/views/Ordersbyitems/Exitsbybrands-history?:iid=5) → no usage, put into monthly run instead
    - [x]  push to monthly queries, comment the old ones, delete output
    - [x]  leave comment in the worksheet
- [exits_by_items](https://tableau.glami.info/#/views/GlamiItemLikes/Exitsbyitems?:iid=11) ([https://tableau.glami.info/#/datasources/115424/askData](https://tableau.glami.info/#/datasources/115424/askData))→ no usage, put into monthly run instead
    - [x]  push to monthly queries, comment the old ones, delete output
    - [x]  leave comment in the worksheet
- providers_tags_items → ambiguous data, explore
- [orders_tracking](https://tableau.glami.info/#/views/COSbytrackingtype/COSbytrackingtype_1?:iid=4) → cut the data or use monthly
    - [x]  Cut to last 13 months
- [visual_search_ga](https://connection.keboola.com/admin/projects/1828/transformations/bucket/902955588/transformation/908079728) → moved to monthly

---

Run time decreased from 6h to 4h.

## Optimising Transformations

### [Channels (AutoCOS filter)](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/673447800) (400 lines reduced)

- [x]  autocos_providers_channels - use first order_grouped as a basis
- [x]  pricing_variants - use autocos_providers_channels as basis
- [x]  providers_by_rev_autocos - delete (replace with autocos_providers_channels in TBL)
- [x]  source_coefficient - used autocos_providers_channels pre-aggregation instead of doing it from the scratch (-150 lines)
- [x]  all autocos related datasets are switched to use exit_log_meta_data instead of auto_cos_providers_snapshot

### [Exit log aggregated](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/625084641) (370 lines reduced)

- [x]  Sport & Premium reports transferred as a monthly transformation
- [x]  Paid_vs_free exits commented, report not used anymore
- [x]  exit_log_channel_device commented, report not used anymore

---

## Optimising Extractors

### GA

- [x]  get rid of all configs except TD (main) in main, bi-weekly and extra run
- [x]  get through main 2 and disable unused datasets or transfer them to monthly
- [x]  reduced marketing cost run from 3 days to 2

---

## Optimising Orchestrations

### Main

- [x]  got rid of inactive main_sql extractors in the morning run
- [x]  reshuffled jobs for clarity
- [x]  pushed monthly transformations to monthly bucket which is fully migrated to New Queue

### Monthly, Weekly and Telemetry

- [x]  All related transformations are moved to the New Queue

### Tableau Prep

- [x]  [**Core users**](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/712460867) moved to Monthly
- [x]  core users related writers are moved to monthly TDE
- [x]  Sklik_keywords moved to monthly, related writer moved to monthly TDE