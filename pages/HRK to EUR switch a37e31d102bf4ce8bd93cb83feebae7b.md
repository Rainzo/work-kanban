# HRK to EUR switch

Created: December 19, 2022 12:26 PM
Last edited: January 13, 2023 12:41 PM
Owner: Magdalena Vasev, Oskar Stierand
Status: Done
Timeline: December 19, 2022 12:00 AM (GMT-1) → January 2, 2023 12:00 AM (GMT-1)
Engineer: Slava Gatin, Michal Smrčina
Estimation: week
Priority: highest

# Description

- Under
    
    Slack channel:
    # ****temp-croatia-euro-adoption****
    
    List of tables affected: [Tasks](https://www.notion.so/969b3b8d35cf467484d9626a310fd4fe?pvs=21) 
    
    > HR is adopting Euro and all related transformations in Keboola will have to be adjusted to reflect that. On the day of the split, 2.1.2023, we will have to swap all queries where currency conversion is done so that values coming from klarka_hr are no longer converted to Euro and CZK conversion is done from Euro and not from HRK. Example, [exit log proc](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/216835093): (lines 123 - 182)
    > 
    
    ```sql
    CREATE TABLE "tmp.rate" AS
    SELECT
    e."exit_log_id",
    to_number(CASE WHEN e."db" = 'CZ' THEN e."cpc"
    WHEN e."db" IN ('SK', 'DE', 'FR', 'GR', 'SI', 'ES', 'ECO', 'LT', 'LV', 'EE', 'IT') THEN e."cpc" * (coalesce(r."rate", q."rate"))
    WHEN e."db" = 'RO' THEN (e."cpc" / (coalesce(f."rate", d."rate"))) * (coalesce(r."rate", q."rate"))
    WHEN e."db" = 'RU' THEN (e."cpc" / (coalesce(u."rate", b."rate"))) * (coalesce(r."rate", q."rate"))
    WHEN e."db" = 'TR' THEN (e."cpc" / (coalesce(y."rate", t."rate"))) * (coalesce(r."rate", q."rate"))
    WHEN e."db" = 'BG' THEN (e."cpc" / (coalesce(n."rate", m."rate"))) * (coalesce(r."rate", q."rate"))
    WHEN e."db" = 'HR' THEN (e."cpc" / (coalesce(p."rate", s."rate"))) * (coalesce(r."rate", q."rate"))
    WHEN e."db" = 'BR' THEN (e."cpc" / (coalesce(l."rate", k."rate"))) * (coalesce(r."rate", q."rate"))
    WHEN e."db" = 'HU' THEN (e."cpc" / (coalesce(h."rate", g."rate"))) * (coalesce(r."rate", q."rate")) END, 10, 3) as "cpc",
    to_number(CASE WHEN e."db" = 'CZ' THEN e."cpc" / (coalesce(r."rate", q."rate"))
    WHEN e."db" IN ('SK', 'DE', 'FR', 'GR', 'SI', 'ES', 'LT', 'LV', 'EE', 'IT') THEN e."cpc"
    WHEN e."db" = 'RO' THEN (e."cpc" / coalesce(f."rate", d."rate"))
    WHEN e."db" = 'RU' THEN (e."cpc" / coalesce(u."rate", b."rate"))
    WHEN e."db" = 'TR' THEN (e."cpc" / coalesce(y."rate", t."rate"))
    WHEN e."db" = 'BG' THEN (e."cpc" / coalesce(n."rate", m."rate"))
    WHEN e."db" = 'HR' THEN (e."cpc" / coalesce(p."rate", s."rate"))
    WHEN e."db" = 'BR' THEN (e."cpc" / coalesce(l."rate", k."rate"))
    WHEN e."db" = 'HU' THEN (e."cpc" / coalesce(h."rate", g."rate")) END, 10, 3) as "cpc_EUR",
    to_number(CASE WHEN e."db" = 'CZ' THEN e."default_cpc"
    WHEN e."db" IN ('SK', 'DE', 'FR', 'GR', 'SI', 'ES', 'ECO', 'LT', 'LV', 'EE', 'IT') THEN e."default_cpc" * (coalesce(r."rate", q."rate"))
    WHEN e."db" = 'RO' THEN (e."default_cpc" / (coalesce(f."rate", d."rate"))) * (coalesce(r."rate", q."rate"))
    WHEN e."db" = 'RU' THEN (e."default_cpc" / (coalesce(u."rate", b."rate"))) * (coalesce(r."rate", q."rate"))
    WHEN e."db" = 'TR' THEN (e."default_cpc" / (coalesce(y."rate", t."rate"))) * (coalesce(r."rate", q."rate"))
    WHEN e."db" = 'BG' THEN (e."default_cpc" / (coalesce(n."rate", m."rate"))) * (coalesce(r."rate", q."rate"))
    WHEN e."db" = 'HR' THEN (e."default_cpc" / (coalesce(p."rate", s."rate"))) * (coalesce(r."rate", q."rate"))
    WHEN e."db" = 'BR' THEN (e."default_cpc" / (coalesce(l."rate", k."rate"))) * (coalesce(r."rate", q."rate"))
    WHEN e."db" = 'HU' THEN (e."default_cpc" / (coalesce(h."rate", g."rate"))) * (coalesce(r."rate", q."rate")) END, 10, 3) as "default_cpc",
    to_number(CASE WHEN e."db" = 'CZ' THEN e."default_cpc" / (coalesce(r."rate", q."rate"))
    WHEN e."db" IN ('SK', 'DE', 'FR', 'GR', 'SI', 'ES', 'LT', 'LV', 'EE', 'IT') THEN e."default_cpc"
    WHEN e."db" = 'RO' THEN (e."default_cpc" / coalesce(f."rate", d."rate"))
    WHEN e."db" = 'RU' THEN (e."default_cpc" / coalesce(u."rate", b."rate"))
    WHEN e."db" = 'TR' THEN (e."default_cpc" / coalesce(y."rate", t."rate"))
    WHEN e."db" = 'BG' THEN (e."default_cpc" / coalesce(n."rate", m."rate"))
    WHEN e."db" = 'HR' THEN (e."default_cpc" / coalesce(p."rate", s."rate"))
    WHEN e."db" = 'BR' THEN (e."default_cpc" / coalesce(l."rate", k."rate"))
    WHEN e."db" = 'HU' THEN (e."default_cpc" / coalesce(h."rate", g."rate")) END, 10, 3) as "default_cpc_EUR",
    e."cpc" AS "cpc_loc_curr",
    e."default_cpc" AS "default_cpc_loc_curr"
    FROM "cln.exit_log_final" e
    LEFT JOIN "cln.rates" r ON r."date"= TO_DATE(TO_TIMESTAMP(e."timestamp")) and r."fromCurrency" = 'EUR' and r."toCurrency"='CZK'
    LEFT JOIN "cln.rates" f ON f."date"= TO_DATE(TO_TIMESTAMP(e."timestamp")) and f."fromCurrency" = 'EUR' and f."toCurrency"='RON'
    LEFT JOIN "cln.rates" h ON h."date"= TO_DATE(TO_TIMESTAMP(e."timestamp")) and h."fromCurrency" = 'EUR' and h."toCurrency"='HUF'
    LEFT JOIN "cln.rates" u ON u."date"= TO_DATE(TO_TIMESTAMP(e."timestamp")) and u."fromCurrency" = 'EUR' and u."toCurrency"='RUB'
    LEFT JOIN "cln.rates" y ON y."date"= TO_DATE(TO_TIMESTAMP(e."timestamp")) and y."fromCurrency" = 'EUR' and y."toCurrency"='TRY'
    LEFT JOIN "cln.rates" n ON n."date"= TO_DATE(TO_TIMESTAMP(e."timestamp")) and n."fromCurrency" = 'EUR' and n."toCurrency"='BGN'
    LEFT JOIN "cln.rates" p ON p."date"= TO_DATE(TO_TIMESTAMP(e."timestamp")) and p."fromCurrency" = 'EUR' and p."toCurrency"='HRK'
    LEFT JOIN "cln.rates" l ON l."date"= TO_DATE(TO_TIMESTAMP(e."timestamp")) and p."fromCurrency" = 'EUR' and l."toCurrency"='BRL'
    LEFT JOIN "cln.rates" q ON q."date"= (select MAX("date") from "rates") and q."fromCurrency" = 'EUR' and q."toCurrency"='CZK'
    LEFT JOIN "cln.rates" d ON d."date" = (select MAX("date") from "rates") and d."fromCurrency" = 'EUR' and d."toCurrency"='RON'
    LEFT JOIN "cln.rates" g ON g."date" = (select MAX("date") from "rates") and g."fromCurrency" = 'EUR' and g."toCurrency"='HUF'
    LEFT JOIN "cln.rates" b ON b."date"= (select MAX("date") from "rates") and b."fromCurrency" = 'EUR' and b."toCurrency"='RUB'
    LEFT JOIN "cln.rates" t ON t."date"= (select MAX("date") from "rates") and t."fromCurrency" = 'EUR' and t."toCurrency"='TRY'
    LEFT JOIN "cln.rates" m ON m."date"= (select MAX("date") from "rates") and m."fromCurrency" = 'EUR' and m."toCurrency"='BGN'
    LEFT JOIN "cln.rates" s ON s."date"= (select MAX("date") from "rates") and s."fromCurrency" = 'EUR' and s."toCurrency"='HRK'
    LEFT JOIN "cln.rates" k ON k."date"= (select MAX("date") from "rates") and s."fromCurrency" = 'EUR' and k."toCurrency"='BRL';
    ```
    
    ---
    
    Second part of the task will be to rewrite historical data as well by just loading all respectful tables where conversion is done and changing HRK to Euro, including GA tables (GA data will not be rewritten historically).
    

# Plan

change interval of extractors

I take 1-2, @Michal Smrčina you take 3+4+New queue (1)

> For GA data: HRK conversion for data **before** 01.01.2022 `union all` EUR converions for data **after** 02.01.2022 (both dates incl) marked **GA
upd: fixed with rewriting of historical tables instead**
> 

List of keboola transformations to change: 

**Legacy transformations**

- main_proc
    - [**data_provider_process](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/216834978)**
        - **output table** **[**data_provider](https://connection.keboola.com/admin/projects/1828/storage/in.c-main-proc/data_provider) - will be fully in Euro** **✅
    - **[exit_log_process](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/216835093)**
        - **output table [exit-log](https://connection.keboola.com/admin/projects/1828/storage/in.c-main-proc/exit_log) is in Euro starting from 01.01.2022** ✅
    - **[exit_log_init](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/216831668)**
        - **input tables exit_log, exit_log_final, exit_log_final_w_date - 2022 fully rewritten**
    - [**items_process**](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/216835260)
        - **output table [item](https://connection.keboola.com/admin/projects/1828/storage/in.c-main-proc/item)  is in Euro starting from 01.01.2022** ✅
        - **output table [item-full](https://connection.keboola.com/admin/projects/1828/storage/in.c-main_proc/item_full) will be fully in Euro** ✅
    - **[orders_process](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/216835325)**
        - **output table [data_provider_order](https://connection.keboola.com/admin/projects/1828/storage/in.c-main/data_provider_order#data-sample) will be fully in Euro** **✅
    - **[ad_sense & ad_content](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/776137937)**
        - **output** **tables ad_sense and ad_content are in Euro starting from 01.01.2022** ✅
    - **[magazine](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/818891046)**
        - **input tables are in Euro starting from 01.01.2022** ✅
    - **[marketing_daily](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/518893977)**
        - **output table marketing_daily will be fully in Euro** *(same way as ad_sense)* ✅
    - **[marketing_performance](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/527330922)**
        - **output table fb_bulk_editing** **will be fully in Euro** *(same way as ad_sense)* ✅
    - **[pixel_order](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/866232202)**
        - **input table [data_provider_order_pixel](https://connection.keboola.com/admin/projects/1828/components/keboola.ex-db-mysql/527040982/query/8240) one time cancelling of where condition**
        - **output table [main_proc.data_provider_order_pixel](https://connection.keboola.com/admin/projects/1828/storage/in.c-main_proc/data_provider_order_pixel) will be incrementally in Euro (incremental output enabled), extractors changed to 1 day -** changed back to full to get the new numbers → it will automatically rewrite the main_proc too January 7, 2023 ✅
    - **[auto cos & smart cos](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/601995887) - changed back to 250 days after exitlog fix January 7, 2023** ✅
    - /to
- main_proc_item_full
    1. [items_process](https://connection.keboola.com/admin/projects/1828/transformations/bucket/482217599/transformation/482218979)
        1. **[item](https://connection.keboola.com/admin/projects/1828/storage/in.c-main-proc/item)** (will be run mid month) clone loading with full item in the back  **✅
- orders second run
    - [data_provider_process](https://connection.keboola.com/admin/projects/1828/transformations/bucket/764334932/transformation/900787444)
        - **output table [data_provider_order](https://connection.keboola.com/admin/projects/1828/storage/in.c-main/data_provider_order#data-sample) will be fully in Euro** **✅
    - [exit_log_process](https://connection.keboola.com/admin/projects/1828/transformations/bucket/764334932/transformation/912821053)
        - **output table [exit-log](https://connection.keboola.com/admin/projects/1828/storage/in.c-main-proc/exit_log) will be in Euro starting from 01.01.2022** ✅
    - [order_process](https://connection.keboola.com/admin/projects/1828/transformations/bucket/764334932/transformation/764335026)
        - **output table [data_provider_order](https://connection.keboola.com/admin/projects/1828/storage/in.c-main/data_provider_order#data-sample) will be fully in Euro** **✅
    - [exit_log_ga_aggr_second_run](https://connection.keboola.com/admin/projects/1828/transformations/bucket/764334932/transformation/769876756)
        - **will be in Euro starting from 01.01.2022** ✅
- tbl_prep
    - [Exit log aggregated](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/625084641)
        - **output tables will be in Euro starting from 01.01.2022** ✅
    - [quiz_cohort](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/893141452) ****
        - **quiz_full will be in Euro after 01.01.2022** ✅
    - [email newsletter](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/2887876219)
    - **[CSS_COS Deviations](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/636910477) - cpc from merchant center - [changed extract to 373 days](https://connection.keboola.com/admin/projects/1828/components/keboola.ex-db-mysql/506357528/query/7321)**

**New queue Transformations**

1. Monthly
[norms](https://connection.keboola.com/admin/projects/1828/transformations-v2/keboola.snowflake-transformation/927229107)

# Converting historical data DB + GA

[Keboola Connection | Keboola Connection](https://connection.keboola.com/admin/projects/1828/transformations/bucket/563687965/transformation/938742368)

[Keboola Connection | Keboola Connection](https://connection.keboola.com/admin/projects/1828/transformations/bucket/563687965/transformation/937064550)

- **DB:**
    
    **exit_log**
    
    **exit_log_final**
    
    **exit_log_final_w_date**
    
    **item_price_history**
    
    **data_provider_order_log**
    
    [analytics_order](https://connection.keboola.com/admin/projects/1828/storage/in.c-main/analytics_order)
    
    items_price_history
    
- **GA:**
    
    *Glami GA - main #2*
    
    - **scout-sessions**
        - transactionRevenue, metric1
    - **email-newsletters**
        - transactionRevenue, metric1, metric2
    - **rex-segments**
        - transactionRevenue, metric1, metric2
    - **dimension_11_ad_sense**
        - transactionRevenue
    - **ad-content**
        - transactionRevenue, metric1, metric2
    - **~~checkout-providers-roi~~**
        - ~~transactionRevenue, metric1, metric2~~
    - **~~checkout-convorigin~~**
        - ~~transactionRevenue, metric1, metric2~~
    

## check: **AutoCOS & Smart COS guarantee**

- 
    - [ ]  *(check again, conversion related? , explore sources, compare LY if not sure)*
    - **AutoCOS providers highlight (need fix)**
        - COS selected date (also missing tracked revenue)
            - yes for Dec, no data for Jan
            - in Tableau even 2022 numbers seems not skewed, in Snowflake, they are skewed
        - ds: auto_cos.tde
            - full load
            - [transformation?](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/601995887)
                - tracked revenue: replace cpc_loc_curr by cpc_EUR from “exit_log”
                - gmv (total_price_loc_curr from “order” - no need to change?)
    - **AutoCOS regular check (need fix)**
        - DTTO
    - **AutoCOS target impact (exits) (need fix)**
        - Revenue (loc curr) - change for revenue_eur?
        - GMV (loc curr) - ok?
        - [transformation?](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/626788090)
            - row 386+
        - ds: auto_cos_kpis_providers (out_tableau).tde
        - target COS ok?
    - **AutoCOS target impact (revenue) (need fix)**
        - DTTO
        - change also Actual COS calc in Tableau
    - **Smart COS target groups (ok?)**
        - uses Revenue if Target COS (calculates on GMV (loc curr) - ok?)
        - data sources include also euro variations if necessary
    - **Smart COS target paid-registartion segments (ok?)**
        - no HR entry at default settings
        - shouldnt affect anything
    - **Smart COS overview (need fix)**
        - underlying sheet ***Revenue (EUR) SmartCOS***
            - HR: Nov revenue too high, Dec and Jan23 missing (yet takes revenue_eur)
            - ds: smart_cos_revenue.tde
                - [transformation](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/626788090)
                    - row 46+
                - missing all HR data since 2022-11-22
    - **Smart COS paid history**
    - **Auto COS KPI’s**
    - **AutoCOS COS vs. target**
    - **Providers (without categories)**
    - **AutoCOS target changes**
    - **Auto COS KPI’s flexible date**

## conversion - static rate (fundamental tables)

- 1/ **[data_provider](https://connection.keboola.com/admin/projects/1828/storage/in.c-main/data_provider#graph) (main)**
    - table, created from many geo-specific extracts
    - full load, no date, no change
    - 1/ follows up (not only ) with **main_proc/*[data_provider_init](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/216831533)*** transformation
        - possible to change cpc which is already in *data_provider* tab
    - 2/ follows up by dependent transformation **main_proc/*******************[data_provider_process](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/216834978)*** and eventually table [data_provider](https://connection.keboola.com/admin/projects/1828/table-preview/in.c-main-proc.data_provider?context=%2Fadmin%2Fprojects%2F1828%2Ftransformations%2Fbucket%2F216755000%2Ftransformation%2F216834978) (proc)
        - row 37+ and loc_curr at 72?
    - **data_provider_daily_snapshot**
        - includes timestamp, needs to change
        - dpds 2.0 should change eventually
        - T: [main_proc/data_provider_w_items_daily_snapshot](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/397071475)
            - *data_provider_process* precedes
                - there table *out.data_provider*  gets created which contains cpcs and is eventually used in this *daily_snap T*
- 2/ [**exit_log_aggr**](https://connection.keboola.com/admin/projects/1828/storage/in.c-main_proc/exit_log_aggr#graph)
    - creates revenue, gmv from cpc
    - preceding tranformation [tbl_prep/Exit log aggregated](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/625084641)
        - taking cpcs from [exit_log_proc](https://connection.keboola.com/admin/projects/1828/storage/in.c-main-proc/exit_log) table (main_proc/exit_log)
            - underlying transformation is main_proc/[exit_log_process](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/216835093),
                - rows 123+ and loc_curr at 163?
- **3/ [smart_cos_revenue](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/626788090)**
    - leads back to 2/ where it gets revenues etc.
    
    ## [tbl_prep](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689)
    
    ### Exit log aggregated
    
    - most of cpc metrics from ***in.exit_log_proc***
    - row 968 - not sure about i*n.ad_sense_data_stileo* source though (*revenue_loc_curr*)
    - row 1048+ creates *out.exitlog_ga_aggr* with conversions, but the path through temp tables etc. eventually leads again to *in.exit_log_proc*
    - row 1234 refers to ***in.forecast*** with forecasted cpcs
        - updates by [Glami - google sheets extract](https://connection.keboola.com/admin/projects/1828/components/keboola.ex-google-drive/323382188) - should be ok?
    - row 1538: *-taking only 14 months of exitlog_ga_aggr and taking care of nulls and empties*
    
    ### CSS_COS_deviations
    
    - uses ***in.merchant_center_cpc*** that has exit_cpc metric
        - comes from our db geos like [this](https://connection.keboola.com/admin/projects/1828/components/keboola.ex-db-mysql/601261090/query/66810)
    - also ***in.exit_log_proc***
    
    ### quiz_cohort
    
    - ***in.order*** (main-proc/order)
        - total prices lead to *main/data_provider_ordes*
            - gathered from geos extracts from db
    - ***in.exit_log_final*** (main-proc/exit_log_final)
        - should be ok with previous exit_log edits?
    
    ### quiz_promo
    
    - [**main-tbl/ga_all](https://connection.keboola.com/admin/projects/1828/storage/out.c-main-tbl/ga_all#graph)** and transactionRevenue
        - T: [marketing_daily](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/518893977) - looks ok?
    
    ### **Smart_COS_revenue**
    
    - above
    
    ### Channels (autoCOS filter)
    
    - cpcs from ***[in.exit_log_meta_data](https://connection.keboola.com/admin/projects/1828/storage/in.c-main_proc/exit_log_meta_data)***
        - based on previous exit_logs, edited and ok? (relates to exit_log_proc?)
    
    ### orders_tracking_types
    
    - in.analytics_order
        - revenue from geos from db
    - [in.autocos_providers_channels](https://connection.keboola.com/admin/projects/1828/storage/out.c-main-tbl/auto_cos_kpis_providers#schema)
        - T [Smart_COS_revenue](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/626788090) precedes so metrics should only follow and be ok
    - [in.order_item](https://connection.keboola.com/admin/projects/1828/storage/in.c-main-proc/order_item#graph)
        - graph too complex, not sure but should be ok (extracted total_price_loc_curr and EUR)
    - [analytics_order](https://connection.keboola.com/admin/projects/1828/storage/in.c-main/analytics_order)
    
    ### BD shops retention
    
    - not affected
    
    ### **cleaning_bq**
    
    - [in.autocos_providers_channels](https://connection.keboola.com/admin/projects/1828/storage/out.c-main-tbl/autocos_providers_channels#graph)
        - i.e. based on the Channels tranformation above
    - [in.exit_log_autocos_channels](https://connection.keboola.com/admin/projects/1828/storage/out.c-main-tbl/exit_log_autocos_channels#graph)
    - same as above
    - both of the tables include a lot of related metrics (also base_cpc, bidding..) yet are at the advanced stages, might be ok?
    
    ### Data provider daily snapshot 2.0
    
    - based on the previous daily snapshot,
    - T [Data provider daily snapshot 2.0](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/677462580)
    - full load ov, w/ snapshot day
    
    ### Data provider monthly sales snapshot
    
    - uses only relevant *in.data_provider_daily_snapshot*
    
    ### Email newsletters report
    
    - uses only in.exit_log_proc
    - e.g. the case with UNION ALL so leaving only the second, converted part there eventually
    
    ### Item counts
    
    - nothing
    
    ### BD reports
    
    - *in.exit_log_proc* and *in.exit_log_aggr* and *in.order*
        - all mentioned before
    - auto_cos_kpis_providers
        - again coming from Smart COS Revenue  T, ok?
    
    ### Glami item likes
    
    - not sure about *[in.revenue_guest_user_daily](https://connection.keboola.com/admin/projects/1828/storage/in.c-main_proc/revenue_guest_user_daily)* and [*in.orders_guest_user_daily](https://connection.keboola.com/admin/projects/1828/storage/in.c-main_proc/orders_guest_user_daily)* though
        - possibly ok, but didnt find them on graph and they use some revenues
    
    ### Inspigroup resources
    
    - uses *in.order* for totals, if ok then ok
    
    ### Pixel data quality
    
    - good
    
    ### User cohorts
    
    - uses in.exit_log, exit_log_proc transformation should take care of it
    - uses *in.order*
- GA
    - [x]  Done
        - [in.ga](http://in.ga/) - revert [sanity_check](https://connection.keboola.com/admin/projects/1828/transformations/bucket/679472618/transformation/679472637) once in.ga is changed