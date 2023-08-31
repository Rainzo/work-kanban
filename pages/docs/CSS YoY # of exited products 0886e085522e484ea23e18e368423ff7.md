# CSS YoY # of exited products

Created: January 18, 2023 11:44 AM
Last edited: January 30, 2023 9:11 AM
Owner: Tomasz Różański
Status: Done
Engineer: Slava Gatin
Estimation: up to 4 hours
Priority: mid

![Untitled](CSS%20YoY%20#%20of%20exited%20products%200886e085522e484ea23e18e368423ff7/Untitled.png)

# also providers' count

```sql
select
"db",
date_trunc('month',"timestamp"::date) as "month",
count (distinct "exit_log_id")
from "in.exit_log_proc"
where "db" in ('CZ', 'SK', 'RO', 'HU') and ("timestamp"::date between '2022-01-01' and '2022-01-12' or
                                            "timestamp"::date between '2023-01-01' and '2023-01-12')
                                            and "source_name" = 'glami_css'
group by 1,2;
```