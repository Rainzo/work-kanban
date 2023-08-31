# Create Provider Performance Report

Created: November 28, 2022 11:06 AM
Last edited: January 13, 2023 12:42 PM
Owner: Magdalena Vasev
Status: Done
Software: Tableau
Engineer: Paweł Nowak
Priority: mid

### What do you want to see and why?

Analysis on provider performance that would be meaningful for both CMs and BDs. The report will help in provider analysis on a monthly basis, as well as checking the pacing and unusual behavior of the most important provider metrics.

### How it should look?

[https://docs.google.com/spreadsheets/d/1Z7NHcasLIRdQCFpHoOSoa3FFrLJ4AZJ2STSUcL8lRtk/edit#gid=1439090237](https://docs.google.com/spreadsheets/d/16xqYLRvBj9hxN82MSqrxPgPRTMgn5ImpRyFBkgt4xkM/edit#gid=1439090237) 

Whereas:

1. Rows should be prolonged to performance of all providers (no “Other” row)
2. It would be ideal if we can add result filtering based on provider being paid/free. However, this shouldn’t be based on a current status given that it can frequently change. Therefore, it would be perfect if the filters can be based on Provider Avg. CPC > 0 / CPC = 0 (See cell AB5 in the Sheet)
3. Ranking (Avg. CPC, CR) is based on a comparison of all values within the column. 1 is the highest rank (e.g. highest Avg. CPC in the column would have rank 1)
4. The report should contain flexible choice of Period 1 and Period 2 (calendar, as in [https://tableau.glami.info/#/views/Presentationdataandcomparison/Presentationdataandcomparison?:iid=1](https://tableau.glami.info/#/views/Presentationdataandcomparison/Presentationdataandcomparison?:iid=1)). Here however Period 1 should represent Final value, while Period 2 - Initial value. 
5. Each metric should contain one more column for the nominal results of Period 2 (as shown in **Exits**)
6. COS columns - If possible, let’s add Expected COS after the Period comparisons, as well as % difference between the Actuals and Expected

Graphs:

1. Exit share, Revenue share, GMV share - top 20 providers. The rest of the providers should be marked as “Other”
2. Exit share vs. Revenue share and GMV share vs. Revenue share - top 30 providers
3. COS graph - Actual COS + line representing Country Average + line representing Country COS target (from Forecast)

### How frequent you will use this?

More than once a month

### How much past data you will need?

Minimum 1 year, preferably 2 years