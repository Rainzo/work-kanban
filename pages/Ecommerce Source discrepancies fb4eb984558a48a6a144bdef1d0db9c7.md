# Ecommerce Source discrepancies

Created: September 14, 2022 9:18 AM
Last edited: September 26, 2022 1:45 PM
Owner: Matej Višňovský
Status: Done
Engineer: Slava Gatin

Several updates:

1. Indeed tracking data is only updated from 8 till 12 am. My morning extractors only grasp data with two days delay. I will set up additional one just to have this data in Tableau after 12:00. (orders_secondary extractors + transformations added)
2. **Tracking source** is group of available trackings from `DataProviderEcommerceStatusOk` table. In keboola & tableau dataset it’s called ecommerce_source. The way it was aggregated was not maybe ok but it’s not correct anymore so i will change it. It should it display all available tracking types while it only shows random one. (data_provider_init/process changed)
3. **Tracking** is selected tracking from DataProvider.Ecommerce + pixelType in case of PX. In keboola & tableau dataset it’s a combination active_tracking and pixel_type columns.