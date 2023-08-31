# Holistics’ Klarka Provider stats add GMV with VAT

Created: January 9, 2023 10:40 AM
Last edited: January 23, 2023 1:50 PM
Owner: Matej Višňovský
Status: Done
Software: Holistics, keboola
Engineer: Michal Smrčina
Priority: mid

Hi team,I have one request regarding Holistics. We prepared this report for Eobuv + Modivo, but the GMV data is from our Klarka Provider stats (without VAT), they would like to see GMV with VAT as they are used to see it in Dashboard. Could this be done?Thanks! It is not a pressing matter but we’d like to provide it for them within a reasonable timeframe.Report:

[https://eu.holistics.io/dashboards/v3/2199023271365?personal_id=2199023286988](https://eu.holistics.io/dashboards/v3/2199023271365?personal_id=2199023286988)

OR here [https://eu.holistics.io/dashboards/v3/2199023268858-modivo-eobuv-daily-costs-report](https://eu.holistics.io/dashboards/v3/2199023268858-modivo-eobuv-daily-costs-report)

## Notes

1. [order_process](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/216835325) → convert total_price (with VAT) to CZK and Euro
2. [exit log aggregated](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/625084641) → add these two new columns coming from main-proc.order
3. [exit_log_ga_aggr_second_run](https://connection.keboola.com/admin/projects/1828/transformations/bucket/764334932/transformation/769876756) → do the same here
4. make sure new columns are in writers:

![Untitled](Holistics%E2%80%99%20Klarka%20Provider%20stats%20add%20GMV%20with%20VAT%20cebb3824ccd64a248c959839c6aada49/Untitled.png)