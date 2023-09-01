# Ewelina Sales report

Created: May 18, 2022 1:11 PM
Last edited: September 14, 2022 9:04 AM
Owner: Ewelina Milczarek
Status: Done
Timeline: May 18, 2022 → July 11, 2022
Software: Tableau, keboola
Engineer: Bartosz Do Trong
Priority: high

As we discussed I am sharing with you the report I currently use to understand current MTD performance of Stileo customers.

It's used everyday by me and sales, but also very often by Igor and board members.

Additionally it's already official that I will be leading all countries so this report for all countries will be crucial for me to understand what's happening with customers and build sales strategy.

[**STILEO sales report**](https://datastudio.google.com/reporting/1fhWNJhnEUfWHNJrKHXYl8vPrESCYcbCI/page/EWPv)

[Rules for bonus system](https://docs.google.com/document/d/1iqA2DuApKMoZ0EcJZbAVSo7G4YcHFFC7RYGkP3oPrw8/edit)

1st tab - MTD status

2nd tab - Guideline what to negotiate - budget or COS

3rd tab - crucial for bonus system. [HERE](https://docs.google.com/document/d/1iqA2DuApKMoZ0EcJZbAVSo7G4YcHFFC7RYGkP3oPrw8/edit?usp=sharing) you can find all the rules.

4rd tab - crucial for bonus system

---

### Notes:

- Primary datasource to be updated: [https://connection.keboola.com/admin/projects/1828/storage/in.c-main_proc/data_provider_daily_snapshot_2_0](https://connection.keboola.com/admin/projects/1828/storage/in.c-main_proc/data_provider_daily_snapshot_2_0)

 - Transformation: 

[Keboola Connection | Keboola Connection](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/677462580)

- Account manager information is stored as mentor_id - to join with [**GlamiUser**](https://connection.keboola.com/admin/projects/1828/storage/in.c-main/glami_user#overview)
- Expected COS is stored [**here](https://connection.keboola.com/admin/projects/1828/storage/in.c-main/data-provider-expected-cos)** (currently empty)
- Provider budget is stored [**here**](https://connection.keboola.com/admin/projects/1828/storage/in.c-main/data_provider_budget) (currently empty, need to set up extractors for all other geos except BG)

After transformation is ready, update the [**writer**](https://connection.keboola.com/admin/projects/1828/components/tde-exporter/677837698/table/out.c-main-tbl.data_provider_daily_snapshot_2_0) with the new columns - select appropriate data types.

Report to be build in the CM folder in the following workbook (**Channels & Categories & Providers)**:

[](https://tableau.glami.info/#/workbooks/312/views)

@Bartosz Do Trong :

Hey Slava, actually I could use some time to focus on the reports; so basically I'd kindly ask you just to help with couple things:

- as monthly budget is already imported, I'd like to combine it with prepaid saldo (CreditAllowance table) to display available funds in joint way
    - do you recommand to add a date next to monthly budget and store the history of it? as currently there's just latest value stored
    - do you recommand to combine prepaid saldo with monthly limit at the extractor level, on the transformation or already in the report?
- in order for report to work, there's a need to import some tiny chunk of custom data (per month per account manager monthly goal - so it's usually like 5 numbers a month). I'd suggest to store it in a google spreadsheet and import it from there - what do you think about such idea?

@Slava Gatin:

1. sorry for not following up on monthly budget snapshot creation - but i’ve just put together [this other query](https://connection.keboola.com/admin/projects/1828/components/keboola.ex-db-mysql/876255797/query/97857) in IT mysql config by simply adding current_date to the query and checking incremental load with pk = concat( date + provider_id). Do you think it will be enough for this kind of table?
2. As for the CreditAllowance - i could not even find available for Keboola and im still waiting for devs to give me sufficient access for mysql workbench explorations. Maybe we should ask devs to make it available for Keboola? Then it will become clear on which level to join it and where. Depending on dimensions we can either join it there or in transformation. Please remind me - do you work with data_provider_snapshot as a primary datasource? Do you think other reports / geos will benefit from having budget and saldo columns in the data_prov_snapshot in the future? Then we can join them separately in the [bigger transformation](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/677462580). I also think it’s a good approach because snapshot budget will be growing more and more and eventually might become slow to load through writer while adding budget to data_prov_snapshot will not increase it in number of rows so time wise it should remain roughly same.
3. Tiny chunk of custom data - idea with google sheet is good enough. We can import it directly to Tableau and blend it there