# Paid/Unpaid for Pricing reports

Created: April 12, 2023 4:00 PM
Last edited: April 24, 2023 9:12 AM
Owner: Zuzana Drápalová
Status: Done
Timeline: April 17, 2023 → April 21, 2023
Software: Tableau, keboola
Engineer: Michal Smrčina
Estimation: up to 8 hours
Priority: high

1. ELMD - too many NULL (empty) paid_exits → check the creation of it [here](https://connection.keboola.com/admin/projects/1828/transformations-v2/keboola.snowflake-transformation/954077216). (inserted)
    1. MS: checked, replicated process leading to ELMD proc – 
2. Paid/unpaid ⇒ based on `is_paid` column.
3. Aggregate on paid/unpaid or keep the same aggregation and add new GMV columns for free providers
4. providers_order_grouped