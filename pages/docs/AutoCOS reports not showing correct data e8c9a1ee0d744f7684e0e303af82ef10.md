# AutoCOS reports not showing correct data

Created: August 8, 2022 5:38 PM
Last edited: September 1, 2022 12:39 PM
Owner: Zuzana Drápalová, Tibor Kese
Status: Done
Engineer: Slava Gatin
Estimation: up to 4 hours
Priority: high

DataProviderAutoCosLog

[https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/747273867](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/747273867)

[](https://tableau.glami.info/#/views/Pricingbreakdown/Pricingbreakdowndashboardbycategories?:iid=1)

- auto_cos_providers_kpis based reports

## Solution:

- Fully fixed 22-08-22 auto_cos_history_snapshots using original table only as the most reliable source, see second fix:
    
    [Keboola Connection | Keboola Connection](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/747273867)
    

### Side fix:

- exit_log_meta_data discovered to contain duplicated exits. 22-08-22 fixed [here](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/673447800). Will affect Channels & Categories & Providers.