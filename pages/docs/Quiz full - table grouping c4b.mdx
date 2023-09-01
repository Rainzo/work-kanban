# Quiz full - table grouping

Created: February 24, 2023 11:35 AM
Last edited: August 21, 2023 1:54 PM
Owner: Kate Usova
Status: Preview / Next up
Timeline: May 31, 2023
Engineer: Slava Gatin
Priority: low

Current quiz cohort analysis in [Quiz report](https://tableau.glami.info/#/views/QuizCohorts_16614200008300/StatsCohorts?:iid=1) is built and aggregated directly in Tableau based on quiz_full datasource where the level of detail is on the guest_id/user_id. Once the table gets too big, it could be aggregated to monthly in a similar way as [visitsall_cohorts](https://connection.keboola.com/admin/projects/1828/storage/out.c-tbl_prep/visitsall_cohorts) so that the final view is:

| GEO | Cohort | cohort_users  | month | users | exits | revenue | orders | gmv | likes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| HR / GR / CZ | the week/month of the quiz_finished  | number of users who finished the quiz in the specific cohort (of a month) | a month index when the exit is happening after the quiz (e.g. - 0: same month, 1: the next month after the quiz etc.) | number of users from a specific cohort with a record within the specific month after the quiz  | number of exits done by the users from the cohort in the given month  | total revenue done by the users from the cohort in the given month | total number of orders done by the users from the cohort in the given month |  | total number of likes done by the users from the cohort in the given month |
|  | date_trunc('month', "time_ created"::date ) as "cohort_month” |  | has to be joined from calendar generator table so that every geo & cohort has equal number of months (in the transformation it is already created under “tmp.months”; calculated as datediff(month, "time_created"::date, "timestamp"::date) as "month_exit, where time_created is from the quiz_done table and timestamp from exit_log table |  |  |  |  |  |  |

Exits and orders can be joined altogether to the month based on the timestamp of exit click, while likes table has to be firstly grouped separately based on the timestamp of like (in transformation it is done in the temp table called “tmp.user_likes”)

Note: there are other output tables created based on the unaggregated “quiz_full” therefore it might make sense to set it to tmp.table instead of completely deleting not to rewrite the code of the other output tables that are based on it