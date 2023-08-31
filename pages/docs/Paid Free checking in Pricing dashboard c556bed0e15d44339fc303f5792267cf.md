# Paid/Free checking in Pricing dashboard

Created: August 15, 2023 11:02 AM
Last edited: August 29, 2023 4:01 PM
Owner: Silvia Lešková
Status: Done
Timeline: August 22, 2023
Engineer: Slava Gatin
Estimation: up to 4 hours

```sql
select "time_created"::date, count("exit_log_id") 
from "in.exit_log_meta_data_proc" where "inserted" = '' 
and "exit_log_id" in (select "exit_log_id" from "in.exit_log_meta_data_new" where "inserted" is not null and "inserted" != '')
group by 1;
```

This code gives empty (reg. joined from EL columns such as paid/free, inserted, tag, etc.) rows in main_proc.ELMD vs ELMD_new (generated using separate [transformation](https://connection.keboola.com/admin/projects/1828/transformations-v2/keboola.snowflake-transformation/1003780461) employing exit log proc)

Test the 45 days solution again in one week