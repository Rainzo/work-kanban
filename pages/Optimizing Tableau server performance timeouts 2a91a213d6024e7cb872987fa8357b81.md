# Optimizing Tableau server performance/timeouts

Created: August 8, 2023 11:20 AM
Last edited: August 8, 2023 11:25 AM
Owner: Michal Smrčina
Status: Doing
Engineer: Michal Smrčina

Based on an issue reported by @Igor Smolny we observe a need to optimize Tableau Server to avoid errors when loading complex reports. The report in question is currently this [one](https://tableau.glami.info/#/views/BDshopretention_16194287488750/RetentionperGEO?:iid=1).

*An unexpected error occurred. If you continue to receive this error please contact your Tableau Server Administrator.*

[https://kb.tableau.com/articles/issue/error-an-error-occurred-communicating-with-the-server-504-viewing-dashboards-when-using-proxy](https://kb.tableau.com/articles/issue/error-an-error-occurred-communicating-with-the-server-504-viewing-dashboards-when-using-proxy)

[https://community.tableau.com/s/question/0D54T00000FWDZOSA5/how-to-increase-the-server-timeout-](https://community.tableau.com/s/question/0D54T00000FWDZOSA5/how-to-increase-the-server-timeout-)