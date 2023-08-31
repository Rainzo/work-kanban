# Additions to KAD

Created: March 7, 2022 6:24 AM
Last edited: October 10, 2022 7:58 PM
Owner: Ján Kešelák
Status: Abandoned
Software: Tableau
Engineer: Paweł Nowak
Priority: low

Hi guys, I have the following requests to be adjusted in the recent KAM dashboard (after second meeting in which it is being used):

- can we please add **autocos target** to “Metric” dropdown in the graph chart at the bottom?
- can we add provider filter that would control the three tables on the top?
- not sure about this one - would it be somehow feasible to add information (either to table or graphs) about the ranking of given shops in terms of spending / exits in a given geo in a selected timeframe?

[https://tableau.glami.info/#/views/Revenueperbrandandprovider/KeyAccountDashboard?:iid=2](https://tableau.glami.info/#/views/Revenueperbrandandprovider/KeyAccountDashboard?:iid=2)

→

Hey guys, sorry for the delay, i was unable to download the workbook due to the Tbl server issues.

1. AutoCOS target is not in this dataset. There is a suitable data but it’s limited by the last 3 months only. I can add another similar graph to the bottom that would just show avg or last day autocos target as a single metric and will have country/provider/timestamp filters with 3 months of data available. Alternatively, i can think of a way of adding autocos target to the current dataset, but it might get tricky and will take longer time.
2. Sure!
3. Sounds good, just need to define the ranking more concretely, it can be exits or spend or both, with a switch.

→

1. Graph will do for now
2. Ok, lets do it
3. Spend is fine