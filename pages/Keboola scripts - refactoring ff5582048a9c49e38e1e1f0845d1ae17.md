# Keboola scripts - refactoring

Created: August 10, 2021 11:18 AM
Last edited: September 23, 2021 10:37 AM
Owner: tomas.dedek@glami.cz, Slava Gatin
Status: Done
Timeline: September 15, 2021
Software: keboola
Estimation: up to 8 hours
Priority: mid

- Slava:
    
    [https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/614572425](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/614572425) can we use exit log increment on input mapping? - yes, will do
    
    [https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/673447800](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/673447800) dynamic time period in tmp.exit_log_autocos + reduce the queries for checkout using existing tmp tables + out.providers_by_rev_autocos - what is it about?
    

out.providers_by_rev_autocos - what is it about? It's this one:

[AutoCOS filter in the bidding report](AutoCOS%20filter%20in%20the%20bidding%20report%20ca48faa002d947a6a97c509291eda884.md) - decreased timestamp to 14 months dynamically

[https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/480664297](https://connection.keboola.com/admin/projects/1828/transformations/bucket/216755000/transformation/480664297) to be reviewed - reviewed and optimised