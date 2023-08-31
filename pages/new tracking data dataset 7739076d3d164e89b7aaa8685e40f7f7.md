# new tracking data dataset

Created: January 31, 2023 9:53 AM
Last edited: August 29, 2023 4:14 PM
Owner: Jan Lupac
Status: Done

Couple of new data inputs:

[Add new `sourceSecondary` column form DataProviderOrder to exit_log_aggr - not updates, obsolete!](new%20tracking%20data%20dataset%207739076d3d164e89b7aaa8685e40f7f7/Add%20new%20sourceSecondary%20column%20form%20DataProviderOr%20becab045356c48a1ab489355bf5323d8.md)

- new relationship between DataProviderOrderLog and DataProviderOrder
    
    ```sql
    from
    	DataProviderOrder dpo
    left join DataProviderOrderLog dpol on
    	dpo.originOrderLogId = dpol.dataProviderOrderLogId
    ```
    

New dataset:

| Output: | Input (source): |
| --- | --- |
| dateTransaction | DataProviderOrder |
| dateExit | DataProviderOrder |
| DataProvider name | DataProviderOrder |
| DataProvider ID | DataProviderOrder |
| Country | DataProviderOrder |
| totalPrice | DataProviderOrder |
| totalPriceEUR |  |
| totalriceExcludingVat | DataProviderOrder |
| totalPriceExcludingVatEUR |  |
| type | DataProviderOrder |
| sourceSecondary | DataProviderOrder |
| detectionType | DataProviderOrderLog |
| Currency | DataProviderOrderLog |

Once it’s done, we can delete [https://connection.keboola.com/admin/projects/1828/storage/out.c-main-tbl/detection_type](https://connection.keboola.com/admin/projects/1828/storage/out.c-main-tbl/detection_type).