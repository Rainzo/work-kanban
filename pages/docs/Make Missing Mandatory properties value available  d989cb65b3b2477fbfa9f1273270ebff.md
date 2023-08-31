# Make Missing Mandatory properties value available for blending to data_provider_daily_snapshot table

Created: August 22, 2022 3:32 PM
Last edited: September 13, 2022 10:30 AM
Owner: Matej Višňovský
Status: Done
Software: keboola
Engineer: Paweł Nowak
Priority: low

2 options:

1. Adjust data_provider_daily_snapshot table to include Missing Mandatory parameters column per provider_id
2. Create a new table that will only have provider_id and Missing Mandatory parameters, so it can be blended with data_provider_daily_snapshot table

Missing mandatory parameters value should hold values available [here](https://connection.keboola.com/admin/projects/1828/storage/in.c-main/ext_import_check_list#data-sample).

The idea is to have all values from the name column, which have status 3 and are any of: 

- brand
- breadcrumbs
- size
- deliveryDate
- title
- price
- mainPicture

### Notes:

Push to Tableau for blending

input is there already:

[https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/577333598](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/577333598)

- add output and then use TDE Main SQL (1) to push it to Tableau and give to @Matej Višňovský